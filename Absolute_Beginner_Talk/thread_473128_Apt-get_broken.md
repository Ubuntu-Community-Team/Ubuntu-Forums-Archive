---
title: "Apt-get broken"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by herrma29 on 2007-06-13
I have been trying out various desktop environments recently, trying to see if there was one I liked more than gnome (there isn't) so I found a couple links in the forum to info on how to remove kde and xfce from my installation and restore my gnome desktop. Previously to all of this, I installed pidgin and removed gaim. Now, I am running into some problems with any software installer on my computer. Apt-get is giving me the following:

```
dpkg: error processing /var/cache/apt/archives/gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/share/dbus-1/services/gaim.service', which is also in package pidgin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried doing sudo apt-get install -f, but it gives me the same thing. I tired removing pidgin, didn't work. I tried installing gaim, didn't work. If anyone has any clue as to what I should do to remedy this situation, I would really appreciate it.

Thanks,
Chris

---

### Post by herrma29 on 2007-06-13
Problem solved! I followed these few steps that I found after doing some searching of my own. Thanks to anyone who might have looked into this for me.


Code:

deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty main

Then, to get his or her key, run:
Code:

wget [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg) -O- | sudo apt-key add -

Then update:
Code:

sudo aptitude update

---

