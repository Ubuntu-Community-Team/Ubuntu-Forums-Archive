---
title: "What can I do if I'm not secure ?"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Me! on 2007-11-19
Hello all,

What can I do if i feel that I not in secure ?

I feel that some one change my trust application.
or some ports with unknown application is open

how can I close this ports ?

what is the best application to scan the security ? to solve it ?

---

### Post by Sef on 2007-11-19
Ubuntu comes installed with a firewall (IPTables.)  Firestarter is a GUI for IPTables.  It is available from Accessories > Add/Remove.

---

### Post by siciliancasanova on 2007-11-19
Firestarter is a good program to start with

---

### Post by Me! on 2007-11-19
I install an external application ( innotek VirtualBox ) from The Web , then my Synaptic can not connect to web !!

I do not know if this external application or other change some things in my system !

I want an application can close any port I select , can some one help me .

---

### Post by BobCFC on 2007-11-19
I use virtualbox every day it is safe

---

### Post by kellemes on 2007-11-19
> **Me! said:**
> I install an external application ( innotek VirtualBox ) from The Web , then my Synaptic can not connect to web !!

I do not know if this external application or other change some things in my system !

I want an application can close any port I select , can some one help me .

You got your answer already..

---

### Post by hyper_ch on 2007-11-19
For scanning open ports you can use the application called nmap. It's a terminal based program. You can read the manual page for it using:

```

man nmap

```

or if you want to have it a bit more confortable:

```

man nmap > ~/Desktop/nmap.txt

```

The second command will put the nmap manual page into a text file on your Desktop.

---

### Post by Me! on 2007-11-19
Thank you hyper_ch I will tray nmap

I want to ask you BobCFC
are you using open one or binary one , binary must download manually from its website

Thanks all

---

### Post by Me! on 2007-11-19
PORT     STATE SERVICE
80/tcp   open  http
111/tcp  open  rpcbind
5900/tcp open  vnc
9999/tcp open  abyss

that what I have

is this safe ? I do not know what are rpcbind, vnc, abyss !!

but I thing the nmap work fine , thank you hyper_ch

---

### Post by Me! on 2007-11-19
```
sudo synaptic 
```

work fine

but with 

```
gksu synaptic 
```

I have a problem in connection

Is this problem with gksu ?

---

### Post by mvanes on 2007-11-19
As long as you have the latest kernel version of Linux (kernel.org) - you're only left to ensure that your applications are up to date - which you can do via your update manager.

You should apply an intrusion detection system to your kernel, possibly apply an ACL as well. 

Also, port forward / disable unused services.

---

### Post by natehatewindows on 2007-11-19
gksuDO..im not sure if gksu work in ubuntu.

---

### Post by BobCFC on 2007-12-02
> **Me! said:**
> Thank you hyper_ch I will tray nmap

I want to ask you BobCFC
are you using open one or binary one , binary must download manually from its website

Thanks all


Sorry for the late reply.   Yes VirtualBox is not open source so it won't be in the Ubuntu repositiories, but the company innotek has their own repos with instructions on the website.

I have an entry in my sources list such as **[http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free** so that it updates itself just as the other software does, you don't have to surf and re-download & install etc.   It also removes itself just as easily.   3rd party repositories are a very flexible system.  You also get a key to sign the downloads and make sure they are official

---

### Post by Me! on 2007-12-04
> **natehatewindows said:**
> gksuDO..im not sure if gksu work in ubuntu.

gksu work in ubuntu , but not with my ubuntu !!

---

