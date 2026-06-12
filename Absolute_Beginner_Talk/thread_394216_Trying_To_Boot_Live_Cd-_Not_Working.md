---
title: "Trying To Boot Live Cd- Not Working?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by numerical on 2007-03-26
Hello,

I just finished burning the live CD to a blank CD at a slow speed (data verified and all).I want to add a new partition to XP but when i reboot nothing happens>

So I have rebooted  and nothing happens ? When I click on the CD and open it or autoplay the Ubuntu program runs with the free apps and all adn it even says "this is the live CD" 
It sems like i have the right CD i just can get it to boot from the CD.

How can I get it to run when I reboot?


Thanks 
Numbers

---

### Post by NicoleM on 2007-03-26
have you made sure your optical drive is first in the boot order in your bios?

the computer needs to check the cd drive first instead of the hard drive in order to boot from it.

access your bios however your manufacturer has you do it (often F1) and look for boot options and move your cd drive ahead of your hard drive then reboot.

---

### Post by numerical on 2007-03-26
Thanks Nicole Now that you have explanied that it makes sense. 

Thanks again 
Numbers

---

### Post by numerical on 2007-03-26
by the way do you know how long this will take to install on a new partition in XP?

Numbers

---

### Post by xueg0i on 2007-03-26
There are two things that might have gone wrong:

#1. You forgot to mention in your cd-burn-program to burn a bootable cd (some programs do have this option, don't forget to finalize your cd!)
#2. Your bios is configured not to boot from CD

If these problems are not the case, then I don't know what you've done wrong.

TOO LATE, SORRY FOR THE DOUBLE REPLY.

---

### Post by agiamba on 2007-03-26
Easy, you aren't booting into your cd. You want to press a key (for Dell's I believe it's F8) when the bios is loading up. An Ubuntu install should take 10-15minutes, but using the live cd you can still access the internet and carry on with your life while it's installing.

---

### Post by NicoleM on 2007-03-26
> **numerical said:**
> by the way do you know how long this will take to install on a new partition in XP?

Numbers

i can't answer this for certain as I've not yet installed ubuntu...still getting a feel for linux myself so I'm a newbie with you here.

I think, however, that the context of your question is a little off...you're not installing anything in xp.  xp is a different operating system and linux is netiher installed within xp or within the xp partition. xp will have no bearing on the length of install time.  

that being said: from what i've read (no firsthand experience yet unfortunately) that barring no problems, ubuntu should take less time than xp to install.  maybe 20-40 minutes max is what I'm expecting, but if anyone can confirm otherwise please speak up!  It will probably also depend on your computer's specs as well.

good luck with everything!

---

### Post by xueg0i on 2007-03-26
It took me about 25 minutes on a fairly new laptop.

Good luck.

---

### Post by arron on 2007-03-26
This question i think is going on elsewhere, and i tried to help some.  Have a look, there may be some help there:

[http://ubuntuforums.org/showthread.php?t=394208](http://ubuntuforums.org/showthread.php?t=394208)

There is a nice howto link there you can use to help you install.  It doesn't take long to get running, and there is a big learning curve.  But it has everything you could ever need, makes a nice hobble to learn more, and has a great community.   Welcome!

---

### Post by numerical on 2007-03-26
****Thanks everyone for your help !

 I have progressed to the next step with your advices and find myself hopefully at the last hurdle (:)): I have booted up the UBUNGU OS and I opened the
GPARTED partition tool - and I am ready to resize my NTFS partition (60gig)and free space(30gig)for the EXT3 partition (set primary boot) and as well as a small SWAP parition (1gig) .My question is should I select these settings and then revert to the INSTALL button on the desktop or should i EXECUTE the partition from within Gparted?

Thanks 
Numbers

---

### Post by arron on 2007-03-26
It is all contained in the install portion.  You will find it easier to repartition within the install option since it will setup the OS accordingly.  You have the option to fully format, resize or manually.  Have a look at the options, just don't hit apply until your sure you got what you want.

Good how-to
[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu)

Disk partition within the install setup:
[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu#Partition_Disks](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu#Partition_Disks)

Next step.... geek-dom! Choo-Choo!

---

### Post by NicoleM on 2007-03-26
> **numerical said:**
> ****Thanks everyone for your help !

 I have progressed to the next step with your advices and find myself hopefully at the last hurdle (:)): I have booted up the UBUNGU OS and I opened the
GPARTED partition tool - and I am ready to resize my NTFS partition (60gig)and free space(30gig)for the EXT3 partition (set primary boot) and as well as a small SWAP parition (1gig) .My question is should I select these settings and then revert to the INSTALL button on the desktop or should i EXECUTE the partition from within Gparted?

Thanks 
Numbers


i think there is no need to partition before using the install command on the livecd desktop.


when you choose to install at some point in the installation process it will ask you about partitions and give you a number of options.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) is a step by step install guide with pictures so it's very easy to follow.

i'm not sure what happens if you partition beforehand, but I'm sure there's someone that will be able to answer that...i just know that the install feature WILL give you the option to partition once you get into it.

in the meantime that install guide i linked above is a GREAT resource.

---

### Post by numerical on 2007-03-26
Thanks to both of you . I just went through the steps and now I am waiting for 3 operations to complete that are currently in progress #1) resize NTFS parion to free space #2) Partition primary boot with freed space set to EXT3 and then #3) PArtition very small 1gig primary boot set to swap - lnx. IS THIS CORRECT?

---

### Post by arron on 2007-03-26
yep, that sounds about right.  give it some time, go get a coffee and cross your fingers!

---

### Post by numerical on 2007-03-26
:) Thanks! that very comforting seriously!I have been at this all day  :popcorn: 

Actually something just happened and now the scre n went black but my labtop  looks like it is still on . Any other  advice on the nxt steps from here>?

---

### Post by numerical on 2007-03-26
All Operations Completed Successfully ! Now What >lol  It Says Prepare Mount Points.

---

### Post by arron on 2007-03-26
give it time.  when its done it will want to restart.  When it does remove the cd, hit enter (it askes to remove the cd and hit enter to reboot).  Then reboot and bingo, your own Ubuntu!

---

### Post by numerical on 2007-03-26
Prepare mount points: 

i get a message that says no root file system?

---

### Post by numerical on 2007-03-26
I am stuck on the prepare mounts point page 

It shows me two old partitions from XP (which I am not altering)

Then it shows the two new un formatted partitions swap and /root .the problem is when i click foward to go to the next step i get an error message saying no root system file ?

I appreciate any additional help

thanks
Numbers

---

