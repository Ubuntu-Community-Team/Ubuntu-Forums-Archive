---
title: "forwarding X11 through ssh"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by blastthisinferno on 2007-07-19
I know there's a ton of threads with problems with forwarding X11, but none of them have helped me.  I'm on a Windows XP machine at work and I have a Feisty Fawn Linux box at my house.  I have X-Deep_32 4.0 installed on the Windows machine and OpenSSH on the linux server.  Here's my problem when I ssh into the linux box from work.

```
/etc/init.d/ssh start

* Starting OpenBSD Secure Shell server...
Could not load host key:  /etc/ssh/ssh_host_rsa_key
Could not load host key:  /etc/ssh/ssh_host_dsa_key
                                                                     [ OK ]

```

Then I try starting a simple program that needs X.

```
xeyes

Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
Error: Can't open display: localhost:10.0


```

I have X11Forwarding enabled in the sshd_config file.

---

### Post by reckless2k2 on 2007-07-19
a few things 1st......use a program called xwinlogon. it'll be a lot easier to use. make sure in your sshd config that you have xforwarding marked to yes. restart ssh then connect using xwinlogon from within your lan. then see how it works.

also...pick screen 1 or 2....something other than 0....you already have 0 running apparently.

---

### Post by asmoore82 on 2007-07-19
dig into the options on your Windows client and make sure X11 forwarding is enabled.

Also, in the past I've run across several ssh clients for Windows that allow X11 forwarding but require a separate program to be running to handle the local X stuff on the Windows box.

---

### Post by blastthisinferno on 2007-07-19
asmoore82 I've been following this tutorial [http://www.linux-tip.net/cms/content/view/302/26/](http://www.linux-tip.net/cms/content/view/302/26/) .  It seemed easy enough, but then I get this problem.

---

### Post by reckless2k2 on 2007-07-19
i won't beat a dead horse anymore. just try xwinlogon. a simple program. you don't need to have ssh running along with deep or anything. it produces the same results much less painful.

if ssh is running on ubuntu and the sshd filed is edited correctly, xwinlogon is simple. pick gnome-session and screen/server 1 or 2

---

### Post by blastthisinferno on 2007-07-19
> **reckless2k2 said:**
> i won't beat a dead horse anymore. just try xwinlogon. a simple program. you don't need to have ssh running along with deep or anything. it produces the same results much less painful.

if ssh is running on ubuntu and the sshd filed is edited correctly, xwinlogon is simple. pick gnome-session and screen/server 1 or 2

Thanks for the tip to try XWinLogon.  I gave it a try and have had problems just as I have from Cygwin.  I was originally trying to use Cygwin before the X-Deep and Putty, but no matter what I try I always have problems getting my Linux gui on my windows system.  I wish I wasn't such a noob when it came to networking, but I'm trying.

I plugged in the external IP address in the Sever field.  I plugged in the username I wanted to log into in the Username field.  I typed gnome-session because I have gnome on the linux box. I tried 0 and 1 for the Display Num because that is what you recommended. What is the point to the Font Server?

---

### Post by reckless2k2 on 2007-07-19
that's not necessary. but if you have cygwin on the win box you have to delete it. even the folder on c:. what errors do you get when you try to shh in? do you get to passwd? is it accepting key..yadda. all this you should be getting...if not.....ssh is not running and you didn't xforward on sshd. xwinlogon is crazy simple. don't run putty and get rid of cygwin and deep. reboot verify ssh is running on ubuntu:

netstat -nat (look for 22 open)

then run xwinlogon after cleanign and rebooting the machine. run on server 2. give me errors if any.

---

### Post by asmoore82 on 2007-07-19
have you tried using "XDM-Authori...." instead of "MIT-Magic..." on PuTTY?

---

### Post by blastthisinferno on 2007-07-19
> **asmoore82 said:**
> have you tried using "XDM-Authori...." instead of "MIT-Magic..." on PuTTY?

That sounded like it'd solve my problems, but it didn't.  I don't see how this is so hard for me...it sounds simple enough to just ssh into a machine, have a X system running on the local machine and have the ssh forward all the X11 crap that you're doing.

[QUOTE=reckless2k2] but if you have cygwin on the win box you have to delete it. even the folder on c:. 
[/QUOTE]

I do not have Cygwin on this computer.  I was trying Cygwin on another computer of mine.  I really didn't want to try XWinLogon because that would have been like the 5th piece of software I've tried.  I really just don't want to hassle with it.  I appreciate the help though.  One of the main reasons I started this thread was so other people with the problem I was having could solve the same problem, instead of drop everything that they had done and just start another thing.

I'm going to keep fiddling with this stuff, and if I find the answer I'll definately post it.

---

### Post by reckless2k2 on 2007-07-19
yeah i've used cygwin and xwinlogon without issue before. i'm still leaning on something on the server not working right. i'd scan that sshd conf file again. xwinlogon is dog simple. ihaven't used putty in combo with anything else because that's too much running a bunch of things and explaining it. like i said before, xwinlogon was the easiest hands down. conf the sshd file to accept xforwarding and kick on xwin and it was done. comb through the sshd file. sometimes i see people having 2 instances of xforwarding by accident.

---

### Post by reckless2k2 on 2007-07-20
sorry..should this be moved to another forum then or do you mean my talk is over the scope of this thread? 

enable xforwarding in sshd.conf

then fire up xwinlogon

that kinda is absolute beginner? i'm not sure. that's why i suggested xwinlogon. ssh and cygwin or deep too along with sshd is a little much for absolute. i don't know. i was just trying to help.

sorry.

---

