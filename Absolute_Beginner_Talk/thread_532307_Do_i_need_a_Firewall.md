---
title: "Do i need a Firewall?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by blinkja on 2007-08-22
well i am using non stop ubuntu and tough about firewall am i expoced to attack?
and i am beginner in linux firewall the similar threads have a link to firestarter and the threads are 2 yas old.

can anobody help me?
i am absolute begginer!!!!!!!!!1

---

### Post by splintercellguy on 2007-08-22
It depends on how you connect to the Internet. Ubuntu already comes with firewall functionality, namely iptables, but the repositories have a tool called Firestarter which will let you administer iptables via a GUI. If you're behind a router, you probably don't need one. Ubuntu does not run any services by default, but if you are directly connected to the Internet, turning on the firewall may help.

---

### Post by WebSiteGuru on 2007-08-22
No need for it. But you still have an option to load firestarter.

---

### Post by bapoumba on 2007-08-22
SIde note: firestater is in universe, so you will need to enable these repositories to install it.
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by blinkja on 2007-08-22
I am absloute begginer as i said early does firestarter is good for begginers and i surf a lot of warez and stuff just for knowledge.

---

### Post by AceofSpades19 on 2007-08-22
you don't really need firestarter, its good to have but not neccessary

---

### Post by tyggna1 on 2007-08-22
Firestarter just lets you maintain the firewall that's already there.  It would let you beef up security, if you want--but unless your a server and online 24/7, and you have enemies with good computer skills--I wouldn't worry about it.

---

### Post by WebSiteGuru on 2007-08-22
> **blinkja said:**
> I am absloute begginer as i said early does firestarter is good for begginers and i surf a lot of warez and stuff just for knowledge.


You are thinking in M$ Windows environment. ;)

---

### Post by splintercellguy on 2007-08-22
> **blinkja said:**
> I am absloute begginer as i said early does firestarter is good for begginers and i surf a lot of warez and stuff just for knowledge.

Not exactly a good idea to say you surf for that stuff :P. Yes, Firestarter should be fine for beginners.

---

### Post by blinkja on 2007-08-22
I just installed firestarter
thanks all,
1 last question

is there any rule i should put in there.
i dont run server just browsing nasty sites, (for knowledge purposes only) :confused:

---

### Post by schorsch on 2007-08-22
If you do not run any services on your machine you will be safe even without a firewall. What is the output of:
```

sudo apt-get install nmap
sudo nmap localhost
```
A software firewall does NOT protect you from bugs inside your browser or another application that uses the internet as long as the connection is triggered from the inside, from you.

---

### Post by tyggna1 on 2007-08-24
Just FYI:  Linux started as a sort of pet-project for hackers.  Even today, the understanding of computer security can be seen in the OS.  The people who started this whole crazy linux thing new security, and new what they needed to keep themselves one step ahead.

---

### Post by rexy on 2007-08-24
ubuntu by default has the firewall disabled, This is not a huge risk since it also by default has no services it exposes to the internet. Regardless configuring a firewall using firestarter is still a good idea.

Remember  that by default firestarter blocks all incomming connections, something you normally dont need, but for programs like bittorrent programs you might want to open ports.

---

### Post by xpod on 2007-08-24
I`d advise anyone to have a read through[THIS](http://ubuntuforums.org/showthread.php?t=510812),it`s full or great information and should help most people understand things a little bit better.

---

### Post by silent1643 on 2007-08-24
> **blinkja said:**
> well i am using non stop ubuntu and tough about firewall am i expoced to attack?
and i am beginner in linux firewall the similar threads have a link to firestarter and the threads are 2 yas old.

can anobody help me?
i am absolute begginer!!!!!!!!!1

bah in short no, you dont need a firewall
but if you must try firestarter or kmyfirewall

but i haven't used a firewall since my install and have had 0 problems

---

