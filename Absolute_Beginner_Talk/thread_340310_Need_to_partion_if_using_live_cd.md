---
title: "Need to partion if using live cd"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by mainstang on 2007-01-17
My question is do i need to partion my hardrive to allow ubuntu live cd to work.  Im under the impression that the live cd will give me an idea to what ubuntu is like alow me to mess with the desktop, but just have all the features as if i would have installed.  Also, I have not partioned yet and even when i try to install it locks up.  The computer is currently running windows 98SE.  Thanks for the help if anyone can.

---

### Post by bodhi.zazen on 2007-01-17
You do not need to partition your HD to run the Ubuntu Live CD.

You will need to partition your HD if you want to install.

Start by defragmenting, then follow this:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

If that fails, and sometimes if does, you will need to try the alternate CD

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

HTH 8)

---

### Post by bigken on 2007-01-17
like bodhi.zazen no you dont need a partition for the live cd 

as well as defraging windows backup anything imporant better 
safe than sorry 

good luck welcome aboard ;)

---

### Post by mainstang on 2007-01-17
ok i let my computer run the disk check for a while but all it does is just sit at the menu screen.  I have also tried to just start ubuntu like the link says to and the cd is spinning, but it still stays at the menu screen.  I burned it again at 4x speed to make sure.  Ubuntu looks great if I can figure it out.  I have pentium 3, 384m of ram.  Could the cd drive be to slow to run live cd.  It currently has windows 98se.  Thanks for the help so far.

---

### Post by bodhi.zazen on 2007-01-17
> **mainstang said:**
> ok i let my computer run the disk check for a while but all it does is just sit at the menu screen.  I have also tried to just start ubuntu like the link says to and the cd is spinning, but it still stays at the menu screen.  I burned it again at 4x speed to make sure.  Ubuntu looks great if I can figure it out.  I have pentium 3, 384m of ram.  Could the cd drive be to slow to run live cd.  It currently has windows 98se.  Thanks for the help so far.

Could be a little slow, give it some time :)

---

### Post by mainstang on 2007-01-17
i went away for like 25 min and all it showed was the main menu.  with a couple of dots running threw the middle.  It looked like maybe the screen wasnt set right.  If you think I should wait longer just let me know.:D

---

### Post by bigken on 2007-01-17
what is the spec of your PC ?

---

### Post by mainstang on 2007-01-17
I have a pentium 3 382mb ram, windows 98se currently running, dell computer, 10 or 12 gig hard drive.  Sorry for being so vague wish i knew more.  Thanks for dealing with my lack of knowlege.

---

### Post by Pobega on 2007-01-17
It sounds like theoretically your PC should be able to run the Ubuntu LiveCD, but sometimes it just doesn't work.

If you want to partition your drive I suggest downloading the gparted liveCD from gparted's official website, and running it as root. Don't forget to defragment any FAT/NTFS partitions first, though, otherwise gparted will just feed you an error.

Then once you've partitioned be sure to remember the name of your new partition, and install Ubuntu to that partition (/dev/hd* or /dev/sd* depending on your hardware) using the Ubuntu alternate installation CD (Which is available on the main site, [http://ubuntu.com/)](http://ubuntu.com/)).

Welcome to Ubuntu :D

---

### Post by vmikalinis on 2007-01-17
I know it doesn't help much, but I tried running 5 different linux distro's on my compaq pIII laptop with no luck but it does run windows 98se.  I broke down and bought a used amd 64 3500 which fixed the problem.  ;)

---

### Post by mainstang on 2007-01-17
I read in one of the other post that you can have the cd do the partioning for you, also would i load gparted in windows 98se. or is it on the disk menu when i have the system set up to boot from cd.  Would this fix my problem with the menu not going away.  I will try to burn the cd again to see if it is a bad burn.  The only thing that i can select and the main menu will go away is if do a memory test. Other selections just freeze when i hit enter on them.

---

### Post by Pobega on 2007-01-17
> **mainstang said:**
> I read in one of the other post that you can have the cd do the partioning for you, also would i load gparted in windows 98se. or is it on the disk menu when i have the system set up to boot from cd.  Would this fix my problem with the menu not going away.  I will try to burn the cd again to see if it is a bad burn.  The only thing that i can select and the main menu will go away is if do a memory test. Other selections just freeze when i hit enter on them.

gparted is a Linux app, I'm almost certain it doesn't have a Windows version. And yes, you have to run it from within the LiveCD, not from Windows.

---

