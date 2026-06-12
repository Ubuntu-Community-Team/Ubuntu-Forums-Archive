---
title: "X Server problem"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Mr Clueless on 2007-02-11
Having a while ago been given an Ubuntu 5.10 disc, today I found the time to have a go with it.#

Everything seemed pretty smooth, really - I just pressed "Enter" a lot, created a username and password and tried to understand the prompts.

Problems I had were at 'screen resolutions' where there were no instructions as to how to exclude particular resolutions...my 'maybe 'enter' is the key I want here' wasn't right, I'm sure. Anyway, things rumbled on with no way I could see of rolling back to that point.
Eventually it's reboot time, and all I get is a black screen. Ctrl+Alt+Bkspc gets me a prompt screen but as soon as I let go of the keys it vanishes. I reboot via the main power switch.
I try booting again, I get a message that said something like 'XServer is incorrectly configured..try again when you've put it right', and then I get taken to the login prompt.

So, given that I am Mr. Clueless, how do I fix it? Simple instructions for the hard of understanding, please.

TIA.
Mr. Clueless.

---

### Post by r4ik on 2007-02-11
Log in with you're username and passwrd and do a

sudo dpkg-reconfigure xserver-xorg

follow the defaults and when finished do a 

sudo /etc/init.d/gdm restart

5.10 is rather old better download 6.0.6 from here,

[http://www.ubuntu.com/products/GetUb...irect=download](http://www.ubuntu.com/products/GetUb...irect=download)

and use this guide,

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

If you want to keep 5.10 try,

[http://ubuntuguide.org/wiki/Ubuntu](http://ubuntuguide.org/wiki/Ubuntu)

Good luck !

---

### Post by nickoli_02 on 2007-02-11
If you have an ATI video card, you'll want to install the fglrx driver. Do a search for a howto :)

---

### Post by Mr Clueless on 2007-02-14
Sadly, 6.1, even after several goes with different CDs just won't do anything, it fails to even recognise the CDRom - I get a 'not ATAPI device' error of some kind.
I still couldn't work out how to put checks in the options boxes on the menus when I tried the 'sudo' thing. This Linux thing is supposed to be easy, isn't it?
Strangely, my Win2k disk just works and it installed just fine.

---

### Post by nickoli_02 on 2007-02-14
Sorry, to enable the checkboxes during install/reconfigure of xserver you press the spacebar. Enter takes you to the next prompt. I found that out the hard way too :)

---

