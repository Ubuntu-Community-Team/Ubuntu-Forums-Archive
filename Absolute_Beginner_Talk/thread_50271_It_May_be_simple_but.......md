---
title: "It May be simple but......"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by alandlynn on 2005-07-19
I have a 450 Ghz Processor, 256 Mb Ram, Windoze ME.
C is partitioned at 32GB for Operating system and where I store my programs.  It has another partition with 4GB, labelled E and empty at the moment.  This is where I intend to put Linux
D is a 40 GB spare Hard Drve where I store all my files.

I now have a file called: kubuntu-6.04-install-i386.iso on my desktop.

I have no idea what to do next.  How do I make **kubuntu-6.04-install-i386.iso** into an operating system?  So far I've burned this and a Knoppix? file to CD ROM but my computer will not even recognise that I have a disk in the drive when the burning process is completed.

I have looked in the search facility but cannot find anything quite this basic.
Thanks for your help.
Al

---

### Post by kvidell on 2005-07-19
[QUOTE=alandlynn]I have a 450 Ghz Processor, 256 Mb Ram, Windoze ME.
C is partitioned at 32GB for Operating system and where I store my programs.  It has another partition with 4GB, labelled E and empty at the moment.  This is where I intend to put Linux
D is a 40 GB spare Hard Drve where I store all my files.

I now have a file called: kubuntu-6.04-install-i386.iso on my desktop.

I have no idea what to do next.  How do I make **kubuntu-6.04-install-i386.iso** into an operating system?  So far I've burned this and a Knoppix? file to CD ROM but my computer will not even recognise that I have a disk in the drive when the burning process is completed.

I have looked in the search facility but cannot find anything quite this basic.
Thanks for your help.
Al[/QUOTE]
 Use your favourite CD Burning utility and burn it to a CD Rom, making sure that it will be bootable.
I like Nero, a lot of people like Roxio.

Next you put the CD Rom in your drive and reboot.
- Kev

---

### Post by alandlynn on 2005-07-19
[QUOTE=kvidell]Use your favourite CD Burning utility and burn it to a CD Rom, making sure that it will be bootable.
I like Nero, a lot of people like Roxio.

Next you put the CD Rom in your drive and reboot.
- Kev[/QUOTE]
 Hi Kev, 
Thanks for your advice, but, I did burn the file to CD using Nero.  Now, neither my CDRW or my CD/ DVD ROM drives even recognise that there is a disk in the drive.
I have tried to set my computer as bootable by CD ROM by chancing settings in CMOS, but cannot seem to get this function to work either.
Sorry to be so incapable.
Thanks in advance,
Al

---

### Post by kvidell on 2005-07-19
[QUOTE=alandlynn]Hi Kev, 
Thanks for your advice, but, I did burn the file to CD using Nero.  Now, neither my CDRW or my CD/ DVD ROM drives even recognise that there is a disk in the drive.
I have tried to set my computer as bootable by CD ROM by chancing settings in CMOS, but cannot seem to get this function to work either.
Sorry to be so incapable.
Thanks in advance,
Al[/QUOTE]
Did you chose "Burn CD Image" or did you burn a Data CD and add the ISO as a "piece" of the data to be burnt?
There's a massive difference :)
- Kev

---

### Post by poofyhairguy on 2005-07-19
YOu want this guide:

[https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28iso%29](https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28iso%29)

---

### Post by alandlynn on 2005-07-19
[QUOTE=kvidell]Did you chose "Burn CD Image" or did you burn a Data CD and add the ISO as a "piece" of the data to be burnt?
There's a massive difference :)
- Kev[/QUOTE]

Iguess my biggest mistake so far was burning an ISO1 File.  I'll try Again with a CD Image.
Thanks.
Al  :)

---

### Post by Kvark on 2005-07-19
Remove the E partition to free up space for a linux partition.

Tell the installer to use the free space. Make sure you don't tell it to use the whole hard disk!

---

### Post by alandlynn on 2005-07-19
[QUOTE=Kvark]Remove the E partition to free up space for a linux partition.

Tell the installer to use the free space. Make sure you don't tell it to use the whole hard disk![/QUOTE]

I've tried all configuration of boot sequence in my seetings, and still can't get my computer to boot from the CD ROM.

How do I remove E:?  Can I just tell windows to delete it?

Thanks for the help so far.
Al

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=alandlynn]I've tried all configuration of boot sequence in my seetings, and still can't get my computer to boot from the CD ROM.
l[/QUOTE]

Will it boot from a Windows install or recovery CD?

---

### Post by gammyhand on 2005-07-20
[QUOTE=alandlynn]I have a 450 **Ghz** Processor, 256 Mb Ram, Windoze ME.[/QUOTE]

Man, 256mb must be a serious bottleneck to that processor! ;)

---

### Post by Phixion on 2005-07-20
Choose "burn image" in Nero, burn the .iso to the dvd / cd and choose to boot from cd, reboot with cd / dvd in, voilla! :)

---

### Post by alandlynn on 2005-07-20
[QUOTE=poofyhairguy]Will it boot from a Windows install or recovery CD?[/QUOTE]

No; like I said, I've set the BIOS / CMOS sttings at every option available but it still won't boot from CD ROM.

Can I try booting from a Windows Recovery, floppy disk and access anything from there?  If so what do I need to do to make the system recognise the possibility of booting from 2 Operating Systems?

Sorry to be so incapable.
Al  :smile:

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=alandlynn]No; like I said, I've set the BIOS / CMOS sttings at every option available but it still won't boot from CD ROM.
[/QUOTE]

Damn...try to upgrade your motherboard bios in Windows. That sounds like a defencitve bios.

If you can't boot from a cd...I don't know how to get Ubuntu on....

---

