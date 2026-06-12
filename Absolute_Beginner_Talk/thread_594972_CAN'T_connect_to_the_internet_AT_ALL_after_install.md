---
title: "CAN'T connect to the internet AT ALL after installing gutsy"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-10-28
Hi, I had Ubuntu Feisty on my Dell  Inspiron e1405 for a while, but after my upgrade screwed it up I decided to make a clean install. So, I formatted the partition, without backing up all of my programs, because I couldn't and installed Gutsy. Problem is, I can't connect using ethernet or my bcm43xx wireless card, which isn't enabled. Should I just get Feisty and enable bcm43xx using the sticky how-to in the Networking & wireless section, or is there a way to somehow enable my wireless driver on 7.10. 
P.S. I can download files to my computer using Micro$oft Windows and transfer them to ubuntu. 
T:guitar:HX!

---

### Post by llamakc on 2007-10-28
Have you tried running the Restricted Drivers Manager yet? It's in System | Administration.

---

### Post by mikecomua on 2007-10-28
wait a sec...

---

### Post by mikecomua on 2007-10-28
Here's what it says:[HTML]The spftare source for the package bcm43xx-fwcutteris not enabled[/HTML]

---

### Post by mikecomua on 2007-10-28
bcm43xx-fwcutter

---

### Post by llamakc on 2007-10-28
> **mikecomua said:**
> Here's what it says:[html]The spftare source for the package bcm43xx-fwcutteris not enabled[/html]

Okay. You need to enable it. It's in the Universe repository.

In GNOME, go to SYSTEM | ADMINISTRATION | SOFTWARE SOURCES

Make sure that Community-maintained O/S software (universe) is checkmarked. I'd check the restricted and multiverse ones too.

Close it, open Synaptic and choose Reload.

Try again with the Restricted Drivers Manager.

---

### Post by mikecomua on 2007-10-28
I can't connect to the internet. It won't reload

---

### Post by mikecomua on 2007-10-28
Is there a way to just transfer the file to Ubuntu

---

### Post by llamakc on 2007-10-28
[http://packages.ubuntu.com/gutsy/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/gutsy/utils/bcm43xx-fwcutter)

Yes, you can download and install it from the commandline with "dpkg -i"

```

sudo dpkg -i bcm43xx-fwcutter

```

assuming a) you're in the same directory where bcm43xx-fwcutter IS, and b) you've transferred it to the machine in some manner.

---

### Post by mikecomua on 2007-10-28
OK, thank u very much:guitar:

---

### Post by jinnman on 2007-10-28
I had a similar problem here:
[http://ubuntuforums.org/showthread.php?t=584733](http://ubuntuforums.org/showthread.php?t=584733)
Your answer helped me out.  Thanks.

---

