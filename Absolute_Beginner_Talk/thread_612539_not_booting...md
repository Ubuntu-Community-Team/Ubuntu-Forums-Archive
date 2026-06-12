---
title: "not booting.."
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by spriizha on 2007-11-14
Hello. i have a small problem. My ubuntu on laptop don't boot any more. its just getting till:

......

* Enabling additional executable binary formats binfmt-support      [OK]
* Checking battery state...                                                               [OK]
* Running local boot scripts (etc/rc.local)                                         [OK]

and thats it. its stops there :( have no idea what to do. don't want to reinstall os again. i got too much configured stuff there..  

can someboady give some advices?

---

### Post by Peter09 on 2007-11-14
Can you boot using the recovery option, second down in the Grub menu?

---

### Post by spriizha on 2007-11-14
i can. and when i type startx its show me smth like this:


Fatal server error:
no screens found
XIO:   fatal I0 error 104 ( connection reset by peer ) on X server ":0.0"
          after 0 requests ( 0 known processed ) with 0 events remaining.

i rly don't know what to do in this kind situation :( :confused:

---

### Post by charleseddy on 2007-11-14
you can probably safely wait for a little more input from other users, but in my experience that's a hardware problem--probably w/ mobo (i.e. onboard video).  ce

---

### Post by chiefbearclaw on 2007-11-14
Ati graphics? If so welcome to hell.

---

### Post by charleseddy on 2007-11-14
okay, i realized i didn't really provide a suggestion.  try, when you boot, replacing /etc/x11/xorg.conf with an older backup file there.  generally, it will go like this, when you hit the command line in resuce mode (just don't type startx):

cd /etc/x11
ls
[there will probably several versions of xorg.conf-something; you're looking to replace xorg.conf]
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

This should replace your current graphics file with something older that should work; if you've ever made a kernel or a driver change, or even some modest updates, i'll assume that there will be some other version of xorg.conf there.  Let us know how it fares.  ce

---

### Post by spriizha on 2007-11-15
charleseddy , thanks. looks like everything is fine now. putted on some older backup. 
only - can u say, how i can safly reinstall my vcard drivers? :/ because i need direct rendering, and can't find how to turn it on :/

anyway thx i can work again ^^

---

### Post by charleseddy on 2007-11-15
As always, no problem--we're all here to help each other.  As for your issue of instaling the drivers, that depends.  NVidia or ATI?  If NVidia, the safest way is to get the drivers directly from them.  You can go to nvidia's site--here i provide the link for the download page for their latest drivers--([http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)).  It'll probably be the IA32 latest version, unless you're using 64 bit or have an older card.  Download the file and put it in your home directory.  Then open up a terminal and type.

cd ~/
sh NVIDIA-Linux-x86-100.14.19-pkg1.run (assuming that's the file you downloaded)

If any errors come up, you can post the results in this thread.  If you have an ATI card, you'll have to fish through the forums, since I'm not exactly an expert on it.  Good luck!

---

### Post by EGRAD on 2007-11-15
I'm having the same error. I tried everything in the thread (and others) but nothing works. I looked but i dont have a x11 folder in /etc. any help would be great!!!!

This is also a fresh install from a 7.04 alternate cd

hp9500t --core 2 duo  t7300 --2g ddr ram -- nvidia 8300gs

---

### Post by charleseddy on 2007-11-15
Okay, surprised that the last guy didn't catch it.  it's actually a capital x.  So, :

cd /etc/X11

Same steps as above after that.  Let me know.  The reason I'm pretty sure that you have an X11 folder is that, if you have a GUI (gnome, kde, etc.), it's running on top of X (a way they interpret graphical interfaces).  11 is the version, and that's where they store the files for X11.  Anyways, try that and let me know how it goes, egrad.  -ce

---

### Post by Crafty Kisses on 2007-11-15
> **spriizha said:**
> Hello. i have a small problem. My ubuntu on laptop don't boot any more. its just getting till:

......

* Enabling additional executable binary formats binfmt-support      [OK]
* Checking battery state...                                                               [OK]
* Running local boot scripts (etc/rc.local)                                         [OK]

and thats it. its stops there :( have no idea what to do. don't want to reinstall os again. i got too much configured stuff there..  

can someboady give some advices?

Have you tried verbose mode?

---

