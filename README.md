# Chatty Cathy

Chatty Cathy is a simple messaging app where users chat in real time, see who is online and also see when a user changes their name. Able to implement WebSocket and understand the idea of the 'Virtual DOM.' Code is consistent, clean and modular. Comments are written throughout code for readability.

## Stack
* Webpack
* Babel
* JSX
* ES6
* WebSockets
* Node
* ReactJS



## Code Sample

```javascript
//----Create the WebSockets server----\\
const wss = new SocketServer({server});
let nextSocketId = 0;

//----Broadcasting messages back to Client----\\
  wss.broadcast = function broadcast(data) {
    wss.clients.forEach((client) => {
      if (client.readyState === WebSocket.OPEN) {
        client.send(data);
      }
    });
  };

//----Establishing connection----\\
wss.on('connection', (ws) => {
  console.log('Client connected');

//----UsersOnline Info----\\
  const socketId = nextSocketId;
  nextSocketId += 1;
  let userLoggedIn = {
    type: "onlineUsers",
    value: nextSocketId
  }
  wss.broadcast(JSON.stringify(userLoggedIn));

```