---
title: "Specify OS to reboot into"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-04-23
Is there a way to use the bash shutdown command to boot to a certain partition?? For example, if i wanted to hide My windows partition on the grub loader (by commenting it out), could I create a bash alias to allow me to reboot directly into windows?? I know it sounds like a useless ability to have, but for me it would be great because it would 1: Help me learn more about how my OSes work, and 2: it would allow me to make my copy of windows bootable ONLY if you have administrator priveleges on Linux... which means that only I could do it. Thanks for the help!!

---

### Post by oilchangeguy on 2007-04-23
wouldn't it be simpler just to put a password on windows, so nobody but you can access it?

---

### Post by brennydoogles on 2007-04-23
> **oilchangeguy said:**
> wouldn't it be simpler just to put a password on windows, so nobody but you can access it?

lol Yes it would, but that would not satisfy goal Number 1!! Actually, I have nothing worth password protecting on windows, the main thing is just learning more about the OS, and also being able to have my computer boot quickly in my non-default OS without me having to press any buttons. I really want to eventually have the computer boot into Ubuntu immediately upon GRUB loading, and to be able to bypass GRUB (or at least my personal interaction with it) the few times I want to boot windows. If I set my timeout low enough to boot immediately into Ubuntu, I end up losing the ability to boot into windows. What i proposed would allow me to Alias a windows reboot into my bash RC so that I can just type "windows" into terminal and go get a drink if i want to. Does that make any sense??

---

### Post by LaurelLynn on 2007-04-24
Dear brennydoogles,

Neither the shutdown or reboot commands have options for this.  The problem is that the os gets completely shutdown with nothing left running.  So, anything that would work at that point would involve the bootloader GRUB.

Now GRUB determines the default partition from the entries in the file  /boot/grub/menu.lst.  What you could do (if your very careful) is run a shell script on shutdown, that edits this file to change the default boot os. That is not so hard to do on the Linux side.  Just make a backup copy so you can restore it with the Ubunt Live CD (assuming you have one).

To get Ubuntu to boot again though, windows would have to edit the file too on its shutdown. That would require tracking down 3rd party drivers to alow windows to read an Ext3 partition (they do exist, and work, I just don´t remember the name).

Either way, proceed with caution and leave a sizable menu delay in place until your sure it works at both ends.

Good Luck!

---

### Post by brennydoogles on 2007-04-24
> **LaurelLynn said:**
> Dear brennydoogles,

Neither the shutdown or reboot commands have options for this.  The problem is that the os gets completely shutdown with nothing left running.  So, anything that would work at that point would involve the bootloader GRUB.

Now GRUB determines the default partition from the entries in the file  /boot/grub/menu.lst.  What you could do (if your very careful) is run a shell script on shutdown, that edits this file to change the default boot os. That is not so hard to do on the Linux side.  Just make a backup copy so you can restore it with the Ubunt Live CD (assuming you have one).

To get Ubuntu to boot again though, windows would have to edit the file too on its shutdown. That would require tracking down 3rd party drivers to alow windows to read an Ext3 partition (they do exist, and work, I just don´t remember the name).

Either way, proceed with caution and leave a sizable menu delay in place until your sure it works at both ends.

Good Luck!

meh... I don't think it's worth all of that to me lol. I just thought it would be cool to be able to reboot into windows with a simple command. But I'm not above hitting the down arrow and enter key in GRUB. Thanks anyway!!

---

### Post by Drakkor on 2007-04-27
> Now GRUB determines the default partition from the entries in the file /boot/grub/menu.lst.
Ok, I'm going to install Fiesty on a freind's computer, but he wants Windows to boot by default. How would I edit the boot/grub/menu.lst ? Thanks :)

---

### Post by confused57 on 2007-04-27
> **Drakkor said:**
> Ok, I'm going to install Fiesty on a freind's computer, but he wants Windows to boot by default. How would I edit the boot/grub/menu.lst ? Thanks :)

See this guide:
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

I personally place the Window's entry above the ###BEGIN AUTOMAGIC.... section.

---

### Post by crav on 2007-04-27
Open a terminal. Type
```
gksudo gedit /boot/grub/menu.lst
``` to edit the menu.
Change
```
default     0
``` To whatever number Windows is.

---

### Post by Drakkor on 2007-04-28
Thanks ,peeps, did the default   4 and it worked like a charm ! :)

---

### Post by Nythain on 2007-04-28
> **brennydoogles said:**
> meh... I don't think it's worth all of that to me lol. I just thought it would be cool to be able to reboot into windows with a simple command. But I'm not above hitting the down arrow and enter key in GRUB. Thanks anyway!!
but wouldnt that satisfy goal number one :)

---

### Post by brennydoogles on 2007-04-29
> **Nythain said:**
> but wouldnt that satisfy goal number one :)

lol, I guess it would, but considering that my motherboard recently fried (moving across town on a rainy day + my computer somehow ending up in the garage (moving help from a 9 year old) = toasted compy :mad: ) I will have to wait until i can build a new one before i can learn more by experience!!

---

