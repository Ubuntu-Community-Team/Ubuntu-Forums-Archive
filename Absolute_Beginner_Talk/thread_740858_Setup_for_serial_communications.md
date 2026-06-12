---
title: "Setup for serial communications"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by aritrakundu on 2008-03-31
Hello,
i am trying to setup communications between two terminals using a standard rs232 cable . As PC's dont have a serial port I am using serial-USB adapter. My /dev setiings are now ttyUSB0 and ttyUSB1.

then to set up the baud rate i typed in the first terminal
stty 9600 cs8 -istrip -parenb < /dev/ttyUSB1  and
stty....................................../ttyUSB0

then in the second terminal i typed
cat < dev/ttyUSB0 to receive data.

Again inthe first terminal i typed 
echo "........" > /dev/ttyUSB1

But i am getting no output.
Please tell me how to configure the terminals so that when i type something in ne terminal i can get the output in the second.

Thank You[B][B]

---

### Post by nsche on 2008-04-01
Are you using a null modem cable?  You need one and can make one by having the wires from pin 2 and 3 swapped in the connecting line so that the transmit on one end talks to the recieve on the other and vice versa.

---

