---
title: "i need help dual booting 3 hard drives ive tried everything i can think of"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by scooterboi on 2007-01-04
i have recently just installed  ubuntu on my spare 40 gig hd and i already had windows xp on an 80gig hd and i had a storage hd wich is 40gig 4 windows  xp  the linux instalation wen twelll and i cna use linux if i unplug windows and put tat ide into the linux hd  i tried to follow a tutorial ina forum that said something about changing the menu.lst file inlinux im pretty sure i did all of that correctly and then attempted to change the drives around as the tutorial said but it doesnt do anythng grub dosent recognise windows! im not sure if im just not puttng them on the right ide or if the jumpers are incorrect or what im totaly confused on what to do i would like to have it so that i start up my pc and it goes into grub and if i dont choose to go into linux after x amount of seconds it boot windows ! i would apreciate any help  oh by the way my mother board is an asus p5vdc-mx

---

### Post by rsambuca on 2007-01-04
Did you have both drives connected when you installed ubuntu?

---

### Post by scooterboi on 2007-01-04
no i didnt i disconected botht the windows drives just to be safe!

---

### Post by rsambuca on 2007-01-04
That's your problem.  When ubuntu installed, it obviously didn't know that you would be adding other hard drives.  When ubuntu or windows, or any operating system is installed, it has to write to a section of the primary hard drive called to the MBR (Main Boot Record, I think).  The MBR contains the info on where the computer should look to get the boot-up files.  After you installed ubuntu, you switched the drives around, and the MBR points to the wrong (or non-existent) place.

How are your drives arranged?  
Are they IDE drives or SATA drives?

---

### Post by scooterboi on 2007-01-04
thanks umm they are all ide hard drives and right this moment all that is plugged in is the windows drive the other 2 arent plugged in is there any risks of installing linux whle windows is plugged in?

---

### Post by scooterboi on 2007-01-04
oh by the way this is the link to the tutorial i followed [http://ubuntuforums.org/showthread.php?t=120994](http://ubuntuforums.org/showthread.php?t=120994) it may help because that tutorial said to unplug windows?

---

### Post by rsambuca on 2007-01-04
I guess that is one way of installing, but it isn't what I have done.  I have 3 hard drives as well, but 2 IDE and 1 SATA drive.  I currently have XP and Vista on the primary IDE, and ubuntu 32 bit, ubuntu 64 bit, Sabayon 32 bit, Sabayon 64 bit, and kubuntu on the SATA drive.

I think it is perfectly safe to go through the installation with all your drives connected providing you know which one is which.  You can determine this by entering your BIOS prior to boot and checking the boot order of the drives.

EDIT:  Anyways, I'll keep an eye on this thread, but I am too tired...  Going off to bed now.

---

### Post by nquinnathome1 on 2007-01-04
Having other drives plugged in is never 100% safe when installing other operating systems, but its not the machine that poses the threat it's the user; as long as you make sure you properly identify which disk you're installing Ubuntu to, you can't go wrong; you get asked during the installation how to partition; choose manually and then you get to view/modify your disks using a GUI partition manager; this partition manager can be used to select and view the other disks too, so just identify which disk you really want and make sure on the next install screen that is the one you choose.

Not too difficult as you should be able to see through looking at partition sizes/remaining space which drive is which.

---

### Post by scooterboi on 2007-01-04
Thanx man youve helped me heaps  you probaly wont read this now  but u may in the future thanks  and just to let you know vista isnt out in australia yet  is it good?

---

