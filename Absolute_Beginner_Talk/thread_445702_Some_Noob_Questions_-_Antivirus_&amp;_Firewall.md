---
title: "Some Noob Questions - Antivirus &amp; Firewall"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Artistar on 2007-05-16
hello,

since this is my first post here, i would like to say hello to all of you - this forum is great - it's filled with helpfull advices, so it's very difficult to find a problem that's not already been answered here. excellent.
first of all i'm a noob to Linux world, but i'm also ready to learn. it's not easy to learn even the basics of linux after working on windows for so many years, but the wish to switch most of my windows tasks to the more secure environment is strong, and seems pretty much like a challenge to me. i have Vista/Feisty dual boot, and it works like a charm. :)

everyone' s saying that there's no antivirus needed on linux, but still, what do you think about putting ClamAV for scanning my system from time to time? is it necessary?

and also, i've been using Agnitum Outpost Firewall Pro on Windows and it's an excellent piece of software if you ask me.... i know that linux has it's own built-in firewall that has all ports closed by default, but i would like to have a firewall that allows me to control all my programs and services, so i can block those that i don't want to access the internet..... tried Firestarter, but it's pretty weird piece of code - i couldn't find any of these options in it, an it also blocked all of my access to the network, so i couldn't even surf with firefox....

thanx in advance for any kind of advice :)

---

### Post by renzokuken on 2007-05-16
not sure about your firewall question, i dont know any others than firestarter (which is simply a GUI for iptables, the linux standard firewall)

as for anti-virus, in theory it is not needed, but to be honest it cant hurt and would probably be prudent to have it. ClamAV is very good for scanning from time to time and i use it on our server occasionally.

i believe AVG now also offer a linux antivirus program.

better safe than sorry i suppose

---

### Post by MrKlean on 2007-05-16
Avast also has a free Linux version, but I've never heard of one needing one !

---

### Post by ajgreeny on 2007-05-16
Guarddog is another front end to the iptables firewall in linux and I have looked at it in the past.  It seems to have more options than firestarter, which I have never got to grips with, and you can allow different protocols such as html, ftp, etc, etc.  Have a look and see if it is what you want.

For viruc checking I very occasionally scan with clamav, but this is only because I send files to other people with windows and would hate to send them something nasty.  Your linux system is certainly safe as things are at present, but the future- who knows?

---

### Post by darkworld on 2007-05-16
Hi and welcome

Ive been using firestarter a few months now. Not too sure what problems you have with it but it works like a dream in my installation. Ive heard people refer to Firestarter as a firewall but I was told its just a GUI for what your machine is doing. If thats true then im not sure how its blocking your services.


Theres a section marked security on this page that gives pointers in ubuntu.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

---

### Post by ghosting0 on 2007-05-16
This topic has been covered rather extensively in the Servers & Security forum. [http://ubuntuforums.org/showthread.php?t=131616]("http://ubuntuforums.org/showthread.php?t=131616")

All of the answers to your questions should be there. Hope that helps.

---

### Post by rich.bradshaw on 2007-05-16
There are no viruses in the wild for Linux. The only reason you might want antivirus is if you are downloading files from dubious places, then using them on a Windows pc.

I don't run any, why should I? It's up to Windows users to sort out their own security.

Firestarter is good - read what the boxes say before you agree to them in Linux - then you won't mess things up. In Windows, the answer to every dialog box is yes. In Linux, you are meant to read them.

---

### Post by Artistar on 2007-05-17
i've installed avast and it's definitely more than enough of a program for occasionally scanning. nice.

well, i gave up looking for a firewall similar to Outpost - i guess i'll just have to trust to this built-in solution....

and thank you all for replying - you have been very helpful :)

---

