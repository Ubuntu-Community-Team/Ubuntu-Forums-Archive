---
title: "[SOLVED] New and cant run 7.10"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Luckyjinxes on 2008-01-05
Im new to Linux and am interested in it but after downloading 7.10 AMD to a "live CD" i wanted to try to get a feel for it before making the change from XP.  But as soon as i select Start/Install from CD the screen will change and it says its running live kernels?  Then the monitor will turn of and say its in sleep mode.  I waited several minutes but still nothing happened.  I restarted again and tried in safe mode but to the same result.  Does anyone know whats wrong?  I run a Nvidia Geforce 8600 vid card and in terms of everything else it should be more than capable of running 7.10.  Any advice pls?  I really want to try it out

---

### Post by frup on 2008-01-05
Get some virtual machine software and try it in that, it should work and you can experience your self a bit.

By safe mode do you mean safe graphics mode?

I'm guessing you have plenty of ram. Did you notice any error messages? Anything like kernel panics or the like? Do you know what type of mother board you are using?

> 	
sowelie  
Re: Ubuntu 7.10 boot up trouble
Sounds similar to an issue I had. Try hitting F6 after the cd boots when you get to the install menu. Before the two dashes add noapic. This should get you into the live environment. You'll need to do the same thing for your first boot into ubuntu and then install the non free graphical drivers.

---

### Post by lolzlolz on 2008-01-05
u r sure you're supposed to use the amd i use i386 with core 2 duo intel, ive never sued amd though so

---

### Post by Sef on 2008-01-05
1) Have you [md5summed]("https://help.ubuntu.com/community/HowToMD5SUM") the download? (Check for a good download.)

2) Did you burn the iso as an iso? (don't burn it as data.)

3) Did you burn the iso at 4x or less? (Faster can corrupt the download.)

4) Have you checked the disk for errors?  At start/install menu, go down to Check Disk for errors.

---

### Post by lolzlolz on 2008-01-05
no wonder i corrupted some of my disks
i burned at 24x always :P
normally worked though

---

### Post by Luckyjinxes on 2008-01-05
Yes i burned it as an iso and not as data.  I have 1GB of RAM nd im not too sure about my motherboard...  My pc is '05 and im pretty sure its AMD.  Ty for ur replies i will try the methods one by one to see if i can get this thing to work

---

### Post by frup on 2008-01-05
The version you downloaded is 64bit Ubuntu though so you need a 64bit chip. The i386 version is 32bit and generally runs on a 64bit processor. You should try the i386 version too. I've installed on 64bit computers where one 32bit release or one 64bit release won't work but the other bit does work.

The acpi bit is good to pay attention to. With an acer laptop I installed ubuntu on it had problems with the extra buttons (such as the wireless on/off) and various other problems until I installed acer_acpi.

---

### Post by Luckyjinxes on 2008-01-05
O lol he said add noapic BEFORE the 2 dashes.  I did it after well ill try that then try i386 version.  I sent u a message u can just ignore that one because im basically repeating myself in this reply.  Thanks!

---

### Post by lolzlolz on 2008-01-05
eh, that's what i was trying to say but i wasnt very clear :P 
good luck :)

---

### Post by Luckyjinxes on 2008-01-05
OIC!!!  Thanks you all lol i feel so dumb...  Why did i choose the 64bit?  I should have selected standard computer, iunno the AMD thing threw me off.  Man..  no wonder.  Time to get my Linux on!

---

### Post by frup on 2008-01-05
That's probably a good point, i've always felt it might be better to call it 32bit and 64bit rather than i386 or AMD. Maybe there is a technical reason for this that is more important. :confused:

---

### Post by Luckyjinxes on 2008-01-06
Ok ive run the new one and now after it loads it seems to be working until...  I get a bunch of permission denied messages = (

---

