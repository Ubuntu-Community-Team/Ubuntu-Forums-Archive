---
title: "Triple Boot(OS X, Ubuntu, Win 7)"
date: 2010-01-25
forum: Apple Hardware Users
---

### Post by Nohtanhoj on 2010-01-25
Well, I'm seriously thinking about getting a triple boot going on my 24" iMac, but before I do, I've got a few questions.

1. Does anyone here have any experience with triple booting (specifically to the install process). I'm pretty computer literate, but there's a few installation specific things that are making me a little nervous.

2. The reason I'm getting nervous about these things is my past experience with editing the partition table on my Mac. When I was attempting to get Ubuntu booting, I over-wrote my entire internal hard drive *Doh*. Good thing I had Time Machine backups on a separate drive. The second time, I installed the GRUB bootloader to the internal drive and it over-wrote my EFI bootloader, thus making my beautiful Mac a Linux only machine. Double hooray for Time Machine backups.

Would using the newest version of Boot Camp to partition again and install Windows 7 create similar problems? The specific thing I'm worried about is when the Windows setup decides to install the Win 7 bootloader to the root of my drive. Will this over-write my existing setup, and thus make me start from scratch all over again?

If so, I'm comfortable with doing a full drive format and recovering from Time Machine. However, this brings up new concerns. If I complete the Windows install process, over-write my Mac and Linux partitions, and then choose to format, will my Win 7 serial number work again?

Thanks for any help you can provide.

---

### Post by ed12348 on 2010-02-07
i currently have this setup, if you boot to the ubuntu disc and install from the livecd, just make sure its going to resize the bootcamp drive (or resize the mac partition manually) , but at the end where the install summary is shown select advanced and tell it to install grub on the bootcamp drive. 

By doing this when you boot, hold down the options key, here you will be greeted with 2 options, mac or windows, select windows. This then shows grub where you can pick either windows or linux. You must install windows using bootcamp first! and i strongly recommend a full backup first incase of accidents.

also what you have to make sure is that none of the installers touch the mac partition, thats why you had problems before, windows when installed on the bootcamp partition doesn't touch mac, and linux installed in its own partition, shouldn't mess with mac either, hence at the end where it shows the install summary for ubuntu, click advanced and make sure grub will install on the windows drive.

so in summary, mac partition (do not touch), bootcamp for windows, linux in its own partition, but grub must go into windows partition.

hope this helps :D

---

### Post by Dullstar on 2010-02-07
Does "touching the Mac partition" include shrinking it to make room for Linux?

---

### Post by linuxopjemac on 2010-02-08
I have read that shrinking is possible without problems.
[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=17](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=17)

---

### Post by Dullstar on 2010-02-20
Mac OS X still works, but the Windows was hosed and Linux won't boot...
Just a note:  It says "Missing Operationg System" when I boot  Can you identify the problem from this???

---

### Post by Q007 on 2010-02-20
Well, its not much to go on, but I've recently done the triple boot. I had Mac OS X and Windows 7 via bootcamp. (I used disk utility to add a partition by reducing the Mac partition before I started, but I'm pretty sure I could have used the bootcamp partition as well through the installer).

I suspect you might have installed grub in the MBR instead of in the Ubuntu partition. To change where its installed, you need to click on the 'Advanced' button during the install process. Where is this button? Well, there is a point where you have to decide where you install Ubuntu, and there are a few options like using the slider to resize your bootcamp partition, or wiping everything and installing a smug Ubuntu instead, or going into another screen and setting it up yourself. Probably the 'Advanced' or 'Manual' option. I suspect that is where the magical 'Advanced' button is that has the grub location settings behind it. I was lucky I spotted it actually. Its a very quiet and discreet button IMHO. 

In my case, in the (we'll called it the 'Manual' option) I needed to choose the partition I'd recently made with Mac's disk utility and make it an ext3 format, and Ubuntu just seemed to know that I meant that partition for the Ubuntu install. I didn't make a swap partition because I got scared from another post I saw on triple booting that thought this caused problems.

I would suggest going selecting each option for where to install Ubuntu and have a look, to see what is there before making the decision of where/how to install. 

BUT before you install you must have set that grub will be put in the Ubuntu partition. You have to find that 'Advanced' button and change its install location.

Hope this helps

Q

---

### Post by linuxopjemac on 2010-02-21
Some guy posted a very nice simple manual to triple boot without rEFIt:

[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=60](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=60)

---

