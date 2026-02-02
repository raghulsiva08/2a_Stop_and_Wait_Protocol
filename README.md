# 2a_Stop_and_Wait_Protocol
## REF NO: 25015705
### DATE:02-02-2026
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
server.py
~~~
import socket

s = socket.socket()
s.bind(('localhost', 1234))
s.listen(1)

print("Server started, waiting for client...")
conn, addr = s.accept()
print("Connected with", addr)

while True:
    frame = conn.recv(1024).decode()
    if frame == "END":
        print("Transmission completed")
        break

    print("Frame received:", frame)
    conn.send("ACK".encode())

conn.close()
s.close()
~~~

client.py
~~~
import socket

c = socket.socket()
c.connect(('localhost', 1234))

frame_size = int(input("Enter number of frames: "))

for i in range(frame_size):
    frame = f"Frame {i+1}"
    print("Sending:", frame)
    c.send(frame.encode())

    ack = c.recv(1024).decode()
    print("Received:", ack)

c.send("END".encode())
c.close()
~~~

## OUTPUT
server.py
<img width="1298" height="1079" alt="Screenshot 2026-02-02 143226" src="https://github.com/user-attachments/assets/a3dd6c6d-34aa-49ce-b8d6-c318d5767065" />

client.py
<img width="1561" height="1025" alt="Screenshot 2026-02-02 143320" src="https://github.com/user-attachments/assets/6e3de010-5f34-4671-8772-e889eae5552e" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
