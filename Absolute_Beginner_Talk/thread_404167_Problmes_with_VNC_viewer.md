---
title: "Problmes with VNC viewer"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by scienceboy on 2007-04-08
Hi
I set up my computer just as it says on the ubuntu wiki
however, when i go and type in the command line, i get the following
vncviewer: connecttotcpaddr : connect : connection refused
unable to connect to vnc server

I suspect that it might have to do with my IP address. The computer is located on a network.
Does anyone know how to fix this? DOes it have to do with my IP address? If it does, how do i find the IP of this exact computer? and what is with the second line in the error message?
Thank you In Advance

---

### Post by LaurelLynn on 2007-04-08
Dear scienceboy,

The problem could also be that the default Ubuntu install only has the VNC Client (not the server, at least thats the way I remember it).  So until you download the server (with Synaptic or apt-get) from Ubuntu you can connect out but not in.

Another thought is to consider Tight VNC (should be available for Unbuntu, or at least Debian).  Tight VNC is much faster because it uses better compression.

Also check out any Firewalls inbetween, they have to be configured to let the connection go thru.

Note: VNC sends everything in the clear, even passwords (anyone can easedrop) so it is safest to use it through an ssh connection.

Laurel Lynn

---

### Post by scienceboy on 2007-04-08
which packet should i download? there are quite alot of them, and most of them say the same thing

---

### Post by LaurelLynn on 2007-04-08
Regular VNC is available from one of the repositories. For TightVNC I would go to the project page.    Look for Ubuntu directions in the download section.  They may list a repository to add to Synaptic. They might also have a ¨.deb¨ file for Ubuntu or Debian.  Last and least desirable is a tar file with the source code.

If you searching on SourceForge.com they will have TightVNC, the download page will have a link that says ¨Project website¨

Laurel Lynn

---

### Post by scienceboy on 2007-04-08
umm ... i think that i just completely messed this up on my comp ... i just got linux, i'm still getting used to it ... which packages do i need to have installed? including client packages ...
the only thing i really know how to do (asides from basics) are running java programs and c/p in the terminal
thank you for putting up with my stupidity
-scienceboy

---

### Post by LaurelLynn on 2007-04-08
One good thing about ubuntu is that you have to type in the root password to really mess things up.

What you need to find is a how-to or guide to VNC specifically for Ubuntu.  Here is a link to one:

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

I would read two or three before attempting to install it (just so you have multiple oppinions on the right way to do it).  I found that one from Google ¨ubuntu vnc guide¨ there were some others.  You might also try replacing guide with how-to.

That one is nice because it has screenshots of the process.

Good Luck

Laurel Lynn

---

### Post by r00tintheb0x on 2007-04-08
Laurel Lynn

Have you ever considered X11 over SSH or XDMCP? Its a lot less resource hungry and a lot quicker.

Mike

---

### Post by LaurelLynn on 2007-04-08
Yes r00tintheb0x,

For my own network I was considering NXfree over ssh.  The only problem is with people who have to use to talk to Windows boxes. They are primitive machines which don´t speak X (maybe with Cygwin it would work).

So for some there is still a need for VNC, or Remote Desktop

Laurel Lynn

---

### Post by r00tintheb0x on 2007-04-08
Laurel Lynn,

If its for a corp environment, we use [http://www.hummingbird.com/products/nc/exceed/index.html](http://www.hummingbird.com/products/nc/exceed/index.html) at work... works great. For a non corp environment, Cygwin would work.

Mike

---

### Post by LaurelLynn on 2007-04-08
Wow, I haven´t seen a copy of Exceed in almost 10 years, been spending too much time working in the Windows world. Yes, they would be more reliable than Cygwin, if you can afford the price.

Laurel Lynn

---

### Post by bmt on 2007-04-08
> **scienceboy said:**
> which packet should i download? there are quite alot of them, and most of them say the same thing
For a gui front-end, try Terminal Services Client (tsclient in Synaptic main).

The I find the best vnc viewer on Linux is xvnc4viewer (also in Synaptic, but universe).  It has fewer quirks and is more up to date than the default viewer, at least in Dapper.  I think xvnc4viewer is based on TightVNC.  I use it frequently to remotely help family members on Windows.

Unfortunately, vncviewer on Linux is not as friendly as on Windows, where it has a toolbar icon and a possibility to change settings.

Try a search on 'vncviewer' on these forums -- there is quite a bit of experience there and several step-by-step instructions, with and without ssh.

---

