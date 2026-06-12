---
title: "can't boot off ubuntu cd from macbook1,1"
date: 2010-10-24
forum: Apple Hardware Users
---

### Post by ikcoder on 2010-10-24
I've been running Ubuntu (9.04) for a while as a VM on my Macbook and I finally have the need to setup dual boot because my work has become more intensive on the linux side.

I created the 2nd partition on my hard drive and installed refit on my macbook. However, when i try to boot off the Ubuntu cd that i burned from the iso it seems to not be working.

I have a Macbook1,1 (core duo processor). I tried 3 different ubuntu iso's (10.04, 9.10, 9.04) burned them onto 3 different disks. The 10.04 disk altho it looks valid on the iMac that i burned it on, the Macbook doesn't find the boot image. The two 9.xx CD's both bring up the ubuntu start menu but when i try to boot off of the cd (so i can run gparted to delete the windows partition created by boot camp) it just hangs for hours. i literally waited over an hour (and multiple times before i aborted and tried again). Should it really take that long to boot off the cd? Doesn't make sense....

 I've since confirmed that my macbook can actually boot off a mac osx cd, so it's not a bad cd drive.

I also confirmed that it's not just the "try ubuntu" option that doesn't work, none of the options seem to work. It just hangs on the opening Ubuntu screen after selecting english as the language.

I also tried the different boot options and none of those seem to work either.

I'm guessing because of the age of my machine (2006 macbook1,1) the ubuntu cd is missing some driver that would enable the machine to boot off of it. 

In the meantime i confirmed that the ubuntu CD's i burned are valid because i can boot off of them with a newer (2008) iMac.

This is really disappointing. I'd really like to have ubuntu installed as a boot option on this macbook, but i'm running out of ideas on how to make this happen.
 	 	 		ikcoder 	 	 		[View Public Profile]("http://ubuntuforums.org/member.php?u=1170999") 	 	 		[Send a private message to ikcoder]("http://ubuntuforums.org/private.php?do=newpm&u=1170999") 	 	 	 	 		[Find More Posts by ikcoder]("http://ubuntuforums.org/search.php?do=finduser&u=1170999") 	 	 	[Add ikcoder to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=1170999")

---

### Post by linuxopjemac on 2010-10-25
Install rEFIt 0.14 in OSX and then you reboot with the CD in. You will see the CD appear as option. Boot from it. I found out that booting with rEFIt is easier.
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by Dans564 on 2010-10-25
The best way to do this would be to make a second partition with boot-camp. then use the live CD to delete that partition leaving empty unformatted space.  then u simply tell Ubuntu to install in the empty space and your done. refit is nice but unnecessary as well.

---

### Post by Dans564 on 2010-10-25
i would also check that the dvds ur using are compatible.  i had that problem for a while and after switching the brands everything went fine

---

### Post by ikcoder on 2010-10-25
Hi All,

Thanks for your advice, but I have tried all of those things.  I am using rEFIt and i used boot camp to create the windows partition.  I can't boot off of the cd (after selecting it in rEFIt) to get to the point where i can remove the windows partition so that Ubuntu will install.  I also tested the CD (not DVD) that i burned the ISO image onto.  I was able to boot of the CD from a newer iMac, so the CD is not the problem either i don't think...

any other thoughts are appreciated...

thanks...

ian

---

