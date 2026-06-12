---
title: "XP &amp; Ubuntu dual boot, XP not found."
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Frak on 2006-11-15
Hello, I installed Ubuntu on my desktop (ran XP) and I had to keep XP (first time) so I installed Ubuntu on a slave drive that I installed myself.  Seems to be when it boots up that it says the usual "press esc. to enter menu 2.. 1.." but XP is not listed, I have no idea whats going on, so I *really* need some help, I kept XP this time for work related reasons (I have no say in the matter)
                                    :confused: 

Thanks!

---

### Post by ReaderRat on 2006-11-15
When you installed Ubuntu to the slave drive, it put its bootloader on that disc. Win XP bootloader for Win XP installed on the master drive. That's probably why it's not listed. If you have the option in the BIOS to boot from either drive, change drives (in the BIOS) and see if Win boots.

---

### Post by Frak on 2006-11-15
Thanks for the analysis but do you know a way that I can get it back, to dual boot
Thanks!

---

### Post by Gaweph on 2006-11-15
> **ReaderRat said:**
> When you installed Ubuntu to the slave drive, it put its bootloader on that disc. Win XP bootloader for Win XP installed on the master drive. That's probably why it's not listed. If you have the option in the BIOS to boot from either drive, change drives (in the BIOS) and see if Win boots.

This is incorrect, he says that he see's GRUB, but doesnt see XP on the grub list.  This means that grub must be installed on the master drive in order for it to be booted at startup (if grub was on the slave, windows would simply be booting up)

Anyway, there is a simple solution to your problem:

*SImply add the windows xp entry to you Grub list 

==Instructions==

*load up ubuntu, go to console, and do the following:

sudo gedit /boot/grub/grub.conf

add the folowing:

title Windows XP Professional
        rootnoverify (hd0,0)
        chainloader +1

this means hd0 partition0 (hd0,0), change these to your values.

You will also see something like this:

default=0 

0 being the first option, then 1 then 2, set this to whatever one you want to be highlited when grub loads.

Hope this helps

---

### Post by Frak on 2006-11-15
OMG, this is the second thing that you have solved *perfectly* I worship you.

---

### Post by Gaweph on 2006-11-15
Not A problem.

I thaught i had noticed the name.  You are the guy who needed help with your NIC.

No troubles, i knew the solution, and i realised that the other person had mis-read your query.

I am on a roll today, but you are now on your own, as i must get up in 6 hours, so have to hit the hay.

GoodLuck (with the rest of your hickups tonight - hehe)

---

### Post by Frak on 2006-11-15
OK update that...
1. did not work, and
2. I can't login to Ubuntu anymore

---

### Post by Gaweph on 2006-11-16
what do you mean, pleease elabrate:

*Did XP not appear on the grub list?
*if you select Ubuntu, it doesnt load?

Please post a copy of your grub.conf for me to take a look at.

---

### Post by bollix47 on 2006-11-16
Out of curiosity why /boot/grub/grub.conf?  I don't have that file on my system.  Grub uses /boot/grub/menu.lst.

---

### Post by Frak on 2006-11-16
> **Gaweph said:**
> what do you mean, pleease elabrate:

*Did XP not appear on the grub list?
*if you select Ubuntu, it doesnt load?

Please post a copy of your grub.conf for me to take a look at.
1. XP does not appear on GRUB list.
2. When I log in it stays at browns creen.
3. I was posting this on the desktop until the Wireless Connection was diconnected by Network manager and no networks are found anymore.

---

### Post by Frak on 2006-11-16
> **Frak said:**
> 1. XP does not appear on GRUB list.
2. When I log in it stays at browns creen.
3. I was posting this on the desktop until the Wireless Connection was diconnected by Network manager and no networks are found anymore.
I guess Ubuntu is not for my computer, I'll take out the slave drive, erase it, and put it back in so I can have more space with Windows$, thanks for trying...

---

### Post by Gaweph on 2006-11-16
Dont give up. i have had my number of mishaps too.

Ok, so this is your situation as i see it:

*HD1 - ubuntu, grub - master

*HD2 - Windows (if set to master will just boot into windows)

Is this correct?

---

### Post by gn2 on 2006-11-16
Dual boot on two drives: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Gaweph on 2006-11-16
ok try this, i forgot to add the 2 middle lines:

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

also yes the file is: menu.lst and not grub.conf

It should work fine.

---

### Post by jimbob on 2006-11-16
If Ubuntu is on your master it will be referred to as hd0 in grub and the slave will be hd1 providing the bios is set that way.

Since the OS's are on separate drives you must add the following after the makeactive line in the XP entry in menu.lst (it is not grub.conf it is menu.lst):  

      map (hd0) (hd1)
      map (hd1) (hd0)

Here is my entry:

   title           Windows XP (piece of crap on HDA1)
root            (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
boot

(Apologize for the sarcasm)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Frak on 2006-11-16
> **Gaweph said:**
> Dont give up. i have had my number of mishaps too.

Ok, so this is your situation as i see it:

*HD1 - ubuntu, grub - master

*HD2 - Windows (if set to master will just boot into windows)

Is this correct?
close just switch them around

and thanks for helping! I was going to quit from pure failure, but you guys keep me fighting. (I read that somewhere)

---

