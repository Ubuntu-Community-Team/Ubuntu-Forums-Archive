---
title: "I broke GRUB, Ubuntu, and XP"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by thedrizz on 2007-10-29
So while in the process of installing compiz (which is obcenely complicated, by the way), i somehow screwed up ubuntu. When i tried booting, it asked me to enter my username and password in the BIOS. Which would be fine, but the screen turns black after like 10 seconds. So instead of doing the smart thing and come to the forum, i decided to take matters into my own hands.

I booted off the desktop disk, and, since i had been using ubuntu for like 3 hours, figured i could just install over it. However, this was easier said than done. I couldent figure the bloody thing out. So i decided to delete my partition and install again. However, the installer still just gave me the option to resize the now-deleted partition, and use the free space. I figured i would just do that and delete the new tiny partition later using a XP program i had lying around. 

Well i did such, and upon reboot i got a grub error 17. Well poop, i forgot to uncheck install grub. Well i boot up the disk again and try to delete one or both of the linux boots, no luck. So now i just really wanna fix grub and get ubuntu working again on my bloody computer. My current plan is to somehow get on XP and use this partition manager to merge all the stray partitions back together and just do another resize of the main drive. However, i need to fix grub first

According to a quick google, i need my XP install cd. Well i lost the bloody thing years ago. Is there an alternative i could use to fix GRUB, if so would it delete any data other than the stuff i wanna delete? And does my ill  conceived plan to get ubuntu back up have any possibility of success?

THANK YOU! (in advance)

---

### Post by kingpoiuy on 2007-10-29
When you boot from the Ubuntu CD and click install does it give you an option to configure your partition manually?

If it does you can delete all your linux ones (not your windows one!) and remake a single linux partition.  

Beware that you have to install linux after windows.  If you find your disk for windows later you cant install windows after you install linux because it will take over the MBR and grub will be gone. 

Also you can boot into the Ubuntu live CD and fix grub with the "grub" command.
```
grub
```
```
find /vmlinuz
```
that will give you your drive info.  use that info here:
```
root (hd0,1)
```
```
setup (hd0)
```

anyway that was a quick tutorial let me know if you have any problems!

---

### Post by thedrizz on 2007-10-29
i will try that when i get home.

But i remember under manual when i tried to delete it and hit next, it said something along the lines of "not in the root". If i set it to / instad of /(whatever it is now), will that make it work?

Edit: Oh and your a fellow michigander.

Hi-five!

---

### Post by kingpoiuy on 2007-10-29
Ooo, a Michigander, Yay! "high five" :)

Yes,  I believe it is suppose to be root. "/"

That would be the "mount point"

Ubuntu does not seem to create seperate partitions for "/home" just "/" and "swap"

---

### Post by thedrizz on 2007-10-29
er i get a file not found error when i type in find /vmlinuz in the grub terminal

---

### Post by kingpoiuy on 2007-10-30
I have noticed this problem.  For some reason sometimes grub will work on the boot disk and sometimes it wont.  I have no idea why.  I just kept trying it until it worked.  If you have to you could find a different boot disk that will just give you the bash.  Any type of boot disk will work as long as it gets you to the bash and able to access your grub.

---

### Post by meierfra on 2007-10-30
You need to use "sudo grub"  in place of "grub"

---

