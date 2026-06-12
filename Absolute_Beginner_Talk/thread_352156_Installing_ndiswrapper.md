---
title: "Installing ndiswrapper"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Citan on 2007-02-02
I want to use ndiswrapper to get my Broadcom wireless card to work, but I'm pretty new to Linux. As such, I don't know how to install ndiswrapper and could use some help. I looked at the official ndiswrapper installation guide, but it requires a degree of knowledge about Linux that I just don't have yet. Could someone walk me through the setup of ndiswrapper?

---

### Post by dpar on 2007-02-02
ndiswrapper is in synaptic package manager, you can install it that way.

---

### Post by K.Mandla on 2007-02-02
It's on your installation and/or live CD as ndiswrapper-utils, I believe. So you don't even have to be connected to the Internet to install it. ;)

---

### Post by aysiu on 2007-02-02
In a terminal, type these commands: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

### Post by .plaid on 2007-02-03
So, a bit of theory if you please.

I just got a (replacement?) copy of ndiswrapper-utils from Synaptic, then couldn't find it so I went to get it again. Synaptic offered me the option to Reinstall....

I am used to downloading apps then installing them...

**Does Synaptic (and by extension, Add/Remove, APT, et al.) download AND install software for me?** This would certainly explain why it's so dag-gum hard to find anything.

Inquisitively,
.

---

### Post by Citan on 2007-02-03
Alright, I've got it installed, and I'm almost done installing the drivers. However, I keep getting this error message after running *ndiswrapper -i bcmwl5.inf*:

"couldn't copy bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144."

According the the ndiswrapper guide, that usually means that I mispelled something, but I've checked and everything is spelled fine...:confused:

---

### Post by alwiap on 2007-02-03
dude, I just configured my Broadcom card a matter of hours ago, I used the search function in the forums for Broadcom ([http://ubuntuforums.org/search.php?searchid=13875095](http://ubuntuforums.org/search.php?searchid=13875095))

and there are a bunch of tutorials of how to do it, I forgot which one I picked but I just followed every letter and it worked great.

gl

---

