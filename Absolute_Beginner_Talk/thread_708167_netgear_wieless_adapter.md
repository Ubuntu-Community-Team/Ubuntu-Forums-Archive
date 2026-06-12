---
title: "netgear wieless adapter"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Stef11 on 2008-02-26
Hi all. Due to lack of support for netgear W311v3 card have loaded ndiswrapper and device chip driver as per instructions from this site. One of the tasks as per instructions was to insert the kernel module with command: sudo modprobe ndiswrapper. lastly to ensure that this is loaded each time i boot my computer, i included: sudo ndiswrapper -m

The problem is each time i reboot the system i need to retype the command in terminal:
sudo modprobe ndiswrapper
and then it asks me for my keyring passphrase
each time i retype the command:
sudo ndiswrapper -m
it tells me its already been done.

what have i done wrong?
PS i can still connect to my wirless router but i need to reload the module each time
help much appreciated
regards
Stef11

---

### Post by anewguy on 2008-02-26
In a terminal window do the following:

cd /etc

gksudo gedit modules

add ndiswrapper to the end of that file then save it

I believe when you reboot it will work now.  As I understand it, this file contains modules you want loaded at boot time.  Someone may correct me if I am wrong.

:)

---

### Post by Stef11 on 2008-02-27
Thanks for your help and I will try that now and let you know
regards
Stef11

---

### Post by Stef11 on 2008-02-27
anewguy, thanks, have typed in
 cd /etc
gksudo gedit modules
But received no response from command line. Sorry for my lack of knowledge of linux, but arethe two lines above to separate commands, or should it be all on the one line.
Thanks
Stef11

---

### Post by anewguy on 2008-02-28
Sorry it took so long to get back here.  I had Gutsy installed for a few months, then went back to Feisty, then decided yesterday to let it go ahead and do the update to Gutsy.  Due to me falling asleep, I didn't catch some things that required my response until today, so basically I couldn't do anything until today.

For your question, each should be on a separate line, each followed by pressing the enter key.  We're going to "cheat" (some people say use gksudo, but I've never had a problem with sudo), so what you should be able to cut and paste from here are the following:


cd /etc

sudo gedit modules

This should ask for your password.


at the end of the file, add the following line:

ndiswrapper

then save the file, exit, and reboot.


If that doesn't work for you, post back and I'll try to get back to you quicker!  :)

---

