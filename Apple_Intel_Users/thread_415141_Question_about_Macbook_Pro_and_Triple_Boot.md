---
title: "Question about Macbook Pro and Triple Boot"
date: 2007-04-20
forum: Apple Intel Users
---

### Post by skwid on 2007-04-20
Here is my current setup.

Apple Macbook Pro 15" 2GB/120GB

I am already using Bootcamp to dual book XP and OSX.  I have 12 gig dedicated to XP and the rest to OSX.  I would like to add in Ubuntu 7.04.  I  have downloaded the desktop CD, and I know I will need reFIT but where do I start?


Thanks for your help.

Jeremy

---

### Post by ronocdh on 2007-04-20
I believe Boot Camp only supports the creation of one additional partition. Since you'll definitely need another one for Ubuntu, you'll have to repartition the drive using the terminal in OS X, or some kind of live CD like GParted. I personally recommend that you use OS X's terminal, however, I don't believe there's a way to do this nondestructively; you'll probably lose what's on your XP part.

Anyone else have a better idea here?

Also, you can grab rEFIt [very easily]("http://refit.sourceforge.net/"), it's a package installer. You can use that even before you add Ubuntu, and I recommend it, because it's much prettier than the interface Apple provides. ;)

---

### Post by skwid on 2007-04-20
Thanks for the tips.  I figured I would go ahead and use reFIT but starting from here is the tricky part it seems.  I think Backup everything just in case and give it a shot this weekend but I thought I would ask around for some tips.

Thanks!

---

### Post by Chowbow on 2007-04-20
I had a similar question, but I don't want to hijack this thread... I have OSX and XP via bootcamp. My XP partition is 40GB, and has plenty of space to fit Ubuntu in there as well. Can I basically partition the XP partition, so that there will be an XP and a Ubuntu partition? Via Bootcamp I would choose to load Windows instead of OSX, and it would go to another bootloader to choose between XP and Ubuntu. Can this be done with minimal destruction and worries?

---

### Post by Mattybook on 2007-04-23
i followe your install manual but at the point of the apt-get install xorg-driver-fglrx part
it can' fetch the files so i can't continue with the aticonfig and X won't start ... 

i think i have no internet when i boot from linux cd so how can i fix this? 
i tried with wireless and with direct cable plugged in, both did not work 

any help would be very appreciated
thanks

---

### Post by ronocdh on 2007-04-23
> **Mattybook said:**
> i followe your install manual but at the point of the apt-get install xorg-driver-fglrx part
it can' fetch the files so i can't continue with the aticonfig and X won't start ... 

i think i have no internet when i boot from linux cd so how can i fix this? 
i tried with wireless and with direct cable plugged in, both did not work 

any help would be very appreciated
thanks
Please let us know more about your hardware. Also, whose "install manual" did you follow? Can you provide a link to it?

Wireless will likely not work out of the box for you, but wired ethernet connection (DHCP-enabled) definitely should. Please post more info for us, e.g. what was the exact error message you got when trying to grab the fglrx driver?

---

### Post by ronocdh on 2007-04-23
> **Chowbow said:**
> I had a similar question, but I don't want to hijack this thread... I have OSX and XP via bootcamp. My XP partition is 40GB, and has plenty of space to fit Ubuntu in there as well. Can I basically partition the XP partition, so that there will be an XP and a Ubuntu partition? Via Bootcamp I would choose to load Windows instead of OSX, and it would go to another bootloader to choose between XP and Ubuntu. Can this be done with minimal destruction and worries?
This is certainly possible, but I unfortunately am not well versed in the ways of nondestructive partitioning in Windows. I suspect that the [GParted CD]("http://gparted.sf.net") would work well for you, but please wait for confirmation from another forum member on that.

Alternatively, you can just google around for nondestructive partition editors for XP. The Ubuntu live CD also has a GUI partitioner, but once again, I have never used it to slice up an XP partition. Please post back with your attempts and results!

---

### Post by Mattybook on 2007-04-24
> **ronocdh said:**
> Please let us know more about your hardware. Also, whose "install manual" did you follow? Can you provide a link to it?

Wireless will likely not work out of the box for you, but wired ethernet connection (DHCP-enabled) definitely should. Please post more info for us, e.g. what was the exact error message you got when trying to grab the fglrx driver?

[http://www.cs.helsinki.fi/u/jzshen/install_feisty.html](http://www.cs.helsinki.fi/u/jzshen/install_feisty.html)
i'm sorry i thought i posted this in the same thread where this maual was...

i have the same mac as the person who made this manual.
a macbook pro 2 ghz 1 gb memory
i have 3 partitions now 55GB mac, 25 windows xp

then i boot the linux cd. it starts loading
with f6 i put lpj=8000000 after the -- from the line that is allready there (about casper or something)

then he boots and x server fails like told in the manual.
then i type the apt-get install xorg-driver-fglrx part and then the pc says: unable to fetch files, could not reach archive.ubuntu.org i think 

so i suppose i don't have any internet, i tried with my airport, i tried direct cable to the cablemodem (yes tested i i had internet in os x) but still the same error message

---

### Post by ronocdh on 2007-04-24
> **Mattybook said:**
> [http://www.cs.helsinki.fi/u/jzshen/install_feisty.html](http://www.cs.helsinki.fi/u/jzshen/install_feisty.html)
i'm sorry i thought i posted this in the same thread where this maual was...

i have the same mac as the person who made this manual.
a macbook pro 2 ghz 1 gb memory
i have 3 partitions now 55GB mac, 25 windows xp

then i boot the linux cd. it starts loading
with f6 i put lpj=8000000 after the -- from the line that is allready there (about casper or something)

then he boots and x server fails like told in the manual.
then i type the apt-get install xorg-driver-fglrx part and then the pc says: unable to fetch files, could not reach archive.ubuntu.org i think 

so i suppose i don't have any internet, i tried with my airport, i tried direct cable to the cablemodem (yes tested i i had internet in os x) but still the same error message
Ah! Well I don't have a complete handle on the exact hardware you're using, but maybe [this post]("http://ubuntuforums.org/showthread.php?t=414194") will do you some good. Please post back.

---

