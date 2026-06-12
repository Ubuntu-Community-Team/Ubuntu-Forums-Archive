---
title: "Grub loading, please wait... error 17"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by ferniebiker on 2008-01-13
Ok so first off I am a total noob. i just got a new computer and it had xp installed on it. I built it with 2 hard drives, one for xp and one for Linux. When it was shipped, one of the hd's became unplugged and since i did not know this, I partitioned one drive. Once I reattached the second hd i wanted to get rid of the ubuntu partition so that I could run my system how I originally wanted to (one os per hd). Now when i try to start my computer it gets stuck on a screen that says:

Grub Loading Stage1.5
Grub Loading, please wait...
Error 17
_

i need good instructions because i know very little about code. 

thanks

p.s.
i have already looked around a bit on the forums and everything seems to be over my head. i need retard instructions.

---

### Post by Xavieran on 2008-01-13
I think you deleted the Ubuntu partition with grub's menu.lst ...

You need to fix the Master Boot record...basically find a windows recovery CD and type fixmbr at the console that it (should) gives you

---

### Post by ferniebiker on 2008-01-13
where would i find this console.

---

### Post by JoshuaRL on 2008-01-13
Hey dude my brother's HP laptop that I'm the tech department for has this same issue.  But he doesn't have any other OS installed.  Clean wipe and it worked for a couple weeks and now it won't boot past Grub error 17.  Do you know what that means exactly?

GO ITEAM!

---

### Post by Xavieran on 2008-01-13
In your Windows recovery disk...boot from the recovery disc like you booted the Ubuntu install CD and it should give you a console...

---

### Post by ferniebiker on 2008-01-13
for some reason i cant get the disk to boot. or there are some problems making it run. what button do i press to make it run. an f key i'm guessing?

as for the other guy i think error 17 has to do with an unfound drive partition or something.

---

### Post by Xavieran on 2008-01-13
What has happened is that GRUB's configuration file was on the Ubuntu partition which has now been wiped...when grub first starts it goes to find it's confiuration file in Ubuntu's partition but it can't access it because there is no ubuntu partition...he just wiped it...so I said go into the windows recovery disk and type fixmbr at the console they gave you because that will restore windows bootloader...

---

### Post by ferniebiker on 2008-01-13
could you provide steps on "going into the windows recovery disc"

---

### Post by Spaceman Spiff on 2008-01-13
1) Put Windows CD into cd drive
2) Wait for CD to start
3) Look for "press R to enter recovery console"
4) wait until you see a text prompt
5) type fixmbr

---

### Post by ferniebiker on 2008-01-13
as i try to boot it, it never says "press R to enter recovery console". i pressed r the entire time it tried to boot. no difference.

---

### Post by Xavieran on 2008-01-13
First things first...do you have a windows recovery disc?

Second if you do then simply place it in your cd drive while the computer is booting and then restart...make sure the boot order is CD first...if it isn't go into your BIOS and select the option "boot device order" or something similar...their should be a splash screen with the keys to activate the bios setup...maybe F2 or F12...

---

### Post by JoshuaRL on 2008-01-13
Is there any way to do the same thing from Ubuntu?  I don't have any Windows on that laptop.

---

### Post by Spaceman Spiff on 2008-01-13
Nooooo sorry to be vague :), you have to boot into the cd.  Just incase you don't know how to do that:

1)Put the cd into the cd drive
2)The first screen that appears should list your system specs (such as processor speed, ram, etc) (sometimes some motherboards have flash screens that cover this)
3)look for something that says "boot menu" or "first-time boot menu", sometimes its f8 and sometimes it's f12
4)a menu will appear, select anything that resembles "cd"
5) follow previous steps

---

### Post by Xavieran on 2008-01-13
> **JoshuaRL said:**
> Is there any way to do the same thing from Ubuntu?  I don't have any Windows on that laptop.

Sabayon Linux' cd has an option called fix mbr...I'm not sure if it would work for ubuntu though (It stuffed up fstab in the process of fixing the mbr for me...:))

---

### Post by c0met on 2008-01-13
Hi FernieBiker

Before getting into the code and stuff, it might be easiest if you downloaded a bootable ISO for the program called SuperGrub. Burn this to a CD and then boot your system from this CD. It will give you options for...
[LIST]
[*]making your win(dows) drive bootable
[*]making your linux drive bootable
[*]setting your system up for a dual boot
[/LIST]
If you have Windows on one drive and Linux on the other, then you simply need to choose the dual boot option and it will setup the Grub menu for you so that you can select which operating system to boot into.

This is a great little program to have on hand. It's got me out of a few tight spots. You can download the ISO from...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by ferniebiker on 2008-01-13
cd is first in line, still no boot from disc

---

### Post by JC Cheloven on 2008-01-13
This will be pretty obvious, but "just in case" :
To choose which device is to be checked first, you have to enter the bios setup at startup. The steps are:
1) Put cd (windows recovery in this case) on the unit. 2) Power on the PC. 3) Inmediatly press and hold the proper key to enter in the bios. It's usually F12, F8 or F2. 4) On bios menu, go to something like "boot devices" an choose the CD unit as the first one. 5) Exit from bios, usually with "esc" key. This will start the system from the cd right away.

---

### Post by ferniebiker on 2008-01-13
> **JC Cheloven said:**
> This will be pretty obvious, but "just in case" :
To choose which device is to be checked first, you have to enter the bios setup at startup. The steps are:
1) Put cd (windows recovery in this case) on the unit. 2) Power on the PC. 3) Inmediatly press and hold the proper key to enter in the bios. It's usually F12, F8 or F2. 4) On bios menu, go to something like "boot devices" an choose the CD unit as the first one. 5) Exit from bios, usually with "esc" key. This will start the system from the cd right away.

tried that and stil no go. 

i will try the super grub thing.

---

### Post by ferniebiker on 2008-01-13
i dont know if this will help but i'm pretty sure that gubs main program was on the partition that i deleted.

---

### Post by pienene on 2008-01-14
Hi, same thing happened to me - after installing kubuntu on laptop with vista ended up with 6 partitions(because for some reason thought I have to divide them  upfront, ha..) > so 2 should be empty -! wrong -  got the same error - booting from windows recovery didn't help - so I reinstaled kubuntu. now seems fine except I have now 8 partitions and about 10 diferent choices at startup....
I gues I have two kubuntu now... 
but I can start up my computer!
how to sort this out, now seems a bit messy for my liking....

---

### Post by pienene on 2008-01-14
ok, so, now i have succesfully deleted all partitions and restored windows startup with super grub - thanks to your advice! will try to install it again properly this time

---

