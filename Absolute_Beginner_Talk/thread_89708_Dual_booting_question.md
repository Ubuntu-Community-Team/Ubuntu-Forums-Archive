---
title: "Dual booting question"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by wilford on 2005-11-13
Hello, im going to dual boot my PC with linux and Windows XP. Cuz i wanna try out linux. But i have a question, can i uninstall the OS linux without disrupting anything in my Windows XP? 

Thanks :D Any reply would be greatly appreciated.:D

---

### Post by salva on 2005-11-13
Well... if you have enought unpartitioned space to install Ubuntu on it should be no problem. Either format a partition you dont use or use partitionMagic to resize an existing one.
Then just plop in the Ubuntu cd and install... it should autodetect that you have a windows partition and set up to dual boot.... then ejoy getting to know Linux.

If by chance it turns out you dont like it ( o.O ), its just a matter of booting back to windows and deleting the partition/s, then all should be back to normal...... ;)

---

### Post by wilford on 2005-11-13
ok. thanks. btw, about partitionMagic, is dat a downloadable app? Because right now, i dont have a free partition. I use both my partitioned drives and im thinking of making another.. thanks again :D

---

### Post by salva on 2005-11-13
Partition Magic is Paid for Application. Unfortunately
As far as i remember WinXp has some similar functionality buried somewhere.
But any way of accomplishing free partition space will do.. Have fun ;)

---

### Post by VJ42 on 2005-11-13
[QUOTE=salva]Partition Magic is Paid for Application. Unfortunately
As far as i remember WinXp has some similar functionality buried somewhere.
But any way of accomplishing free partition space will do.. Have fun ;)[/QUOTE]
IIRC you have to boot from the Win XP CD to use its partition tool.

---

### Post by aysiu on 2005-11-13
> **wilford]Hello, im going to dual boot my PC with linux and Windows XP. Cuz i wanna try out linux. But i have a question, can i uninstall the OS linux without disrupting anything in my Windows XP?[/QUOTE] You can, but you'll need the Windows install disk and some kind of partitioning utility to erase the Linux partition, extend the Windows partition, and restore the MBR. Luckily, Microsoft has provided [url=http://support.microsoft.com/default.aspx?scid=kb said:**
> documentation [/url] for this.

[quote]about partitionMagic, is dat a downloadable app? Because right now, i dont have a free partition. I use both my partitioned drives and im thinking of making another.. thanks again Partition Magic is supposed to be great, but you pay for it. Ubuntu's installer has its own partitioning tool. Read [this tutorial on setting up a dual-boot](http://users.bigpond.net.au/hermanzone/). You won't regret it.

By the way, Ubuntu has [a live CD](http://us.releases.ubuntu.com/releases/5.10/ubuntu-5.10-live-i386.iso)--you can try it out without hurting your hard drive. Why don't you see if it's something you really want to install? If it isn't, you didn't just go through the whole trouble of repartitioning and installing an OS. It runs completely off the CD itself and your computer's RAM.

---

### Post by wilford on 2005-11-13
wow. thanks a lot. this will surely help. thanks all of you man. :D Il post the results or if i ever do have any more problems. :D

---

### Post by wilford on 2005-11-14
[QUOTE=aysiu]By the way, Ubuntu has [a live CD](http://us.releases.ubuntu.com/releases/5.10/ubuntu-5.10-live-i386.iso)--you can try it out without hurting your hard drive. Why don't you see if it's something you really want to install? If it isn't, you didn't just go through the whole trouble of repartitioning and installing an OS. It runs completely off the CD itself and your computer's RAM.[/QUOTE]
Sorry for double posting but you can check the date and its not spamming:D 

aysiu, i read the tutorial and documentation and i'm ok on uninstalling linux. but about the live cd. I didn't check it out back at home. I just checked it out now, in school. I'm using the school computer right now and when i clicked the live cd link, it downloads something. Of course i canceled it because this is not my computer.
Now, observing your message, you said that when i run the live cd, it will not install ubuntu on my pc. But why the download? Will it just download it the run it so il be able to see and have a feel of linux? 
-sorry I'm really a n00b :D thanks

---

### Post by throntax on 2005-11-14
hey WIlford! the live cd is a bootable disk! which means you have to have it in the cd drive when the computer boots up. it will then read the cd, if the bios of the computer is set to boot from cd, that is ;). If it isn't, i assume you can set it to boot from cdrom before harddisk in the bios menu at boot time ( usually by pressing the 'del' button or control-c or something) BE CAREFUL! Bios is not something you should mess with on someone else's computer, so probably save it for your own one...
hope you have fun with linux and ubuntu!

---

### Post by throntax on 2005-11-14
oh yeah oops! just re-read your message, a little closer this time ;) ... you were almost about to download the .iso image of the bootable live cd, which you would then need to burn to a cd, using nero-whatever, THEN ( and only then..) would you be able to boot from the bootable disc. does school have good bandwidth and a burner? maybe they wouldn't mind... ;)

---

### Post by wilford on 2005-11-15
[QUOTE=throntax]hey WIlford! the live cd is a bootable disk! which means you have to have it in the cd drive when the computer boots up. it will then read the cd, if the bios of the computer is set to boot from cd, that is ;). If it isn't, i assume you can set it to boot from cdrom before harddisk in the bios menu at boot time ( usually by pressing the 'del' button or control-c or something) [/QUOTE]
Ok, i get it. but how do i do that? :confused: 
Can you give me a link on a tutorial involving configuration on bios? thanx :D

---

