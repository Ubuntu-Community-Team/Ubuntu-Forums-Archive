---
title: "Booting trouble"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by penguin steve on 2007-03-08
Hey everyone, im new to linux and i downloaded a ISO of the Ubuntu linux 6.10 and burned it to cd using Nero 7 with the ISO burning tool. just before you start making assumptions, i will say i am NOT a newbie to computers (at least with Win XP) and ive been doing all sorts of things with computers for a long time. so just to try this linux out,(i didnt realize you dont have to install it to test it at the time) i downloaded virtualbox to try it out without actually installing it on the hard drive so i take no chances screwing something up. I installed it on a virtual hard drive no problem. ok so to my problem now. i ran Ubuntu in the virtual computer fine and everything but then when i burned it on a cd and tried to boot it for real, i have problems.

it comes to the home ubuntu screen and i select
"Start or install Ubuntu"

then a window pops up saying
"Starting..... loading linux kernel"

then it brings me to the ubuntu loading screen with the orange bar going side to side.

then it stops and it says exactly this:

> 
BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu) Built in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh : can't access tty ; job control turned off
(initramfs)_

i dont know what to do so i just reset and i tried different settings. still dont work. do you know what i can do to fix it?

my burner is not the problem as i just burned 3 DVD movies with nero 7 onto 3 DVD-Rs and they work fine. ive also burned other ISOs before with nero and ultraISO and they also worked. its the first bootable discs i make. so maybe its having trouble making the boot files burned properly?

also, if there cant be an error in the ISO because it did run on my virtual computer.

Thanks for all your help!

---

### Post by daou on 2007-03-08
It could be a lot of issues. But whenever you have trouble installing Ubuntu on new hardware, do this:

1. google [or search Ubuntu forums for] the exact output right before it hangs.
2. Then google your hardware to see if there are problems with it and Ubuntu, or Linux in general. Check the components in this order:
-- motherboard.
-- NICs, wireless, etc... stuff related to networking
-- graphics card
-- CPU (very unlikely)
-- hard drives (unlikely, unless its a problem with the hard drive controller of the motherboard like JMicron controllers on Asus P5B mbs.)
-- any other "special" (read: uncritical) hardware that you are running. If you are comfortable with playing around with your hardware, try disconnecting uncritical components and installing. 

If all this fails, then the next best thing is to try a newer version of Ubuntu (Feisty) or a different distro.

---

### Post by daou on 2007-03-08
In addition, its most likely that the problem is with hardware. First, it *usually* is. Second, installing Ubuntu in a virtual machine inside Windows works as long as Windows is working on the machine. This is because Ubuntu doesn't see your hardware in a VM. Your VM gives virtual hardware to the Ubuntu VM process. The VM knows how to interface with the hardware because it's able to use the manufacturer's hardware drivers installed in Windows.

---

### Post by fakie_flip on 2007-03-10
My younger brother is having the same error with Ubuntu Edgy Eft 6.10 on his computer. It was working fine since it was installed about a month ago until this morning. He says he added an 80 gb hard drive to his computer, but I don't see how that could cause the problem.

---

### Post by penguin steve on 2007-03-10
ya i did a search and i cant seem to find someone with the same problem as me simply from trying to boot the live CD. i have this problem and its not installed on my hard drive. so as people were saying, just pointing grub to boot from the right partition drive, does not apply to me as im just trying to boot from the CD and ubuntu is not installed yet. fake flip your problem is that grub is trying to boot from the new 80 gig hard drive so you need to go in grub and point it to the original partition drive it was installed on.

thanks for your help guys but i need a different solution.

---

### Post by halitech on 2007-03-10
when you burned the cd, di dyou burn them at high speed or the lowest speed possible?

---

### Post by penguin steve on 2007-03-10
i burned at 40x

---

### Post by rusty4r on 2007-03-10
Most recommend burning a livecd at 4x

---

### Post by penguin steve on 2007-03-10
ok that might explain it. i will try it and tell you how it goes

