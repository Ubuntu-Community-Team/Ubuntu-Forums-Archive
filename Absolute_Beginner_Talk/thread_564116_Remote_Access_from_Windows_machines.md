---
title: "Remote Access from Windows machines?"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-09-30
hey guys,

Ive read another thead by another dude bout remote access to Ubuntu machines from Windows machines but- how do I do it, and is it possible?

thanks in advance

---

### Post by Pumalite on 2007-09-30
[http://ubuntuforums.org/showthread.php?t=340386&highlight=share+folder](http://ubuntuforums.org/showthread.php?t=340386&highlight=share+folder)

---

### Post by mlentink on 2007-09-30
Go to: System > Preferences > Remote Desktop
Fill in the form. Choose to let others share your desktop and how paranoid you'll be. Click ok.
Then in you windows box download UltraVNC Viewer. Start it up and view your desktop.
If you don't see it, configure your router to forward port 5900 to the machine you want to control. Try again.

---

### Post by hyper_ch on 2007-10-01
What kind of remote access do you want? Just access to your files or do you want a graphical interface?

---

### Post by JasonBourneLinux on 2007-10-01
Just to my files (like FTP i guess- dont quite know how to use FTP because im noob lol)

---

### Post by hyper_ch on 2007-10-01
It would be simpler to use SSH

(1) Install OpenSSH Server
```

sudo apt-get install openssh-server

```

(2) Get a SCP client for windows:
[http://www.winscp.com](http://www.winscp.com) (free and virus-free ^^)

(3) Install WinSCP and run it. As user / password use the details you log in on your ubuntu computer.

That's it ;)

If you are behind a router, you can forward port 22 to your ubuntu computer and then you could use WinSCP also from outside your lan (or any other SSH connection e.g. by Putty)

---

### Post by Distortedgamer on 2007-10-19
I am curious on how to set up a remote desktop connection from winXP to linux. I am on the winXP machine now, but connecting to linux box per ssh. I need to setup the remote connection through CLI in SSH. Any suggestions?

---

### Post by mlentink on 2007-10-19
Tell us what you want to achieve...

---

### Post by Distortedgamer on 2007-10-19
Well, my ultimate goal is just to be able to remote desktop connection to my linux box from a windows XP machine. I found a tutorial on how to do this using VNC but you have to enable XDMCP. Unfortunately, it only told you how to enable that through a GUI. I am at work and the linux box is at home. The only connection that I have to it right now is SSH. I want to be able to connect to the desktop from my windows machine!

---

### Post by bodhi.zazen on 2007-10-19
:lolflag:

See if these pages help :

[uwiki]VNC[/uwiki]

[uwiki]FreeNX[/uwiki]

[uwiki]SSHHowto[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki] * Security

---

### Post by Distortedgamer on 2007-10-19
Thanks

---

