---
title: "Vnc"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-04
I'm trying to connect remotely to my ubuntu box from a windows machine.
I downloaded vnc4server using
sudo apt-get install vnc4server
then after running it, i entered the password that clients will have to give.
however, after attempting to connect to it, using the same box. (using a viewer from the server box)
it gave me the error:
connection refused
Now, is this due to a port problem?  People tell me i should NOT have open ports for vnc to use, but instead forward the vnc ports through ssh.  Anyone know how to do this? Would putty be a better choice for this, rather than the vnc viewer?  I don't have any firewalls installed, unless there is one that came installed on regular ubuntu gutsy.
How do i access my ports, and furthermore how do i forward them through ssh to vnc?
thanks.

---

### Post by mlentink on 2007-11-04
There' s an easier option.
Go to:
System>Preferences>Remote Desktop
Answer all questions. It will even show you how to access the box in question.

Works for me, I access my box (after forwarding port 5900 in my router) every day form work, where I unfortunately have to use Windows quite often.

---

### Post by wigg on 2007-11-04
Connection is refused because your linux box isn't allowing connections on that port or from the ip of your windows box.  This could be for a number of reasons.  You could have a  program like Moblock that is filtering iptables, a firewall, etc...  What I would suggest is following a vnc over ssh tutorial from the web.

Here is the one I used when I set this up on my SuSE box:
[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Another thing you might look into is port knocking.  It will allow you to connect to ports by only opening them when the correct sequence of port requests are made.  I think you can set that up with something called "Sure Wall."  It's something I've been reading about so I'm not going to claim to be the expert.

T

---

### Post by jordank on 2007-11-04
following the system>preferences>remote desktop approach, it tells me users can connect  to your desktop by typing the command vncviewer jordan-laptop:0
what does this mean? what if i want to access my box from 
a) a windows box
b) outside the lan?

what do i use/type?

---

### Post by jordank on 2007-11-04
> **wigg said:**
> Connection is refused because your linux box isn't allowing connections on that port or from the ip of your windows box.  This could be for a number of reasons.  You could have a  program like Moblock that is filtering iptables, a firewall, etc...  What I would suggest is following a vnc over ssh tutorial from the web.

T

I havent installed any programs like Moblock or a firewall.
Do either of these come installed?
how can i check if i'm behind a firewall or if moblock is running?

i am not behind a router.

---

### Post by wigg on 2007-11-04
> **jordank said:**
> I havent installed any programs like Moblock or a firewall.
Do either of these come installed?
how can i check if i'm behind a firewall or if moblock is running?

i am not behind a router.

If you haven't installed moblock then you don't have it.

As for the firewall you will most likely need to check your windows firewall settings. Laughably I don't have a computer with Windows installed to help walk you through configuring you firewall.  If you are trying to make this connection from a work network.  Chances are you network administrator has prevented you from communicating on most ports.  You could try tunneling the connection on port 80, but your isp you have at home might block that port.  This problem is very hard to give specific answers too without knowing how the 2 networks you are trying to use are configured.

---

### Post by jordank on 2007-11-04
i dont think you understood the question. i was trying to connect to the server box using a client from the same box.
it's not a windows side problem.
if i try to connect to the same computer i'm running vnc server on, with a viewer, it gives me connection refused. why is it?

---

### Post by mlentink on 2007-11-04
Have you installed a vncviewer on your windows box? I would suggest [UltraVNC]("http://www.uvnc.com/"), but others (RealVNC or TightVNC) should work similarly. 
Obviously, if you're at a remote location, you need to use your public IP-address (i.e. your router external adress) not your internal name or IP address.

Say your internal address is 192.168.0.2, and the external address of your router is 123.567.890.123, you would have to use the latter for your vncviewer

---

### Post by mlentink on 2007-11-04
Wups, sorry, hadn't read your last post. 
I have never actually tried to do that, connecting to a VNCserver with a VNCclient on the same box. Theoretically, afaik that should work. Have you tried it with two different boxes as well? That would be the most common situation...

Obviously you would then have to use ' localhost' for the name of the vncserver

---