---

### Post by rusty4r on 2007-03-10
Did you check your downloaded iso's md5sum and then after burning at 4x when the Ubuntu screen shows up select "check cd for defects" then you'll know that your download is good and your cd is good.

Check out this page
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

---

### Post by penguin steve on 2007-03-10
i know my download is good because it worked in virtual box perfectly so its either just me of my CD

---

### Post by penguin steve on 2007-03-11
hello, this time i did "check cd for defects" with the livecd i burned at 40x (didnt burn another one yet)

it brought me back to the exact same screen as the original one in my first post.

when i hit Ctrl + Alt + F1, this screen pops up

> 
cp: Unable to open 'root/var/log' : no such file or directory
mount : Mounting /root/dev/.static/dev failed : no such file or directory
mount : Mounting /sys on/root/sys failed : no such file or directory
mount : Mounting /proc on/root/proc failed : no such file or directory
Target filesystem doesn't have /sbin/init
_


i will burn another CD at 4x and see what happens

---

### Post by penguin steve on 2007-03-11
thanks sooo much for that link rusty4r. i learned a lot. i did the md5sum and it didn't find any errors.

---

### Post by penguin steve on 2007-03-16
this is really really weird. first off, i burned another liveCD at 16x (the lowest speed possible) and it still does not work on my computer:confused: . BUT, just out of curiosity, i stuck in the CD i burned at 48x (the cds are rated at 52x) into my old computer, and sure enough it works perfectly!:)  why doesn't it work on my new computer? :mad: they are both from the same company and both custom built. the only thing i had to do was change the boot priority in the BIOS settings so that the cd boots before the HDD and away it goes! (i already did this on the new comp)

by the way this post was written from Ubuntu linux on the live CD on my old computer.

thanks for your help!

---

### Post by korren10284 on 2007-03-16
OK, not a total n00b to computers in general, but a n00b to Linux.  Yes, i to am having troubles loading booting/loading ubuntu 6.10 (i think it its, w/e the latest non alpha/beta version is).  I downloaded iso, burned iso, i can boot the live cd and run it.  I can supposedly install on my harddrive.  I canNOT turn off my comp from the shutdown function off of the cd and when i try to boot from the harddrive it just hangs on a blank black screen with just a blinking "_" cursor.  If i press a button the cursor goes away, but still hangs.  I will do the other tests soon, but i have to leave in 1 min.

---

### Post by fakie_flip on 2007-03-17
> **korren10284 said:**
> OK, not a total n00b to computers in general, but a n00b to Linux.  Yes, i to am having troubles loading booting/loading ubuntu 6.10 (i think it its, w/e the latest non alpha/beta version is).  I downloaded iso, burned iso, i can boot the live cd and run it.  I can supposedly install on my harddrive.  I canNOT turn off my comp from the shutdown function off of the cd and when i try to boot from the harddrive it just hangs on a blank black screen with just a blinking "_" cursor.  If i press a button the cursor goes away, but still hangs.  I will do the other tests soon, but i have to leave in 1 min.

which version of Ubuntu were you trying? if it was Feisty 7.04, that would explain why it is not working because feisty is beta still in development with bugs. I suggest that you try another version such as 6.06 if you are using 6.10 or 6.10 if you are using 6.06. you could also try installing from the alternate iso instead of the desktop iso. i once had a problem. the 64 bit version of ubuntu would not install on my computer, and i got the errors in the picture. i had to install the 32 bit version instead and that worked, but i would still like to get the 64 bit version working.

---

### Post by korren10284 on 2007-03-17
I am running Ubuntu 6.10, and when booting i get your first screenshot with the 2 [OK]'s on the right and stuffs about mounting on the left.  when that screen changes, that is where the blinking cursor comes into play.

---

### Post by penguin steve on 2007-03-17
anyone have an idea why ubuntu works on my old computer and not my new one?

i really want this to work. thanks

---

