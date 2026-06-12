---
title: "connecting to ubuntu box"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by WannaNo on 2006-05-05
hi all. need some advice on setting up an ubuntu box. i'm currently running ms-win2k and wish to set up a box running ubuntu, but i want to run it without monitor,keyboard and mouse. then i would like to connect and log on to ubuntu box from win2k box. is this at all possible. if so, what would you advise on how i should go about doing this.
all help greatly appreciated.:D

---

### Post by htinn on 2006-05-05
I don't have any experience with this, but it sounds like you're going to get well-versed in the use of Samba:

[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

---

### Post by cgjones on 2006-05-05
I would recommend doing the initial install right at the computer, then you should be able to unplug the monitor, mouse and keyboard. Here are a few things that you will want to do before you make it headless.

1. In the BIOS, set Halt On (or whatever it's called) so that the computer will still boot even without a keyboard, mouse and monitor. (I think the keyboard is the main thing)

2. Make sure OpenSSH server ([http://help.ubuntu.com/starterguide/C/ch07s03.html#installssh](http://help.ubuntu.com/starterguide/C/ch07s03.html#installssh)) is installed and working correctly, this will give you command line access to the computer. You might also want to look into VNC software. (Vino in Ubuntu?)

Those are the two main things that come to mind right now. Give it a try and post any problems you might have.

---

