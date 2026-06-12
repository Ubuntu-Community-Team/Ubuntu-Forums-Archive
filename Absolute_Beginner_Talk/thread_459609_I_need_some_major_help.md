---
title: "I need some major help"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by michael08 on 2007-05-30
Ok, so I installed Ubuntu as a dual boot with windows XP.
Everything worked for about a day.

Then all of a sudden, I tried booting up XP and it said Disc Read Error. Restart bla bla bla.

So I booted Ubuntu again and I can't even open up the hard drive or anything.
Now, I got my XP disc to boot from it and install XP again, and after it says "System is checking your hardware stuff"

Then it just goes black and stays black. I can't run the install XP from Ubuntu and now I have no idea what to do.

Any help?

---

### Post by daimaru on 2007-05-30
:confused: what what what ???
u tried reinstalling windows xp , formating the whole disk etc;-  partition time 2 and u can't install it?
that would most likly mean that ur harddisk or ram  is screwed. but maybe not plz give more info.

ps:
i dont quite get what u mean with "I can't run the install XP from Ubuntu and now I have no idea what to do."
have you reinstalled winxp and it does not work?

---

### Post by NICU on 2007-05-30
I would first suggest using the Ubuntu LiveCD (if you can) and backing up everything you need.  After that, I would suggest booting back into Ubuntu (hard drive install) and giving us information on your hard drive partitions and file systems - where is Ubuntu installed, where is XP installed, what file systems are on each?  From there you should be able to mount all your partitions.

---

### Post by michael08 on 2007-05-31
Well... I'm not quite sure what you guys are asking for, but this is what I got.

I have Ubuntu and XP installed.

They both worked fine for a few days. Then, all of a sudden, when I chose to boot xp, it just said, "Disk read error occured. Crt+ALT+DEL to restart. Then It brings me to the boot menu.

Ubuntu can boot from the hardrive fine, with no problems.... but I can't get into my hardrive from Ubuntu. It just says "Sorry, couldn't display all contents."

It doesn't show anything.

I can't boot XP from the disc, and when I am running Ubuntu, The XP disc doesnt run or anything. 

I'm not sure how else I can help

---

### Post by NICU on 2007-05-31
Ok I have a few more questions - when you say Ubuntu can't open the hard drive - what are you trying to open?  Can you view files in your Ubuntu partition?  Can you browse your home directory and create/view/edit files?  

You can see the tutorials here for how to mount a Windows partition - [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions)  I would suggest mounting your Windows partition and backing up any data that you need.  

My next question - how did you want to go about fixing the Windows install?  Did you want to reinstall Windows XP?  Here is another great tutorial on how to install/reinstall Windows XP when you already have Ubuntu installed - [http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp](http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp)  Instead of changing your Ubuntu partition you can just use the existing Windows partition (if you don't mind reformatting and losing everything on the Windows partition that you haven't backed up)

---

### Post by michael08 on 2007-05-31
I can download, create and edit files in Ubuntu. But the drive that is on the desktop won't open.

And now, after that tutorial you sent, it isn't even there. So I really don't know what to do now haha.

---

### Post by NICU on 2007-05-31
> And now, after that tutorial you sent, it isn't even there. So I really don't know what to do now haha.:(

Ok, could you ever mount the Windows partition using the NTFS Configuration Utility?  The last step is to unmount it, so if you could mount it, then unmounted it, you can remount it using the NTFS Config Utility.  How much progress did you make into mounting the NTFS drive?

Do you need to back anything up from you Windows partition, or can you just reformat the partition (losing everything on that partition) and attempt to reinstall?

---

### Post by michael08 on 2007-05-31
Well, I don't really mind losing everything. It's just music (which I still have on my zune) and programs that I can just download again.

What I am gonna do is just reinstall Ubuntu using the whole hard drive, then get a version of XP.

I mean, I have a paid for, not-pirated copy of windows XP cd, but I can't boot from it or anything. I wish I knew what was wrong so i could fix it.

---

### Post by michael08 on 2007-05-31
Oh, and I installed the NTFS thing, And i checked the enable write for internal device. It gave me some error saying I should download something like ntfsfix or something like that. After that message, the drive disapeared, and now I can't mount anything. The drive just isn't present anymore.

---

