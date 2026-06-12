---
title: "Make a file and print server"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by movrshakr on 2007-07-26
How hard will it be to convert a machine now running XP to ubuntu -- and have it share a folder to the local network so that other Windows machines can read and write and create sub-folders?

Also, I need for the ubuntu machine to share a parallel port Samsung ML-1210 printer to the network for all other computers to print to.

It is essential that it do these two things.  There will not be anyone using the machine as a day to day desktop, but perhaps occasional at the machine use.

I have minimal dabble experience with linux.

---

### Post by FleetAdmiral74 on 2007-07-26
In order to share the folders with XP, the easiest way is to create a seperate partition formatted as something like FAT32, that xp can recognize. It does not play nicely with ext3...not that it can't just extra software to install. But I would not want XP w/ access to my OS partition.

---

### Post by splintercellguy on 2007-07-26
You can install NTFS-3G to access NTFS partitions: sudo apt-get install ntfs-config
On Windows, for ext3 access, you can install a filesystem driver: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Orochi on 2007-07-26
You don't need to create a separate partition or worry about ext3/ntfs compatability if you're just sharing across the network and not between local drives. You just need to install Samba (Windows) file sharing which is incredibly easy to do in my experience (just right click on a folder and choose sharing and choose Windows/Samba sharing. it automatically downloads whatever software you need for it the first time you share something).

I don't know about sharing printers, but I assume it's just as easy as sharing folders. A more pressing concern is checking to make sure there are Linux printer drivers for your printer model.

---

### Post by movrshakr on 2007-07-26
OK, you are going to have to bear with me here, but I don't understand all of that.  

It is essential that the Windows machines on the network be able to "work with" the documents stored in the shared folder on the converted ubuntu machine.  They were originally created in XP or Vista on NTFS file system.  My intent is to convert the current storage machine to ubuntu, put the folders/files in a shared folder, and have the other network machines continue work with them just as they did when the storage machine was running under XP.

Were you saying ubuntu needs to be in one partition and the shared folder in another partition?  FAT?  They are now NTFS??????

---

### Post by FleetAdmiral74 on 2007-07-26
> **movrshakr said:**
> 

Were you saying ubuntu needs to be in one partition and the shared folder in another partition?  FAT?  They are now NTFS??????


Yes...I think. Ubuntu will probably be installed on an ext3 partition, and then you can just use gParted to make anther one FAT32 and it should show up for XP. WIthout extra software (mentioned by a poster above), Xp will only see the fat32.

---

### Post by civic_si on 2007-07-26
> **Orochi said:**
> You don't need to create a separate partition or worry about ext3/ntfs compatability if you're just sharing across the network and not between local drives. You just need to install Samba (Windows) file sharing which is incredibly easy to do in my experience (just right click on a folder and choose sharing and choose Windows/Samba sharing. it automatically downloads whatever software you need for it the first time you share something).

I don't know about sharing printers, but I assume it's just as easy as sharing folders. A more pressing concern is checking to make sure there are Linux printer drivers for your printer model.

I agree follow the suggestions here there is no need to partition the drive and worry with file systems. I booted to the live cd and the printer driver for the Samsung ML-1210 is in the list of available printer drivers so it should work just fine.

---

### Post by Orochi on 2007-07-26
The storage machine is going to be all Ubuntu right? Not a dual boot? You want to get rid of XP on it and install Ubuntu right? If so, then what you want to do is copy all the files off that machine to a backup drive (NTFS or FAT32 formatted). Then reformat the machine as ext3 and install Ubuntu. You can then copy the files back onto the Ubuntu machine and share them over the network with Samba. If you don't have a secondary drive to move the files too, you can instead shrink the current drive's partition and install Ubuntu to the free space making a new ext3 partition (effectively giving you a dual boot machine).

---

