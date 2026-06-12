---
title: "Remote Desktop"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by tennyis on 2006-07-02
Hey Guys/Gals, 

I have been a computer tech for about 5 years now in a complete Windows environment. As our company is expanding and the world is changing I feel I really need to start to learn about Linux. I've been told Ubuntu is a great place to start. I'm likely going to try it out on Vmware on my laptop but I'd like to eventually switch to Linux completely. 

The big thing holding me back though, is I absolutey must have a remote desktop connection to our office windows terminal server on my laptop. Are there any ways of accomplishing this in Linux? With windows I just use the remote desktop client that comes with XP. I've done some google searches and I notice there are a few programs that allow this but only to Linux server. 

Any help would be greatly apprecated!

---

### Post by majstor on 2006-07-02
Dont know if thats what you need but i use RealVNC [www.realvnc.com](www.realvnc.com) for remote loging into brothers Windows when I need to shut down his Azureus ;). Works OK.

---

### Post by T700 on 2006-07-02
There are a variety of ways, but for plain vanilla simple, I like [VNC]("http://www.realvnc.com/").  

Paul

---

### Post by tennyis on 2006-07-02
no,it's not a VNC connection it's a terminal server connection.

---

### Post by izmaelis on 2006-07-02
Check out [this]("http://www.rdesktop.org/"). I connect to my windowsy work machine with it. Looks like it's working fine.

---

### Post by tennyis on 2006-07-03
[QUOTE=izmaelis]Check out [this]("http://www.rdesktop.org/"). I connect to my windowsy work machine with it. Looks like it's working fine.[/QUOTE]

Thanks, that worked perfect!

---

### Post by rtcary on 2006-07-03
I use VNC to remotely access my Linux and Windows work stations.  What is the difference between using VNC and rdesktop?

Many thanks....

---

### Post by lamego on 2006-07-03
Remote Desktop uses a the Windows Terminal Services which comes already with Windows and should be better integrated with the system. For VNC you will need to install the vnc server yourself.
I don't kown much about the internals but I believe that unlike VNC the windows remote desktop uses encryption.

---

