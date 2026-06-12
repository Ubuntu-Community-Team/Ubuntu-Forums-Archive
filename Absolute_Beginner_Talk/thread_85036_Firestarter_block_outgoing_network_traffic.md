---
title: "Firestarter block outgoing network traffic"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by Iesos on 2005-11-01
How do i block outgoing traffic for a sertain program?
Can you do it with Firestarter?
Can you do it with Trickle?
Anyone got a clue? And if so, how? Do i need to know target ip-address, or something else?
I am looking for a way to block a program from all internet access, in and especially out.

---

### Post by KingBahamut on 2005-11-01
Firestarter is the more intuitive sort to use in my opinion. You can automatically set it up to be restrictive by default, and then allow whatever it is that you want to allow outside of that.

---

### Post by Iesos on 2005-11-01
how do i do to allow acces for other programs then?
for example, how do I allow total access for firefox? And then i might get a hint for other programs.

---

### Post by KingBahamut on 2005-11-01
thats as simple as creating rules, based on ports and hosts within firestarter once you get it running. Understanding how TCP and UDP ports work, and which ones function which programs is important. 

Classically 

Firefox or HTTP traffic is controlled via port 80
Gftp or ftp traffic is controlled by 21
Thunderbird or pop email recieving traffic is port 110
Thunderbird or smtp email sendind traffic is port 25 

So once you know which hosts and ports are in use by the system or systems on your network, adjusting Firestarter (if your sharing the connection with other systems it too will block / fend off for them as well) is very simple.

---

### Post by nitricacid on 2005-11-01
Typically UDP is for Games since TCP is more for basic HTTP\web browser stuff.

UDP uses a different system then TCP.
I for get how excalty they are different but UDP basicly is RAW data and not filtered as much as TCP packets. SOemthing like that.

All I know is to run my Wolf: ET server I have to use UDP and open the IP and PORT numbers so others can play on my server.

---

### Post by KingBahamut on 2005-11-01
The User Datagram Protocol (UDP) is one of the core protocols of the Internet protocol suite. Using UDP, programs on networked computers can send short messages known as datagrams to one another. UDP does not provide the reliability and ordering guarantees that TCP does; datagrams may arrive out of order or go missing without notice. However, as a result, UDP is faster and more efficient for many lightweight or time-sensitive purposes. Also its stateless nature is useful for servers that answer small queries for huge numbers of clients.

However 

The Transmission Control Protocol (TCP) is one of the core protocols of the Internet protocol suite. Using TCP, applications on networked hosts can create connections to one another, over which they can exchange data. The protocol guarantees reliable and in-order delivery of sender to receiver data. TCP also distinguishes data for multiple, concurrent applications (e.g. web server and email server) running on the same host.

Alternate forms of Transport protocol include 

DCCP - The Datagram Congestion Control Protocol (DCCP) is a message-oriented transport layer protocol that is currently under development in the IETF.

SCTP - As a transport protocol, SCTP is equivalent in a sense to TCP or UDP. Indeed it provides some similar services as TCP, ensuring reliable, in-sequence transport of messages with congestion control. While TCP is byte-oriented, SCTP deals with framed messages.

and 

RTP - The Real-time Transport Protocol (or RTP) defines a standardized packet format for delivering audio and video over the Internet.

---

### Post by Doc.Caliban on 2005-11-01
This may be asking a bit much, but can Firestarter build rules dynamically by prompting me for input whenever a process tries to access the net?

---

### Post by Iesos on 2005-11-02
Nice question Doc. Im hoping for a positive answer for that too.

---

### Post by Iesos on 2005-11-02
Ok! This is my question, when i run '$netstat -p' I get the following output about the program that i would like to block:

unix  3      [ ]         STREAM     CONNECTED     266875   13797/Prgmname
unix  3      [ ]         STREAM     CONNECTED     266828   -                   /tmp/ .X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     266827   13797/Prgmname
unix  3      [ ]         STREAM     CONNECTED     266792   -                   /tmp/ .X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     266791   13797/Prgmname
unix  3      [ ]         STREAM     CONNECTED     266692   -                   /tmp/ .X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     266691   13797/Prgmname
unix  3      [ ]         STREAM     CONNECTED     258292   -

Im guessing nothing of these numbers are ports used by the program. The numbers starting in 26... are (by netstat) called I-Node and the number 13797 is called PID. Does this information in anyway help me in finding out how to block it?

---