### Post by jd65pl on 2007-07-26
No need to format as FAT or NTFS, that is complete misinformation. you can serve the files to your windows machines with samba ([wiki]("http://en.wikipedia.org/wiki/Samba_%28software%29")).
See [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server") on installing samba and [this]("http://doc.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html") on configuring samba.

---

### Post by movrshakr on 2007-07-26
Ok, great information coming back here!  Let's see how much of it I understand...

1.  Whether machine is to be ALL ubuntu or not is a little open--but probably it will be.  But I could put a second partition on that machine (how?) (if enough room...I think there is), format it ext3 (how?), and install ubuntu in that?

2.  Yes, I have an external USB drive I can store the current files on.  Will ubuntu see that?

3.  If I did choose to create a second partition for ubuntu (how?), could it share to the network the file documents directory that would be over in the other XP NTFS partition?  Windows machines connect to a "share name."  Will ubuntu provide the share name over the net?  Will the XP machines "see" the share (is it advertised)?  Actually, that is not critical so long as they will connect properly to it if I can enter it for example as \\ubuntumachine\sharename  to attach M: to.

4.  Good to hear the ML-1210 is supported.  At some point, probably will need discussion as to steps to actually share the printer.  For now, I just need to know for certain that can be done in a way that the XP/Vista machines on the network will be able to print to it.  Don't need details now--just confidence that if I go this route it can be done.

Sorry for all this, but it =is= the Absolute Beginner forum!

---

### Post by obrient on 2007-07-26
You shouldn't worry about partitioning* at all*. Take that right out of the mix.

> You just need to install Samba (Windows) file sharing which is incredibly easy to do in my experience (just right click on a folder and choose sharing and choose Windows/Samba sharing. it automatically downloads whatever software you need for it the first time you share something).


As said before make sure that your printer works with Ubuntu. That would be the major concern. You will be using Samba to share the printer as well.

---

### Post by movrshakr on 2007-07-26
"As said before make sure that your printer works with Ubuntu. That would be the major concern."

And HOW do I do that =before= going with a non-partitioned, ubuntu-only disk (wiping out my working XP install)?  If it is not to be partitioned, I HAVE TO BE SURE this is going to work before starting the conversion.  You say, "make sure it works"  Yep, that is exactly what I am trying to do here with this discussion.  Telling me to make sure it works is telling me to ask these questions, which I am already doing.

Someone else said the ML-1210 printer driver is in ubuntu.  That's encouraging, but is it as far as I need to go?    What about whether it is sharable?  Being printable from the ubuntu machine is not the major issue--I need printer to be attached to the ubuntu machine, but being printable from all the other Windows machines is the must-work component.

---

### Post by civic_si on 2007-07-27
I booted to the live CD yesterday when you first asked the question. The printer driver was there... I even searched for the printer and it shows that it is compatible with Red Hat 6.1 Linux. So there should be new drivers for that in Ubuntu.

---

### Post by obrient on 2007-07-27
To make sure it works boot the live CD and print a test page with the printer.

---

### Post by movrshakr on 2007-07-27
I do intend to do that, but first have to figure out how to SHARE the printer onto the network.  That is the critical part, assuming that ubuntu will work with it--which seems probable.  Point is, I need to not only print from the machine to which it will be attached, but more importantly, from the other Windows machines on the network.  That is a part I do not know how to set up in ubuntu.

---

### Post by obrient on 2007-07-28
You will need to set up Samba and CUPS. Samba is a file and print sharing utility for Linux. It will let you share folders and/or printers. The basics would be to install the Samba Server on the machine. Turn on CUPS and use the wizard to configure it to print using Samba. You should be able to do it without any problems. There is a lot of documentation here as well as in the [Ubuntu wiki.]("http://wiki.ubuntu.com")

---

### Post by movrshakr on 2008-04-14
It is 9 months later and I just found a link to this in a folder I was keeping while trying to do the setup discussed in the preceding posts.

To update, I did convert the machine totally to ubuntu.  There was quite a bit of effort involved in setting up samba...learning about how to get a folder shared, setting it so all could work with it, and so on. eventually, I was successful--mostly.  The other machines on the network can store files there and work with them quite well.  I still have a problem trying to work at the ubuntu machine with files other machines have stored there.  Typically, I have to do a chown on the files before I can work with them at the ubuntu.  That is annoying, since I enter 'sudo gedit foobar' and still can't work with them until chown.

I got a new Samsung SCX-4725FN printer, and it is network connected at a router, rather than direct attached to the ubuntu machine.  Installing it to be able to print to it from ubuntu was another great (for me) challenge.  The linux package from Samsung did NOT make it usable after install.  I was finally able to determine the files that were needed and where to put them--after much effort.  Can now print, but it was not a smooth transition.  Had to install cups and configure it as well.

So, it is done.  It is successful.  But it was not easy.  Many days and nights involved.

---

