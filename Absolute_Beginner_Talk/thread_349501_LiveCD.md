---
title: "LiveCD"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Jun0 on 2007-01-30
Hi there,
As I post days ago,
My liveCd cannot work properly due to
(frequency out of range or something like that). 
Now my Grub seems to corrupt in MBR.
How can I enter rescure mode??
via my DVD(ubuntu v6.10)

---

### Post by an.echte.trilingue on 2007-01-30
I think that the person who answered you on the other thread misunderstood your problem.

You screen problem is probably caused by a missing graphics card driver.  Tell me what your card is and I will tell you how to install it.

Now, as for fixing grub, the easiest thing to do is going to be to reinstall.

What is the output that tells you the MBR is corrupted anyway?

Take care
-mat

---

### Post by jvc26 on 2007-01-30
The frequency issue is probably a gfx card issue- what is your gfx card? The livecd issue is possibly solvable, if not you may want to use the alternate installer cd - available from the site, doesnt use a GUI rather using  text based interface which allows you to install.
Il

---

### Post by Jun0 on 2007-01-30
> **an.echte.trilingue said:**
> I think that the person who answered you on the other thread misunderstood your problem.

You screen problem is probably caused by a missing graphics card driver.  Tell me what your card is and I will tell you how to install it.

sis6326

i read someone said that relating to xorg.conf
( HorizSync and VertSync values)

duno just what's going on
> **an.echte.trilingue said:**
> 
Now, as for fixing grub, the easiest thing to do is going to be to reinstall.

oh...
god
it really take time.....!!!
> **an.echte.trilingue said:**
> 
What is the output that tells you the MBR is corrupted anyway?

i un-hide a XP partition.
then i cannot enter ANY os FOREVER.
(i have 3 OS in my PC)
i guess this action made MBR lost
> **an.echte.trilingue said:**
> 
Take care

:--]

---

### Post by an.echte.trilingue on 2007-01-30
> **Jun0 said:**
> sis6326
Well, some good news and some bad news:
Good news, you don't have to install any drivers.
Bad news, SiS cards have horrible linux support.  You will not have 3d rendering.
To fix the card, use the alternate CD to install, then boot into the command line prompt, and type ```
sudo dpkg-reconfigure xserver-xorg
```This will launch a wizard of sorts to help you configure your display.  You will need to know your screen resolution.  Then reboot and see if it works.  You might have to try a few times before you find what works.

You might not need to reinstall.  With the alternate CD you can TRY:
```
sudo grub --install-partition=<your_ubuntu_partition>
```
but I am not really sure if this will help you.

Probably won't make your situation any worse, though.  Try at your own risk.

Take care
-mat

---

