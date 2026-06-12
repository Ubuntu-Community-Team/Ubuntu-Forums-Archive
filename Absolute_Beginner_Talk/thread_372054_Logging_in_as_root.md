---
title: "Logging in as root?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by zlegge on 2007-02-27
Okay, I installed Samba from "Add or Remove Programs"  When I opened Samba it sayed that I needed to be logged in as root.  I know the root password.  When I tryed to log in from the log in screen, it said that I can't log in as root from that window.  How do I log in as root??????

---

### Post by taurus on 2007-02-27
Why do you have to log in as root?  If you need to configure it, use sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by zlegge on 2007-02-27
What is sudo? and why should you care, all I need to know is how to log in as root it dosen't matter why...

---

### Post by Brunellus on 2007-02-27
> **zlegge said:**
> What is sudo? and why should you care, all I need to know is how to log in as root it dosen't matter why...
sudo is a means by which a regular user is granted superuser privileges for a limited amount of time (usually one command) and in a way that leaves a traceable record of actions (with commands executed under sudo logged in /var/log/auth.log). 

Complete details of what sudo is and why Ubuntu disables the root account by default can be found in [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

Finally, I'd like to add that responding to an otherwise helpful post in a hostile manner is frowned upon on these forums.  We're volunteers here--plain old users--not paid staff.  Do NOT abuse us like you would abuse paid helpline people.

---

### Post by Quillz on 2007-02-27
> **zlegge said:**
> What is sudo? and why should you care, all I need to know is how to log in as root it dosen't matter why...
Actually, it does matter. Linux is not Windows. Running as a root user at all times can be very damaging to your system. Sudo is a command that lets you execute commands as root in an emulated Terminal state. That is how you need to run Samba. 

One of the most fundamental rules of Linux is you never, ever run as root. This is why sudo is here... For the rare times you need to be root, you can, safely.

---

### Post by ddom87 on 2007-02-27
You can set the root password in users; SYSTEM ---> ADMIN ---> Users and Groups. Tick the box below that says show all users and groups. Then find the root user, hit properties at the bottom is should say password: Set (text area) Change your password here. click ok 

then you should be able to log in as root 

ITS NOT RECOMMENDED its a security risk. But afterall it is your system.

---

### Post by zlegge on 2007-02-27
I'm sorry, I didn't see the link you put.  Ummm.. I didn't understand it.  What command line do I use to log in as root or sudo???

---

### Post by Brunellus on 2007-02-27
> **zlegge said:**
> I'm sorry, I didn't see the link you put.  Ummm.. I didn't understand it.  What command line do I use to log in as root or sudo???
open a terminal.  

at the prompt, type

sudo COMMANDNAME

where COMMANDNAME is the name of the command you want to execute with root priviliges.

you will be prompted for a password.  type your USER password.

The command will execute with root privileges.

If you need a root shell, execute

sudo -s

that will give you a root shell, but be advised that this is NOT RECOMMENDED.

If you need/want to manage files graphically as superuser, it's 

gksudo nautilus

this is **HIGHLY DANGEROUS** GUI file management + root privileges = HIGH potential for mistakes that are **NOT RECOVERABLE**.  Be sure you know what you're doing if you mess with things outside of /home.

---

### Post by zlegge on 2007-02-27
Thank you!  At least I figured out how to log in as root but I can't understand Samba.  With Windows File, and Printing sharing is very easy.  Maybe I'll just switch to windows.  Sorry about before I was just mad that he wanted to know why I needed to log in as root and I have  a headache.  I wasn't trying to be mean or anything.  But thanks for your help!!:)

---

### Post by Brunellus on 2007-02-27
if your question was about samba, why on earth didn't you ask a question about samba?

I note that everything I typed was covered in the wikipage we referenced.

---

### Post by Quillz on 2007-02-27
> **zlegge said:**
> Thank you!  At least I figured out how to log in as root but I can't understand Samba.  With Windows File, and Printing sharing is very easy.  Maybe I'll just switch to windows.  Sorry about before I was just mad that he wanted to know why I needed to log in as root and I have  a headache.  I wasn't trying to be mean or anything.  But thanks for your help!!:)
If you're having trouble with Samba (as I did, it is a bit confusing,) simply ask for it in a new thread. Don't give up on Ubuntu just because of one pitfall. I think once you get it set up to your liking, you'll see it can be just as productive as Windows.

---

