---
title: "Please help! Ubuntu wont install!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-12
Ok, i downloaded version 6.10.  I used winmd5sum to make sure that the download was valid. I then burned the disc with infrarecorder at 1x speed.  I have a dell optiplexGX60, celeron 2 gHz processor, 1 gB of RAM.  This is the 5th or 6th time ive been through the entire process of downloading the iso, burning it, trying to install and im just about to tell everyone who said "ubuntu is so user friendly!" to come to my house and show me how its done.

First of all, im not entirely computer illiterate.  I am however new to linux/ubuntu.  Whenever i loaded the 6.10 desktop cd, the first thing i did was "check cd for defects"....this passed without a hitch.  Then i proceeded to selecting "start or install ubuntu" .  This led me to a "windows like" post screen for about a minute.  Then after this, it shows ubuntu booting up (i guess, it was just a bunch of lines of words and numbers running down the screen) then it just stops!  Does nothing else, just stops.  I am just about tired of this hype everyone is giving ubuntu's "ease of use".  I have tried EVERYTHING people have said in these forums and across the internet. Please help.

---

### Post by 13thMonkey on 2007-06-12
How long did you wait for? The LiveCD can take quite a long time to load on lower-end PCs. Give it maybe 10 minutes or so and then try a reboot (which has fixed it for me in the past). What is the last message you normally see?

---

### Post by Inxsible on 2007-06-12
Why are you trying to install 6.10, when the latest version(7.04- Feisty) is more user friendly. 
 
Don't know if it will solve all your problems, but I was just curious as to why you wanna use an older version.

---

### Post by ITdrummer on 2007-06-12
it stops at a different point each time i do it. I would have waited longer but the green activity light on my machine was not blinking.

---

### Post by phr0ze on 2007-06-12
Ubuntu can not be immediately compatable with all possible hardware either. You could try to unhook all unneeded devices and try again or try the alternate CD.

For most computers Ubuntu works fine out of the box... er iso

---

### Post by ITdrummer on 2007-06-12
the reason i am trying 6.10 is because ive gone through the entire process with version 7.4 also.  Same result.  The only version i can get to work is VERSION 5.04!!

---

### Post by ITdrummer on 2007-06-12
> **phr0ze said:**
> Ubuntu can not be immediately compatable with all possible hardware either. You could try to unhook all unneeded devices and try again or try the alternate CD.

For most computers Ubuntu works fine out of the box... er iso

the only things i have plugged in are my keyboard, mouse, and monitor.  I assumed that these were needed.

---

### Post by 13thMonkey on 2007-06-12
I've had quite a few experiences with LiveCDs (not just Ubuntu) where nothing appears to be happening too. As I said, wait 10 minutes and then try a reboot (especially if you're getting different messages each time).

As suggested you might want to try the latest version (Feisty Fawn) too. It will still run perfectly well on your hardware (assuming you can get it to install :o)

The alternative install CD is a good option too as it doesn't use a shiny GUI or LiveCD so should cause you fewer problems. Once the basic system is installed just type 

> sudo apt-get install ubuntu-desktop for the full Ubuntu install.

---

### Post by Gagle on 2007-06-12
If you have a PXE boot capable bios, you can try a PXE-LAN Edgy install using two diskettes.
It's a bit of hassle, for you need another working pc that serves a server.

Consider this option if all else fails....

regards,

Gagle

---

### Post by vinceZZZZ on 2007-06-12
Hello,

i too cannott install xubuntu......my PC is 8 years old......bought in 1999.....it is a pentium 3... 450 megs...with a 3d voodoo graphics chip......VERY COMMON PC....an MSI motherboard...

well xubuntu just fails.....it loads the live CD.....then starts a REAL install....and then stops dead on progress.....you can wait 5 minutes and ther is no hard drive activity and the mouse is LOCKED...

my PC always starts out with a FLAT hard drive....not formatted....xubuntu then partitions the drive....but i ges it should also format it...(it never gets to that point)

tried it all a couple of times and it failed in the exact same fashion...

the only thing connected is the screen, mouse, keyboard and ethernet card (ROUTER)

------------------------------------------------------------------------------------------------------------------------------------

maybe it is worth trying the ALTERNATE CD for xubuntu......like you describe...

this is not hte first LINUX that has failed on this machine.....MANDREVA 2005 also failed.....got half way thorugh install....50 minutes....then simply hangs...

also MANDRAKE 2003 failed.....but this was resolved by changing the VGA setting to LOW REZ .....a BOOT option....

i am not sure with xubuntu....because it's 2007 and now.....and my machine is 8 years old....but it runs winXP just fine....

it just seams odd that my PC would not run a ......TAILORED linux package........ that is made for OLD HARDWARE

what do you think

V

---

### Post by Gagle on 2007-06-14
Maybe your hard-drive has some issues.  I would consider booting with GParted (using a live CD or diskettes) and prepare yourself your partitions.  You need a root (I recommend ext3 file-type) and maybe a home partition.  After that , Boot using the live-cd of your favorite distro.  The install should take care of the swap.
It could also hang because of the video card detection.  

I would try the alternate CD , then maybe try VectorLinux.  It's a very nice lightweight distro with interesting install methods.  Take a look at their official web page.  It saved my old laptop....

regards,

Gagle

---

