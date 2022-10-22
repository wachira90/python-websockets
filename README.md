# python-websockets
python websockets


Here’s how a client sends and receives messages:

````
#!/usr/bin/env python

import asyncio
import websockets

async def hello():
    async with websockets.connect("ws://localhost:8765") as websocket:
        await websocket.send("Hello world!")
        await websocket.recv()

asyncio.run(hello())
````

And here’s an echo server:


````
#!/usr/bin/env python

import asyncio
import websockets

async def echo(websocket):
    async for message in websocket:
        await websocket.send(message)

async def main():
    async with websockets.serve(echo, "localhost", 8765):
        await asyncio.Future()  # run forever

asyncio.run(main())
````


Also, websockets provides an interactive client:

````
python -m websockets ws://localhost:8765/
Connected to ws://localhost:8765/.
> Hello world!
< Hello world!
Connection closed: 1000 (OK).
````

