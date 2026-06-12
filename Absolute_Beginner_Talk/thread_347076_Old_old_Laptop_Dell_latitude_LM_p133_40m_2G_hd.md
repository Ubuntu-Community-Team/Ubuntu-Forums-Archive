---
title: "Old old Laptop Dell latitude LM p133 40m 2G hd"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by marc66thomas on 2007-01-26
I have been bouncing around distros for this laptop. Dell Latitude LM 3com ethernet card P133   40 MB RAM 2G of disk space. Tried Free bsd, redhat 8, and would like info on Ubantu.

Can you suggest if Ubantu will load and boot into this near door stop of an old laptop? It was fully functional as a win 98 box. but I was unconfortable with the virus threats that inherantly are in WIn98 over a cable modem (routher is in front of the laptop).

My Goal:
Boot into a GUI surf the net and mail. Not much else is requred -important.. (I like firefox and the Ubantu interface) under Dapper Drake

Thank you in advance.
suggestions requested even if it's go away!

---

### Post by josys36 on 2007-01-26
Run Windows for Workgroups 3.11!

:)

---

### Post by OldTimeTech on 2007-01-26
Have you thought about using Damn Small linux or puppy linux, either of those should work fine on that old of a Dell.  I have an old 166mhz IBM that I use puppy linux on.....not enough hard drive to run ubuntu and have room for files.

---

### Post by towsonu2003 on 2007-01-26
try this one: [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

the basics:
0. install ubuntu from the alternate CD with the option "server" (no quotes)
1. Enable the universe-repository by removing the Hashmarks in file /etc/apt/sources.list
2. ```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install icewm
sudo apt-get install xserver-xfree86
sudo apt-get install x-window-system-core
sudo apt-get install xdm
sudo apt-get install numlockx
sudo apt-get install xterm
startx #don't use sudo with startx

```
check out the software list of Damn Small Linux for a list of nice low-requirement software for doing work.

---

### Post by marc66thomas on 2007-01-26
Thank Folks for the quick responses and suggestions.

WIN 3.11 for work groops... No cuz I want to use and learn about Linux 
Puppy ... I have looked at it I'll need more time b4 I commit. 
Ubuntu/Debian-Sarge Mini-RAM HOWTO ... looks like a winner to me.

I appreciate the suggestions.

---

