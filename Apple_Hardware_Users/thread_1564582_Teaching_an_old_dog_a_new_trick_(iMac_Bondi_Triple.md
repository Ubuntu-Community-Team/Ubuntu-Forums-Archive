---
title: "Teaching an old dog a new trick (iMac Bondi Triple Boot: Mac Os X, Mac Os 9, Ubuntu)"
date: 2010-08-30
forum: Apple Hardware Users
---

### Post by LtPitt on 2010-08-30
Hello my friends!

Question N.1: is this possible?

I've been partitioning and formatting and installing like crazy without luck.
I can install 10.3, no problems.
Then I install Mac OS 9, no problems.
Then I install Ubuntu 9.04 and it kills my Os X and Os 9 boot.

Does any hero has hints on how to achieve this result? :(

---

### Post by LtPitt on 2010-08-30
ps

of course I think the main limit would be the 8 gb problem that affected those old imacs...

But maybe a true indiana jones could suggest me how to partition and install correctly.

If I could put mac os x and mac os 9 AND yaboot in the 1st 8 gb and my root partition in another place maybe I could do it.

Or maybe I'll just have to live with Mac OS X and 9 but it sounds like a defeat :(

---

### Post by mikenzb on 2010-08-31
I would like to know too
I have a Emac 1.42 Ghz And i was thinking of Quad Booting it
Leopard , tiger , 9 And ubuntu 10.04 (PPC) :P
Only Problem Is I Dont Know Where to Start Off.
And I have never Used Ubuntu Before. I do not want to keep formating My hd again and Again 
If its going to fail
Lets Just Hope when i try this Next week it will work. or else im doom :(
I will be book marking this  Thread Anyways 
PS I Only Have 512 Mb Of ram. :KS

---

### Post by linuxopjemac on 2010-08-31
You have to read about yaboot, you will find it here among other stuff:
[http://mac.linux.be/content/apple-powerpc-wiki](http://mac.linux.be/content/apple-powerpc-wiki)

---

### Post by LtPitt on 2010-08-31
Hi mikenzb!

In your case I'd suggest make 3 partitions from the mac os x installation and leave some free space for the future 4 partition for ubuntu.

Install mac os x (I just don't know how to handle 10.4 and 10.5 on the same mac but I think you can just install it on another partition without much too problems) in its partition.

Install mac os 9 in its partition.

Start ubuntu and choose the "use free space" option to partition/install.

That should be it :)

---

### Post by LtPitt on 2010-08-31
> **linuxopjemac said:**
> You have to read about yaboot...

I know, my friend...
I was just wondering if anybody knew if ubuntu was able to get past the 8gb startup disk limit of my imac :)

---

### Post by mikenzb on 2010-08-31
> **LtPitt said:**
> Hi mikenzb!

In your case I'd suggest make 3 partitions from the mac os x installation and leave some free space for the future 4 partition for ubuntu.

Install mac os x (I just don't know how to handle 10.4 and 10.5 on the same mac but I think you can just install it on another partition without much too problems) in its partition.

Install mac os 9 in its partition.

Start ubuntu and choose the "use free space" option to partition/install.

That should be it :)
Right 
Will Installing ubuntu 10.04 ppc Kill my mac os 9 , 10.4 and 10.5? :confused:

---

### Post by guidop on 2010-09-01
I think you might be able to get past the 8 GB limit if you partition so that the boot partition (and maybe all of OS9) are within the first 8 GB of the disk.

I have dual booted OS9 and Ubuntu (5.04!) on a Bondi-blue iMac with a 13 GB disk, but the install was done with that disk installed in a later slot-loading model.

A second possible problem may still occur with the current mac ppc partitioning tool killing the OS9 drivers.  See this archived thread for some details:
[http://ubuntuforums.org/showthread.php?t=495347]("http://ubuntuforums.org/showthread.php?t=495347") 


I would suggest treating this machine as a learning experience.
Even with a minimal install and very lightweight desktop, such as fluxbox or lxde, you will still need more than the original 32 MB RAM which came with the machine, probably 128 MB or more.  Even then, in my experience, performance will be less than on an old Pentium PIII machine.

For good info on running on older ppc machines, also search he forums for posts by oswaldkelso.

---

### Post by mikenzb on 2010-09-01
> **guidop said:**
> I think you might be able to get past the 8 GB limit if you partition so that the boot partition (and maybe all of OS9) are within the first 8 GB of the disk.

I have dual booted OS9 and Ubuntu (5.04!) on a Bondi-blue iMac with a 13 GB disk, but the install was done with that disk installed in a later slot-loading model.

A second possible problem may still occur with the current mac ppc partitioning tool killing the OS9 drivers.  See this archived thread for some details:
[http://ubuntuforums.org/showthread.php?t=495347](http://ubuntuforums.org/showthread.php?t=495347) 


I would suggest treating this machine as a learning experience.
Even with a minimal install and very lightweight desktop, such as fluxbox or lxde, you will still need more than the original 32 MB RAM which came with the machine, probably 128 MB or more.  Even then, in my experience, performance will be less than on an old Pentium PIII machine.

For good info on running on older ppc machines, also search he forums for posts by oswaldkelso.
Dam if its killing mac os 9 drivers i will not be able to install mac os 9
ohh well
i was going to partition my eMac hd 
100gbs tiger
45gb leopard
5gbs os 9
10gbs ubuntu
But ohh well :(
I just instal tiger leopard and ubuntu 
i hope to try it by next week

---

### Post by guidop on 2010-09-01
The linked thread: 

[http://ubuntuforums.org/showthread.php?t=495347](http://ubuntuforums.org/showthread.php?t=495347)

gave 2 ways to maintain OS9 boot capability with later installs:

1) Use an older version of the partitioning tool to preserve OS9 boot partitions by using an Ubuntu 6.06 install disk.
(I used this method on a slot-loading iMac.)

2) Re-install the OS9 drivers after installing Ubuntu.  
(As suggested by user fkdev.)


With proper partitioning, drivers, and a well-configured yaboot.conf file with different aliases for the Tiger and Leopard installs, you should be able to make the machine quad-bootable, *assuming it could natively boot OS9 in the first place*.  You'll have to learn a bit about yaboot, and its alias command to make this work.
(According to this: [http://www.everymac.com/systems/apple/emac/stats/emac_1.42.htm](http://www.everymac.com/systems/apple/emac/stats/emac_1.42.htm), only certain 1.0 GHz and earlier eMacs can natively boot OS9.)

In addition, a working mac-on-linux application (Does mol work in Ubuntu 10.04?) should be able to boot OS9 from either a disk image or disk partition (without the OS9 drivers on the physical disk) with a properly edited macos.molrc file.
(I'm using Debian Lenny + mol to play OS9 games on a PowerBook that can't natively boot OS9.)

---

### Post by mikenzb on 2010-09-01
> **guidop said:**
> The linked thread: 

[http://ubuntuforums.org/showthread.php?t=495347](http://ubuntuforums.org/showthread.php?t=495347)

gave 2 ways to maintain OS9 boot capability with later installs:

1) Use an older version of the partitioning tool to preserve OS9 boot partitions by using an Ubuntu 6.06 install disk.
(I used this method on a slot-loading iMac.)

2) Re-install the OS9 drivers after installing Ubuntu.  
(As suggested by user fkdev.)


With proper partitioning, drivers, and a well-configured yaboot.conf file with different aliases for the Tiger and Leopard installs, you should be able to make the machine quad-bootable, *assuming it could natively boot OS9 in the first place*.  You'll have to learn a bit about yaboot, and its alias command to make this work.
(According to this: [http://www.everymac.com/systems/apple/emac/stats/emac_1.42.htm](http://www.everymac.com/systems/apple/emac/stats/emac_1.42.htm), only certain 1.0 GHz and earlier eMacs can natively boot OS9.)

In addition, a working mac-on-linux application (Does mol work in Ubuntu 10.04?) should be able to boot OS9 from either a disk image or disk partition (without the OS9 drivers on the physical disk) with a properly edited macos.molrc file.
(I'm using Debian Lenny + mol to play OS9 games on a PowerBook that can't natively boot OS9.)

This is way to hard for me to do i will just not install 9
but willl ubuntu 10.04 kill os x? 
cause if it does  ](*,)
It should boot os 9 
lets just hope it does. 
i got to get installing once i get my main mac pro back
i just wnt to do a quad boot of this emac then sell it :KS

Well we see how it goes

---

