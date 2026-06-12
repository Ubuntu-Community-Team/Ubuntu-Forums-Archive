---
title: "Attaining description of modules"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by marx2k on 2006-12-14
Let's say I want to trim down the list of modules that are in use (for instance, bluetooth module when my comp has no bluetooth connectivity) - I want to do a few things (I will center around the bluetooth module here as an example):

1. I would like to get a description of the module in use.  For instance, where do I get a description of the 'bluetooth' module?

2. I see that there are 2 other modules using bluetooth:

```

Module                  Size     Used by
bluetooth              53476  2 rfcomm,l2cap

```

How do I find out what THOSE modules are, why they are using bluetooth module and how to get them to stop since I am unable to remove the bluetooth module until it is no longer in use by those 2 modules.
```

$ modprobe -r bluetooth
FATAL: Module bluetooth is in use.

```

3. If this is the situation I am in, will blacklisting bluetooth give me problems on startup if those 2 other modules depend on it? I went through synaptic and removed everything that had bluetooth in the description so at this point there should be nothing using that module, I would imagine?

---

### Post by frootstripe on 2006-12-14
I'm bumping this question because I too would like an answer to it.

---

### Post by frootstripe on 2006-12-14
can't anybody answer this?? I have bluetooth services running  - l2cap I can't disable with `modprobe -r l2cap', get the msg:

FATAL: Module l2cap is in use.

I've never had any bluetooth devices, btw.

---

### Post by Ocxic on 2006-12-14
this is a good question....

---

### Post by wolfmanjm on 2006-12-17
Hi, I was looking for the answer, I think I found it.

edit the file /etc/default/bluetooth

and set 

BLUETOOTH_ENABLED=0

This seems to work on Edgy.

---

### Post by Ocxic on 2006-12-18
just remove all of the bluetooth-utils and other bluetooth programs in synaptic (there are only about 3 of them, and they may not all be installed) and reboot, this worked for me..
these are what i removed in synaptic

bluez-cups
bluez-pin
bluez-utils

---

### Post by marx2k on 2006-12-18
> **Ocxic said:**
> just remove all of the bluetooth-utils and other bluetooth programs in synaptic (there are only about 3 of them, and they may not all be installed) and reboot, this worked for me..
these are what i removed in synaptic

bluez-cups
bluez-pin
bluez-utils

Yep that's what I did too, but that doesn't answer the second part of the question as to how to find out the descriptions, uses and dependencies of and on modules.

Also, you might want to install and check out the program 'modconf' - Pretty useful as far as removing and inserting modules

DESCRIPTION
       modconf  is  a script for installing kernel modules on Linux. It can be
       used interactively (GUI mode) or from the command-line (batch mode).

---

### Post by frootstripe on 2006-12-24
>  Originally Posted by Ocxic  View Post
just remove all of the bluetooth-utils and other bluetooth programs in synaptic (there are only about 3 of them, and they may not all be installed) and reboot, this worked for me..
these are what i removed in synaptic

bluez-cups
bluez-pin
bluez-utils

Okay, I did the above but I still get the following: 

$ lsmod | grep 'l2'

l2cap                      25156  2
bluetooth              48580  3 l2cap

---

### Post by bodhi.zazen on 2006-12-24
See if this helps:

[http://www.cyberciti.biz/tips/how-to-display-or-show-information-about-a-linux-kernel-module-or-drivers.html](http://www.cyberciti.biz/tips/how-to-display-or-show-information-about-a-linux-kernel-module-or-drivers.html)

---

