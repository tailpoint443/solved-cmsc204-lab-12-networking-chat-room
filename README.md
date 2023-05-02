Download Link: https://assignmentchef.com/product/solved-cmsc204-lab-12-networking-chat-room
<br>



<strong>Introduction</strong>

Everyone is familiar with chat rooms. In this lab we are going to create a server/client infrastructure that supports multiple users sending messages to each other.

In this lab you will not need to build the user interface, or to design the class structure.  You will be given most of the class structure and will focus on creating instances of classes that run inside threads, and on creating sockets and in- and out-streams with which to communicate.

First, we need a blueprint. Here is the basic class diagram:

<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2020/05/545.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2020/05/545.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>Let’s look more closely at each class.

<ol>

 <li><em><u>GUI</u></em>. The user interface is a set of classes providing the basic interface to start a server, start each client, and exit the application.  You will not need to edit this code.</li>

 <li><em><u>ChatServerExec</u></em>. The sole responsibility of the <em>ChatServerExec</em> is to implement the method <em>startServer</em>. This class implements the <em>ChatServerExecInterface</em>. You will be editing this class to put the server in a thread and start the thread. The ChatServer is placed in its own thread so the GUI can operate asynchronously.  The ChatServerExec then exits, while the ChatServer continues to operate.</li>

 <li><em><u>ChatServer</u></em>. The responsibility of this class is to create the server socket, listen for each client, and set up in- and out-streams. It then ensures that each client submits a unique screen name and adds the name to the set of client names. Finally, it creates a server to respond to the individual client and places it in a thread.  The <em>ChatServer</em> than continues its loop to listen for the next client.</li>

 <li><em><u>ServerThreadForClient</u></em>. This server responds to an individual client. When its client sends it a message, this server is responsible for sending out that message to each out-stream, i.e., to each client.  Note that this is an inner class.</li>

 <li><em><u>ChatClientExec</u></em>. Just like the <em>ChatServerExec</em>, this class is responsible for implementing <em>startClient</em>, which involves running the <em>ChatClient</em> instance in a thread. This class implements the <em>ChatClientExecInterface</em>.</li>

 <li><em><u>ChatClient</u></em>. This class is responsible for building its own window (code provided) as a separate GUI. You will create a client socket with server address and port and set up in- and out-streams to the server.  The class then follows the application protocol.  This involves first getting a screen name from the user, and then receiving messages from the clients via the <em>ServerThreadForClient </em>instances and posting the message in its textarea.  When this client sends a message, the user enters it into the window’s textfield whereupon it is sent to its<em> ChatClient </em>implements <em>ChatClientInterface<u>.</u></em></li>

 <li>Upload the initial files in GitHub in the repository you created in Lab 1, and modify them as you implement the solution. Take a screen shot of the repository and submit it.</li>

</ol>




<strong>Task #1 Starting a Thread</strong>

<ol>

 <li>In <em>ChatServerExec</em>, create a thread containing the server instance, and start the thread.</li>

 <li>In <em>ChatServer</em>, create a server socket. Also uncomment the System.out.println so that the console reflects that a server was started.</li>

 <li>When you run the GUI, you will be able to start the server, and launch clients, but will not be able to enter anything in the client’s textfield.</li>

</ol>

<strong>Task #2 Creating In- and Out-Streams</strong>

<ol>

 <li>Inside the <em>ChatServer</em> while loop, listen for a client to join, and when one does, create an in- and an out-stream.</li>

 <li>Compile and run, but you will still not be able to enter messages.</li>

</ol>

<strong>Task #3 Creating the Client</strong>

<ol>

 <li>In <em>ChatClientExec</em>, create a thread containing the client instance, and start the thread.</li>

 <li>In <em>ChatClient</em>’s run method, create a client socket with server address and server port.</li>

 <li>In <em>ChatClient</em>’s run method, set up in- and out-streams.</li>

</ol>

<strong>Task #4 Running the application</strong>

<ol>

 <li>Compile and run.</li>

 <li>Start the server first.</li>

 <li>Then start a client. Enter a screen name.</li>

 <li>Start a second client, with a unique screen name.</li>

 <li>Send messages by entering in a client’s textfield.</li>

 <li>Take a screen shot of two clients running and chatting.</li>

</ol>