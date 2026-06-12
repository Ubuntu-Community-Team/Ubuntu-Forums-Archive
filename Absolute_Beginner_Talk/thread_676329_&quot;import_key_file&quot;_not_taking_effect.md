---
title: "&quot;import key file&quot; not taking effect"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by boobahzone on 2008-01-23
I've been working to install beryl on my Ubuntu 7.10 system using the instructions provided on Lennart Hansen's guide ([http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)), but I've been having trouble importing the "key file" to work.

This is what I've done so far on my quest for beryl.  I should note that I've been using Ubuntu's built-in GUI-based controls rather than the command line, but both methods have sprung up with the same problem at the "key file" step.
-I updated my system before I began working on it
-I then added the [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) repository via the "Software Sources" program on Ubuntu.  
-Then, I download the file [email]root@lupine.me.uk.gpg[/email] (from [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg))
-I opened the Software Sources module, and from the Authentication tab from the Software Sources program, I import [email]root@lupine.me.uk.gpgs[/email] as a key file.  However, when I ran this step I initially got an error message.  When I retried my steps, I would not get the error message any more, but the key still does not show up in the list, and I cannot continue to the next step of the process, which is to install beryl, Xgl, and ATI drivers because beryl will not show up on my synaptic package manager.

Does anyone know what is going wrong at my "key file" step of this?  I appreciate any help, as I am new to Ubuntu and would like to run beryl, but also I would like to learn how to work with Ubuntu in general, so any help is greatly appreciated!

---

### Post by wolfen69 on 2008-01-23
is there a reason you want beryl instead of compiz? compiz is installed already if you are using gutsy. enable your video driver in restricted drivers manager. then go to system>preferences>appearance>visual effects.

then, in terminal:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by bwtranch on 2008-01-23
Should be able to get it from add/remove gui, also. Same thing, really.

---

