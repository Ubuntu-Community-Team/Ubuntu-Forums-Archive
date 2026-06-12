---
title: "Dual Boot... Where the heck is Windows Vista?? [Solved]"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by aSpork on 2007-09-21
**PROBLEM SOLVED**
It turns out I just had to boot it for the third time... Now I can do my homework for mysql class and oracle. x_X Whew.


So... I installed ubuntu on a partition... Yay.

But I want to go back to Windows Vista. >_<

I'm following this guide: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

I'm at the part where it's like this:
"There are loads of options you can change, but only a couple that you&#8217;re likely to be interested in. The default boot entry is defined by the &#8220;default&#8221; value.

The default value is 0, which means that the first entry in the list (which is Ubuntu) always gets loaded.

If you want to make it so that Windows Vista loads by default, change the value to 4, as Vista is the fifth item in the list (the numbering system starts at 0 and "Other operating systems" counts as a line)..."

Default value? What? :confused:

Edit: I'm not asking just about the default value. I can't start up Windows Vista from the menu itself. It gives me a blue screen and restarts.

---

### Post by alienexplorers on 2007-09-21
Please list your menu.lst file

> cat /boot/grub/menu.lst

Then paste the results back here.

---

### Post by Wiebelhaus on 2007-09-21
who the hell cares?











sorry couldn't resist cracking a joke , yea , what's your grub list look like?

---

### Post by eph1973 on 2007-09-21
This means that if you leave it alone (i.e. don't change the default value), if you don't interfere (make a choice on the GRUB menu other than the default value), you will boot into that OS after the countdown is complete.  So for example:
Let's say your GRUB menu looks something like this:

```
Ubuntu 2.6.20-16 blah blah blah            position 0
Ubuntu 2.6.20-16 (recovery mode)           position 1
memTest x86                                position 2
Other Operatings Systems:                  position 3
Windows Vista                              position 4
```The positions aren't on the GRUB menu, obviously.  I am just trying to show you what they are talking about.

So if you don't change the default value they are referring to, you will load Ubuntu after the 10 seconds that GRUB waits for you to change the choice is up.  Otherwise, you just go ahead and select Windows Vista, or whatever, and that OS will boot up.

Ultimately, if you are worried about figuring out where the "default value" you need to change is, you can just leave it alone, and just make sure you choose Windows Vista manually from the GRUB menu when you need to boot into Vista.  You could always change it later by editing the file /boot/grub/menu.lst

---

### Post by Joeb454 on 2007-09-21
Did you make sure you had free space available for Ubuntu (i.e. unformatted hard drive space) before you installed, like the guide said?

Because if you then install and choose "Guided - Use Continuous Free Space" or whatever it is, it *should* recognise the Vista partition...I know my install did.

*EDIT*

Woops! Misread the question, my bad!

Follow what other people said - edit grub, there's a guide to doing it on that link as well though, you just need to figure out how to edit it :)

---

### Post by aSpork on 2007-09-22
> **eph1973 said:**
> This means that if you leave it alone (i.e. don't change the default value), if you don't interfere (make a choice on the GRUB menu other than the default value), you will boot into that OS after the countdown is complete.  So for example:
Let's say your GRUB menu looks something like this:

```
Ubuntu 2.6.20-16 blah blah blah            position 0
Ubuntu 2.6.20-16 (recovery mode)           position 1
memTest x86                                position 2
Other Operatings Systems:                  position 3
Windows Vista                              position 4
```The positions aren't on the GRUB menu, obviously.  I am just trying to show you what they are talking about.

So if you don't change the default value they are referring to, you will load Ubuntu after the 10 seconds that GRUB waits for you to change the choice is up.  Otherwise, you just go ahead and select Windows Vista, or whatever, and that OS will boot up.

Ultimately, if you are worried about figuring out where the "default value" you need to change is, you can just leave it alone, and just make sure you choose Windows Vista manually from the GRUB menu when you need to boot into Vista.  You could always change it later by editing the file /boot/grub/menu.lst

That's it?

When I boot that menu thing, and I select Windows Vista, it gives me a blue screen and restarts. Should I try again or am I doing something wrong?

---

### Post by Tyke91 on 2007-09-22
use your vista cd and run the windows command

CHKDSK

this will solve your boot problems with vista

---

### Post by aSpork on 2007-09-22
> **Tyke91 said:**
> use your vista cd and run the windows command

CHKDSK

this will solve your boot problems with vista

I don't have the CD at the moment but I'll be sure to find it.

However, the first time I booted it up, I think it was doing something like that, but the second time it gave me a blue screen, and I'm afraid of trying it again. :(

---

### Post by eph1973 on 2007-09-22
If the chkdsk thing doesn't work out, perhaps you want to try to use the Vista Bootloader to boot up.  Just pointing out this little excerpt from the apcmag website:

> If instead of GRUB you want Vista's bootloader to be in charge, load up the Vista installation and install EasyBCD. Go to “Manage Bootloader”, then “Reinstall the Vista Bootloader”, an GRUB is overwritten. You can then configure the Vista bootloader to add Linux to the boot menu.Might be worth a shot.

---

### Post by aSpork on 2007-09-22
Problem Solved. All is well. :D

---

