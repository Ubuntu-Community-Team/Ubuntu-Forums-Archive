---
title: "Headless system."
date: 2011-04-09
forum: Any Other OS
---

### Post by mbudden on 2011-04-09
I'll try to keep this short.
OS: Linux Mint LXDE

I have a computer that is headless that I use as a Minecraft/Ampache server. Problem is, it doesn't like when I don't have a monitor installed. I have X11VNC Server installed so I can VNC into to. But when there is no monitor installed, it doesn't allow me to connect/boot. But when one is connected, it's fine and boots up perfectly. 

I have been reading about /etc/init.d/xorg and editing that. But the problem is, when I try. It's empty. But most of those guides/details are for Gnome. 

Any way I can go headless without having to have a monitor connected at boot? It's quite a pain to reset and have to bring the monitor out just so it can go into the OS. Thanks.

---

### Post by mbudden on 2011-04-09
Sorry for the bump.

But it seems that without the monitor installed x11vnc isn't starting on startup. I can SSH into the machine and manually start x11vnc and then I'm able to connect. 

I find that quite strange... Wondering if there is a way I can get around that and having to do all that unnessicary work. I close Putty and TightVNC closes. Hmm.

---

### Post by spynappels on 2011-04-09
Is there a specific reason you need the GUI? If you can ssh in, you can control the server, and for GUI tasks you could have a look at X forwarding through ssh. Then the server is not using resources for running it's own GUI and you don't have the risks often associated with running VNC.

---

### Post by volkswagner on 2011-04-09
Do you have it set to autologin a user?

---

### Post by mbudden on 2011-04-10
> **spynappels said:**
> Is there a specific reason you need the GUI? If you can ssh in, you can control the server, and for GUI tasks you could have a look at X forwarding through ssh. Then the server is not using resources for running it's own GUI and you don't have the risks often associated with running VNC.

Because it's easier for editing files and downloading the files I need. I read about using X through SSH but I didn't understand how to do it, so I just used VNC. 

But you talk about risks, what risks? 

> **volkswagner said:**
> Do you have it set to autologin a user?

Correct.

---

### Post by spynappels on 2011-04-10
> **mbudden said:**
> Because it's easier for editing files and downloading the files I need. I read about using X through SSH but I didn't understand how to do it, so I just used VNC. 

But you talk about risks, what risks? 


Incorrectly configured VNC servers are the most common reason for compromised Linux systems.

For a simple tutorial on X Forwarding, look at [http://solaris.reys.net/how-to-x11-forwarding-using-ssh-putty-and-xming/](http://solaris.reys.net/how-to-x11-forwarding-using-ssh-putty-and-xming/)

I use it on both Ubuntu and CentOS without problems, and it is more secure than VNC, especially if you use public key authentication for SSH.

---

### Post by CharlesA on 2011-04-10
In your case, I'd suggest using FreeNX from NoMachine. It's more secure then VNC and works great.

---

