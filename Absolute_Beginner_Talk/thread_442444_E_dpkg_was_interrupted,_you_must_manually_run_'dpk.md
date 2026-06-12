---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-05-13
Hi All, 
I tried to install a few programs lately through "Application--> Add, Remove"
and "apt-get install filename" and have had on several occasions th error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What does this mean and how do I solve the issue it is trying to warn me about.
From what i gather is that the package was not properly installed and I should run it from my computer, but I don't know where what the package would be or where it is..


Any help would be appreciated.

---

### Post by oilchangeguy on 2007-05-13
open a terminal and type sudo dpkg --configure -a and press enter

---

### Post by Nythain on 2007-05-13
it basically means that sometime during the installation dpkg was interrupted, or closed, or crashed...
sudo dpkg --configure -a       from inside a terminal should try to reinstall whatever was being set up when it happend

---

### Post by snoopdoggydogg on 2007-05-13
i had that problem once to... do exactly wat oilchangeguy said

---

### Post by quinnten83 on 2007-05-13
TNX guys and/ or girls.
It seems there was something with my java installation. I didn't properly finish it the last time.
(i could't get it to select ok, so I just closed the window).
seems allright now.

---

### Post by j_evenstar on 2007-05-13
does it take a long time before it's fixed? coz i have the same problem, and now it's on "setting up synaptic (0.57.8ubuntu13) ..." is this process long? thanks.

---

### Post by Happy_Man on 2007-05-13
It could be a while, depending on how much stuff was affected. I suggest just walking away, taking a nap, just leave for an hour and then come back and check.

---

### Post by j_evenstar on 2007-05-13
uhm that didn't solve the problem. when i came back the terminal is gone! i guessed it closed  without me knowing!
so i ran it again, and so far it has accomplished this
> jillian@jillian-desktop:~$ sudo dpkg --configure -a
Password:
Setting up totem (1.4.3-0ubuntu1) ...
Setting up synaptic (0.57.8ubuntu13) ...
*** glibc detected *** malloc(): memory corruption: 0x088fdac0 ***
/var/lib/dpkg/info/synaptic.postinst: line 6:  6099 Aborted                 scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing synaptic (--configure):
 subprocess post-installation script returned error exit status 134
Setting up ubuntu-base (0.120) ...
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up ubuntu-docs (6.06.2) ...


---

