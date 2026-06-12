---
title: "[SOLVED] vnc dropdown menu"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Bigbird999 on 2007-11-16
I am using my old laptop to learn Linux, surf the web, email and manage my windows based home theater DVRs with xvnc4viewer.  When I open vnc4 viewer in windows, it "remembers" the previous IPs that I have entered, and presents them in a dropdown menu 192.168.0.12  -  192.168.0.17 etc.  It saves me from havng to type them in every time I want to connect.  It is not a big deal but it is a PITA for me on a keyboard with no numpad. 

So is there any way to make the Linux version of the VNC viewer behave the same way as the windoze version, or alternately, make shortcut or single click icon that would launch vnc viewer with the ip address already entered. Then I would only have to enter the password.

BB

---

### Post by eldragon on 2007-11-16
what i do is add a cool name to the LAN ip in /etc/hosts

then you just run vncviewer coolname

---

### Post by Bigbird999 on 2007-11-16
Thanks! I added "192.168.0.14    htpc" to /etc/hosts and now i can launch from terminal by typing xvncviewer htpc and it presents me with the password screen .  Almost perfect!   Now, is there any way to put an icon on my desktop that will launch xvnc4viewer htpc and take me to the password screen with no typing??  I'm a terminalphobe and prefer simple GUI methods for oft repeated tasks.  

BB

---

### Post by Bigbird999 on 2007-11-16
Browsing threads and discovered how to make an application launcher on my desktop.  Created one for my HTPC with the command xvnc4viewer htpc.  Combined with the /etc/host edit above (thanks eldragon) it gibes me the vnc pasword screen and I am connected.  Exactly what I wanted.  Now I will try and figure out how to mark this thread solved.

BB

---

