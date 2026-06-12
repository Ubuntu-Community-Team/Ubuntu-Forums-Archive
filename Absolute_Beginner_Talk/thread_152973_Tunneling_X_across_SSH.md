---
title: "Tunneling X across SSH"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by wiz561 on 2006-03-31
Hi!

   I'm having some problems trying to tunnel X apps across SSH to my machine.  I've tried and looked, but can't find anything that will work.  It's a default "server" install of Ubuntu with nothing special.  On the client, I have done..

ssh -X <ip>
-and-
ssh -Y <ip>

    Either one doesn't work.  I've also tried to export the display variable as localhost:0.0 and localhost:10.0, but nothing works.  Whenever I do that, it says "Can't open display: <whatever the display variable is>".  

    On the client end, I'm using Mac OS X 10.4 with X11.  I have done this before on my computer, so I know that it works...but I can't get it to work with the ubuntu machine.  


Thanks for any help!
Mike

---

### Post by stuporglue on 2006-03-31
Are you using the X term? Not Apple's Terminal.app, it needs to be the Xterm.

---

### Post by hw-tph on 2006-03-31
Is "X11Forwarding" set to "yes" in the /etc/ssh/sshd_config file on the server?


Håkan

---

### Post by Gustav on 2006-03-31
If it's a server install of ubuntu on the server there are no X to forward. 

Or does it not work that way?

---

### Post by wiz561 on 2006-03-31
Hi!

   Yes, I'm using Apple's xterm and not the terminal app.  I've also added those lines to sshd_config and restarted sshd...heck, I even restarted the computer!  

    To my knowledge, if you do a server install, you can't run X apps on the server console....but you should be able to tunnel the apps over SSH to view them on a workstation.  I've also installed xauth on the server, but nothing works.  


Thanks!

---

### Post by wiz561 on 2006-03-31
Hi!  Well, I finally figured out what the problem was.  I turned on the debugging mode of sshd and watched the log file while logging in.  I kept seeing this message...

error: Failed to allocate internet-domain X11 display socket.

	A google search brought me to this page...

[http://giray.devlet.cc/Linux/Laptop/HiGradeNotino3400s/](http://giray.devlet.cc/Linux/Laptop/HiGradeNotino3400s/)

	Turns out that it's related to some sort of problem when I tried to setup the second NIC.  I removed the information I put in the interfaces file, rebooted, and now everything works beautifully.


Thanks!

---

### Post by R3linquish3r on 2006-03-31
Is there a terminal program for Windows that I wold be able to use to tunnel to my desktop?

---

### Post by cwaldbieser on 2006-03-31
[QUOTE=R3linquish3r]Is there a terminal program for Windows that I wold be able to use to tunnel to my desktop?[/QUOTE]
Any ssh client can do the tunneling.  The tricky part is having an X Display server on your Windows client.  Cygwin can be configured to do this, and there are various non-free options.

A simpler option might be to just get a VNC client for Windows (e.g. tightVNC).  You can tunnel that over ssh (via putty, for example) if you want a more secure connection.

---

### Post by R3linquish3r on 2006-03-31
Is cygwin a free program? If not can you recommend any free ones?

---

### Post by cwaldbieser on 2006-04-01
[QUOTE=R3linquish3r]Is cygwin a free program? If not can you recommend any free ones?[/QUOTE]
Yes, it is free.  Here is the link to the home page for Cygwin/X, which includes the X Display server you want:
[http://x.cygwin.com/]("http://x.cygwin.com/")

Basically, the setup program for it is similar to using something like apt-get or synaptic.  You download a bunch of packages to your PC, and you can start a *NIX style shell (bash by default, I think).

---

### Post by R3linquish3r on 2006-04-01
Gotcha, then I can SSH X from my home desktop. Thanks :)

---

