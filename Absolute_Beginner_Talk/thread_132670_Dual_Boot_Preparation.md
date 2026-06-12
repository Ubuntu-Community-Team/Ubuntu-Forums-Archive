---
title: "Dual Boot Preparation"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-02-18
I pop my windows xp OS install cd in and want to install to partition using FAT32 so i can install Ubuntu and read and write....but it only gives me NTFS can anyone help me install windows in FAT32 so i can dual boot? And be able to read and write...

---

### Post by cilynx on 2006-02-18
Boot an Ubuntu 5.10 Live CD.  
Run 'gparted'.
Set up the partitions the way you want and be sure to specify the Fat32 partition.
Exit clean.
Reboot.

From here, the Windows installer should recognize the Fat32 partition and ask if you want to install to it.

---

### Post by jasrog on 2006-02-18
that did not work..windows install cd cannot recognize that...any ideas?

---

### Post by cilynx on 2006-02-18
What version of XP?

I have had good luck w/ XP Pro base release and XP Pro SP1

Never tried Home or SP2

---

### Post by jasrog on 2006-02-18
xp pro media center 2005

---

### Post by cilynx on 2006-02-18
My only guess is that Media Center might have dropped support for Fat32.

My best advice would be to try one from the standard series unless you really need the Media Center functions.  Beyond that, you're out of my league...

Any other takers?

---

### Post by prizrak on 2006-02-18
Create more than one partition. Leave about 5 gigs of unpartitioned space on your HDD then install XP on that, make a big FAT32 partition for both OS's to read/write to. I highly doubt that  MCE dropped FAT32 support since most(all?) flash media use it. It's just annoying as far as installing on FAT goes.

---

### Post by carverj on 2006-02-18
Going back a little to Cilynx's post:

regarding:
Boot an Ubuntu 5.10 Live CD. 
Run 'gparted'.
Set up the partitions the way you want and be sure to specify the Fat32 partition.
Exit clean.
Reboot.

I want to install XP on Hda5, without having to reinstall Ubuntu (as I haven't learnt how to re-install GRUB properly), would the gparted partitioner help me to include my Hda1 Linux partition on the boot menu?
If not I have a question regarding VMWare. Could I run XP during a Ubuntu session using VMWare and then install furthur programs (such as Project) during that same VMWare session?
:-k 
Ta in advance ;) 


From here, the Windows installer should recognize the Fat32 partition and ask if you want to install to it.

---

### Post by cilynx on 2006-02-18
The problem w/ installing Windows after Linux is that Windows takes over your bootloader.  After installing Windows, you'll have to rescue-disk your way back into Ubuntu and the reinstall GRUB.

If you're not looking to do heavy graphics work, VMWare could be a very good solution.  In all actuality, VMWare recently released a free version.

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

I've used VMWare for various tasks for years now.  You spawn a virtual machine with VMWare, install XP on that, and then it's just like anything else running XP, just a touch slower.  You can install whatever you want.

Edit:

Oh yeah, the idea posted above to have a Windows partition, a Linux partition, and a shared Fat32 data partition is a really good idea.  That's how I set up all of my dual-boot machines.

---

### Post by unbutuju on 2006-02-18
[QUOTE=cilynx]...and a shared Fat32 data partition is a really good idea.  That's how I set up all of my dual-boot machines.[/QUOTE]

Hi there, I wonder if you could help me on how to make that work, I just reformated one of my ntfs partitions because I want to try that too!

I have 3 partitions, 1 ntfs for winxp, 2 (the reformated one with fat32) and the ubuntu one. I went to the disk manager and I can see all the partitions, and on the now vfat i try to "enable" it but nothing happens!

I started using ubuntu a few weeks ago so any tip would be apreciated!
thanks in advance

---

### Post by cilynx on 2006-02-19
Can you elaborate on "nothing happens"?  Does it say that it enabled it?  Do the buttons not change state?  Does it throw an error?  If you can get around on the command line: "mount /dev/whatever /mnt" will mount it for you.

---

### Post by unbutuju on 2006-02-19
Wow, thats fast... :-) thanks

Well I mean nothing at all :-) nothing realy, no buttons changes no erros no messages absolutly nothing !

havent tryed the terminal , will do it now...
see ya soon!

---

### Post by unbutuju on 2006-02-19
Hi Cilynx, 

well "nada" with the command line, well at least something happened, it says it can't find my hda2 wich is the fat32 partition, and on the X disk manager is there as "Windows virtual fat" vfat, access path (none) and behind "enable" button says Inaccessible!

Once again thanks for ur possible future tip!

---

### Post by cilynx on 2006-02-19
Can you possibly c&p the mount command used as well as the output?

---

### Post by unbutuju on 2006-02-19
> Can you possibly c&p the mount command used as well as the output?
Hi Cilynx

Thanks again for your help, 
I did it, i made amistake at the command, and also not used to the "sudo" :-) i started with redhat into my linux adventure, but i should say this is good to prevent mistakes!

Any way thru the terminal I made it happen, and after that i went to X disk manager and its there now, I wonder how to make it apear now as a disk in "computer" browser, you know like windows... well its late in the ocean i am very exited with ubuntu but have to sleep so I see you tomorrow Thanks again!

---

### Post by carverj on 2006-02-19
hmmm :-k 
No floppy available for the rescue disk option. I do have a USB pen with tom's root boot. Would this enable me to re-install GRUB after the Windows installation? If no, I can always go with the VmWare option. So you say Programs can be installed on XP as usual ay ? :-D

---

### Post by cilynx on 2006-02-19
By "rescue disk", I mean "anything that can possibly boot you into Linux".  If you know what you're doing, you can even use the Ubuntu Install CD.  You need to get Linux up and running, then run the GRUB installer to put it back on the MBR.  Don't worry if you accidently make it so you can't boot Windows, you can edit your GRUB config and add it back once you've booted into your Linux system.

As for VMWare / XP, yes, it's just like running it directly on your computer.  The speed isn't even too bad on a modern machine.  The only downside is that the faux graphics card isn't all that great, so you can't play most games.  However, for productivity work, it's great.

---

### Post by cjm5229 on 2006-02-19
Hi, Here are a couple of very good Howto's for you. one is on dual booting, [http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")
The other on mounting your Windows partitions. [http://www.psychocats.net/linux/mountwindows.php]("http://www.psychocats.net/linux/mountwindows.php")
The first one is by Herman, the second one is by Aisus, If you follw these guys around the forum, as well as Arnieboy, it will really speed up your learning curve in Ubuntu. Good Luck.

---

### Post by unbutuju on 2006-02-19
Hi cilynx, here is what i was doing (stupidly) !

I was trying to enable the vfat partiton on the x disks manager without mentioning any mount path :oops: 

So now I am trying to figure out how to enable that disk everytime i login ubuntu and if possible to make a virtual access thru "Places > Computer" as a hard drive icon!

see u around ant tnx for ur atention!

---

