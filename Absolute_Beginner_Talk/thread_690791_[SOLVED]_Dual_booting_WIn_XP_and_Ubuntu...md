---
title: "[SOLVED] Dual booting WIn XP and Ubuntu.."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by R@inm@n on 2008-02-07
I've read a lot about this already, and tried altering my grub list so that I can dual-boot into either Win XP or Ubuntu.

In the grub menu at the end of the file I typed:


title                  Microsoft Windows
rootnoverify      (hd0,0)
savedefault       
makeactive
chainloader      +1


That didn't work.

So then I tried this:



title                     Microsoft Windows
map                    (hd0) (hd1)
map                    (hd1) (hd0)
rootnoverify         (hd0,0)
makeactive
chainloader          +1



Still didn't work...:(


I have Win XP on one HDD which is set as Master and Ubuntu on the second HDD which is set as slave, both on the same IDE-1 on my motherboard.

What I want to get is the option to boot into either system on start-up.

As it is now, when both HDD's are connected to the motherboard, Ubuntu always boots, but doesn't give me the option to boot into Windows.

I press 'esc' on startup and get the options list, but the closest I have gone to having success is seeing the WIN XP option at the bottom of the list, but when I selected it and hit 'Enter" I just got an unsupported or invalid report...:(


Can anyone give me the proper command for sudo gedit /boot/menu/.lst that I can add to the bottom of the grub list so that I can choose which OS to boot on system start please?


Thanks,



   R.

---

### Post by Forrest Gumpp on 2008-02-07
Have you visited Herman's Illustrated Dual Boot site?  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Herman goes into the GRUB in great detail.  His site is linked to by ubuntu_demon in the sticky thread at the top of the index pages under "Dual Boot Problems", so his advice is obviously highly regarded by forum admin.

---

### Post by Forrest Gumpp on 2008-02-07
Herman's GRUB page within the Illustrated Dual Boot Site gives this link to an Ubuntu Forums thread started by confused57:  [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Posts #1 and #2 look like they may have an answer for you.

---

### Post by R@inm@n on 2008-02-08
YAY !  That thread on dual-booting on two seperate HDD's was just what I needed.

I followed the directions, and it worked.

My mistake was trying to get the dual-boot option with Win Xp on my master HDD.

Once I configured the Win XP drive to slave and the Ubuntu HDD to master, it went fine.

I'm happy that this finally worked...:)

I changed the timeout and the "hidden" menu as well.

Now, if only I could get the ATI drivers to work...  :)



  Thanks mate,


   R.

---

### Post by oedha on 2008-02-08
have you try envy for your ATI

---

### Post by R@inm@n on 2008-02-08
Yes mate, I tried Envy when I installed Mint a couple of days ago. It mucked up my desktop....again ... :(

It really doesn't matter that much right now, as i'm still dual-booting with XP, but when I do go over to Ubuntu permanently, I will need to sort that graphics issue out.

My sons are keen to go over to Ubuntu too, but i'm not going to give them the OK until I get the graphics card thing worked out 100% simply because they are both keen game players....and I would never hear the end of it if they couldn't play ... :)

This is a great learning experience for me. I have such a long way to go, and my memory is shot to bits... so I have to write everything down because I forget.

Nevertheless, i'm enjoying learning this new OS.



    R.

---

### Post by theHUNTER76 on 2008-02-08
Hi guys, is it possible to dualboot WinXP and Ubuntu in the same HDD but in different partitions? Thanks for any help you can provide this newbie Ubuntu fan. :)

---

### Post by oedha on 2008-02-08
> **theHUNTER76 said:**
> Hi guys, is it possible to dualboot WinXP and Ubuntu in the same HDD but in different partitions? Thanks for any help you can provide this newbie Ubuntu fan. :)

It will be nice if you make a new thread..........but i'l like to answer
yes you can...either on different HDD or in the same HDD and of course by using different partition !

---

### Post by R@inm@n on 2008-02-08
> **theHUNTER76 said:**
> Hi guys, is it possible to dualboot WinXP and Ubuntu in the same HDD but in different partitions? Thanks for any help you can provide this newbie Ubuntu fan. :)


Yes it's possible, and easy. It's easier to dual-boot Win XP and Ubuntu on the same HDD I found, initially.

Just use the Live CD.

Also, there are plenty of threads on 'how to' do what you want to do.


  R.

---

