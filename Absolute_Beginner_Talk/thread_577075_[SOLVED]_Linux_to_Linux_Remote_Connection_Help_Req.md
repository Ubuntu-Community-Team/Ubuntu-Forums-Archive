---
title: "[SOLVED] Linux to Linux Remote Connection Help Request"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Dan_G on 2007-10-15
I am new to Ubuntu Linux but not to Unix, which I have been using to host legacy applications since the early '80s. I am trying to migrate away from Windows as much as possible. During the transition, interoperability is important.

So far I have figured out how to remotely log into a Windows systems via RDP from Linux. I have also figured out how to remotely log into a Linux system via Xming from Windows. I am not able to find a good guide which explains how to remotely log into a Linux system from another Linux system. 

I have searched without success for a guide explaining how to do a Linux to Linux remote login. Any assistance would be greatly appreciated.:)

---

### Post by Dr Small on 2007-10-15
*How* do you want to connect to another linux box ?
Samba?
SSH ?
VNC ?

I mean, what is your sole purpose ? To be able to access files, execute commands or port the desktop over to your box ?

Dr Small

---

### Post by Dan_G on 2007-10-15
File sharing is not the problem (got that sorted out). Mainly I need to be able to login into the system over a LAN in order to use it as though I were logged in as a console user. Updates, maintenance, etc for other desktop users. Also I have one system I am using for testing & development which has no keyboard, mouse or monitor. I would like to be able to log into it in a similar way that you can terminal into a Windows Terminal Server box.

---

### Post by wormser on 2007-10-15
I would recommend [FreeNX]("http://freenx.berlios.de/") or [NoMachine NX]("http://www.nomachine.com/").  I am not sure which one is better for Ubuntu but it is faster than VNC and designed to be secure.  Search the forum for installation guides.

BTW, it looks like the FreeNX site is currently down.

---

### Post by Tjarn on 2007-10-15
> **Dan_G said:**
> I am new to Ubuntu Linux but not to Unix, which I have been using to host legacy applications since the early '80s. I am trying to migrate away from Windows as much as possible. During the transition, interoperability is important.

So far I have figured out how to remotely log into a Windows systems via RDP from Linux. I have also figured out how to remotely log into a Linux system via Xming from Windows. I am not able to find a good guide which explains how to remotely log into a Linux system from another Linux system. 

I have searched without success for a guide explaining how to do a Linux to Linux remote login. Any assistance would be greatly appreciated.:)

For what it''s worth... here's what I do.  (Oh and I use it to both a Lunux machine and an OpenBSD machine from my normal box.)   On my personal box I install the VNC client.  xvncviewer.  I've been on the command line so long it's easier for me to type 'sudo apt-get install xvncviewer' than find it in the gui instaler.

On the remote machine, (still running Dapper I think) it's 'apt-get install vncserver'  (or the gui equivalent)

I make sure that the ssh server is running on the remote machine and that I've installed the ssh client locally and that I have the same login name on both machines.  (not necessary, but simpler)

Then its  'ssh opal' (the remote machine) and I log in.
there, I give the command to start the vncserver.

opal$  vncserver :5 -geometry 800x600

(actually I have the command in a script there)

Then I log out of opal.

Back on my desktop machine I can run the command 'xvncviewer opal:5'
It prompts me for a password, accepts and then I'm sitting at a 800x600 screen on opal. 

The size of the screen is set with the -geometry argument on the server side.  There are a number of VNC programs around.  tighvnc, realvnc are two that I remember.  There's also a faster NMclient viewer from ...hmm NoMachines?  something like that.  And there is the terminal server client that speaks VNC so you can skip the xvncviewer if you wish.

Good luck.

---

### Post by scrooge_74 on 2007-10-15
You can also follow this guide:

[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

EDIT: this is the link I wanted to show  [http://ubuntuforums.org/showthread.php?t=499431](http://ubuntuforums.org/showthread.php?t=499431)

---

### Post by Dan_G on 2007-10-15
Thanks to you all! Great info. Looks like I will be busy this evening digesting all the feedback.:)

---

### Post by Tjarn on 2007-10-15
Oh, and there's some assumptions with my procedure.  That you're behind some sort of strong firewall that keeps your exposure down.  The more secure alternatives all work fairly similarly.

---

### Post by Dan_G on 2007-10-15
Thanks Tjarn. I'm behind a router & SonicWall which are tightly locked down, so I'm not to worried about the LAN traffic from a security standpoint.

---

### Post by totalnub on 2007-10-15
just install openssh-server. ssh into the box via console on your machine and poof! you're right there.

you can also run graphical apps by using the -X option.

e.g.
user@box$ ssh -X username@ip address of linux box connecting to 
type in password
then 
username@remote box $ _    

there you have it :)

---

### Post by mysurface on 2007-10-15
> **totalnub said:**
> just install openssh-server. ssh into the box via console on your machine and poof! you're right there.

you can also run graphical apps by using the -X option.

e.g.
user@box$ ssh -X username@ip address of linux box connecting to 
type in password
then 
username@remote box $ _    

there you have it :)

You may wanna use -Y instead of -X

---

### Post by scrooge_74 on 2007-10-15
Yep, much better to use -Y

---

### Post by totalnub on 2007-10-15
yea, my bad, don't know how old the unix machine is. lol
on my ubuntu computer i use -Y, but on the solaris machine at school i have to use -X....guess i've been at school too much. GL and have fun messing around :)

---

### Post by Dan_G on 2007-10-16
Thanks to all for your help! Problem solved. NXClient/Server did the trick.:)

---

