---
title: "Suspend-To-Ram on PowerBook 12&quot; 1.5Gh ?"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by snowdrop on 2006-07-24
I searched the forum for an answer to my question, but without success. So here is my problem for which I spent 2 nights to resolve, again without success:

MacOSX have a perfect Sleep function. I think this should be possible with ubuntus suspend-to-ram. But when I try to suspend the honey notebook dmesg says: sleep not supported on this machine.

1. Is it possible with ubuntu? (Kernel-patchs apt-gets etc.)
2. If yes, how?

Thanks for your answers

---

### Post by APU on 2006-07-24
I did not yet try this myself but I have already done some research in this field since I want to switch my PowerBook 12" (1,5 GHz) to Ubuntu within the next couple of weeks.

It seems that the reason that suspend to RAM is not supported is that there is no documentation from Apple or NVIDIA available that would allow to wake the graphics chip after a suspend which means that tere is no way to get screen output. (And what is equally bad at least - threre is no option for using the 3D acceleration at this moment)

It seems that suspend to disk will work though since the machine is completely powered off in that case and the Open Firmware will initialize the graphics chip when you turn on the PowerBook just like it would during a normal boot.

I don´t have any links available but you could search the Web for "PowerBook6,8 Linux Suspend" to find this information and probably much more details.

APU

---

### Post by snowdrop on 2006-07-25
I installed ubuntu with success. All the components I need works perfectly. I build my own vanilla kernel. The only significant problem for me to not use ubuntu is the leak of suspend. Even suspend-to-disk is not working for me. I searched in google for hours (for nights). 

I found out that you must use pbbuttonsd to sleep. but 

# pbbcmd sleep 

does nothing. 

# echo -n mem > /sys/power/state

is not working, too

# echo -n disk > /sys/power/state

do a suspend-to-disk if you give the resume= kernel parameter. But on wake up the system is booting normally from scratch.

Does anybody have an idea?

---

### Post by APU on 2006-07-25
Look at this page: [http://www.ncc.up.pt/~rvr/kh/kh.html](http://www.ncc.up.pt/~rvr/kh/kh.html)

Suspend to Disk seems to work somehow.. but if it is not it would definitely be a showstopper for my plans to put Ubuntu on my PowerBook

---

### Post by snowdrop on 2006-07-26
hi,
the above given link is broken. Can you check the url ?
Thanks

---

### Post by APU on 2006-07-26
It does work for me by either clicking directly on it as well as by using copy and paste. Please try again, it is correct!

APU

---

### Post by snowdrop on 2006-07-28
sorry for the late answer. I know the page. But I read that pmud should not used together with pbbuttonsd. If you try to apt pmud, some important packages will be removed. 
But I will try pmud at least to find out, if suspend-to-disk is working with ubuntu.

---

### Post by APU on 2006-07-28
Please tell if you have been successfull then!

I even found something more abot ppbuttonsd and pmud. It could be necessary that you have to recompile ppbuttonsd and include pmud support into it to make them work together. Look at: [http://pbbuttons.sourceforge.net/projects/pbbuttonsd/doc.html](http://pbbuttons.sourceforge.net/projects/pbbuttonsd/doc.html) for details

APU

---

### Post by APU on 2006-07-28
I found even more Info:

Look at [http://pbbuttons.sourceforge.net/projects/pbbuttonsd/changelog.html](http://pbbuttons.sourceforge.net/projects/pbbuttonsd/changelog.html) and there at the changelog from 2005-09-04

Maybe simply issuing pbbcmd HIBERNATE does the trick ;-)

APU

---

### Post by snowdrop on 2006-08-01
pbbcmd hibernate does nothing for me. Have you successfully hibernate your powerbook?

---

### Post by APU on 2006-08-01
Not yet but it´s on the Agenda

I already installed Ubuntu on the Powerbook and am now working through all things to get my "ideal" setup. The Trackpad was a bit hard, now comes WLAN (including WPA) and then I will try to hibernate the thing... I will tell you when I have been successful!

APU

---

