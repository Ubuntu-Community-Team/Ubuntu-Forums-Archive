---
title: "Big installation issues--gasping for air here."
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by deNoobius on 2005-11-19
My Linux install has pretty much been a bust.  I am trying to track down the documentation on my issues, but it's getting frustrating.  So I thought I'd see if I could shortcut the process and save myself some aggravation by appealing to those wiser than myself for ideas.  Here are my two main issues:

1.  I can't load the printer driver for my Samsung laser CLP 510N.  Samsung does provide Linux drivers.  I downloaded the driver for i386 (the other option is PPC.  I'm using Ubuntu on an old intel PC).  The installation instructions are:


 1) Login as root
2) Download and Extract the driver.
# tar xzf DownloadedFileName ( .....tar.gz)
3) Execute Installation Program.
# ./cdroot/Linux/install.sh
4) Select and click your model and click "Install"

As you can imagine, I'm stuck at the first step.  I've tried using sudo and getting a temporary root password as per suggestions here, but no matter what, I get the following error:

Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

(I'm sure I'm in the right file in terminal--I should cd to the same one where I've downloaded the driver, right? The name is right, I just cut-and-pasted it, also double and triple-checked it).

I need this computer to work with the printer, because my whole home network prints (or printed) through it.  

2.  I was afraid of this happening--GRUB does not list Windows as one of the boot options.  Assuming I can rescue the Windows partition, can I then edit the bootloader, or do I have to reinstall yet again from the ground up?

All right, those are the two main ones, I've been up since 6:00 am working on the printer, but I have no clue what to do about Windows other than use the rescue disk to reboot windows.  But how can I then edit the bootloader so it works properly?  Or do I have to reformat and reinstall again?

Thanks.

---

### Post by campusloop on 2005-11-19
[QUOTE=deNoobius]My Linux install has pretty much been a bust.  I am trying to track down the documentation on my issues, but it's getting frustrating.  So I thought I'd see if I could shortcut the process and save myself some aggravation by appealing to those wiser than myself for ideas.  Here are my two main issues:

1.  I can't load the printer driver for my Samsung laser CLP 510N.  Samsung does provide Linux drivers.  I downloaded the driver for i386 (the other option is PPC.  I'm using Ubuntu on an old intel PC).  The installation instructions are:


 1) Login as root
2) Download and Extract the driver.
# tar xzf DownloadedFileName ( .....tar.gz)
3) Execute Installation Program.
# ./cdroot/Linux/install.sh
4) Select and click your model and click "Install"

As you can imagine, I'm stuck at the first step.  I've tried using sudo and getting a temporary root password as per suggestions here, but no matter what, I get the following error:

Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

(I'm sure I'm in the right file in terminal--I should cd to the same one where I've downloaded the driver, right? The name is right, I just cut-and-pasted it, also double and triple-checked it).

I need this computer to work with the printer, because my whole home network prints (or printed) through it.

2.  I was afraid of this happening--GRUB does not list Windows as one of the boot options.  Assuming I can rescue the Windows partition, can I then edit the bootloader, or do I have to reinstall yet again from the ground up?

All right, those are the two main ones, I've been up since 6:00 am working on the printer, but I have no clue what to do about Windows other than use the rescue disk to reboot windows.  But how can I then edit the bootloader so it works properly?  Or do I have to reformat and reinstall again?

Thanks.[/QUOTE]

1. tar is definitely not able to find the file. there could be no other explanation. so just make sure that you enter the name correctly - if the filename has spaces in between just cut and paste of filename in terminal won't work to be extra sure enclose the filename in double quotes like 
```
tar zxf "Downloaded file.tar.gz"
```

2. there is no need to reinstall grub ( the bootloader ). you can edit its configuration file to include windows in the boot menu. the configuration file is /boot/grub/menu.lst. A typical entry for adding windows to the boot menu would look something like this
 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

the above piece shows that the first partition of master hard disk contains windows. The above code can be appended to /etc/grub/menu.lst with appropriate modifications regarding where windows is installed.

Hope this helps.

---

### Post by cstudent on 2005-11-19
I don't have the expertise to help you with #2, but I don't think you're tanked. I think it's possible to recover.

As for #1, you would download the tar file. Open the terminal and navigate to the directory the file is installed. Use the tar command to unpack the archive. *Then* you would use sudo to run the install file. 

It also might be possible the tar file is corrupted. Did you try downloading a new copy?

Bill

---

### Post by deNoobius on 2005-11-19
Thanks very much Campusloop (this is on the boot loader issue)!  I changed the ownership of the /boot/grub/menu.lst file to me, made the edit (in point of fact, windows is at the very begnning of the first partition of the first hd, so it is literally as you stated) , changed the ownership back to root, rebooted, and now I do get Windows as an option in the bootloader and it works. 

Now on to the printer issue.

---

### Post by steve.horsley on 2005-11-19
[QUOTE=deNoobius]Thanks.  Just to make sure I understand--do I edit the /boot/grub/menu.lst file, or created a "grub" folder in /etc/ and add a revised menu.lst file there?
[/QUOTE]

You edit the file /boot/grub/menu.lst, and add the lines for windows (in the code box below). The thing that worries me is that the installer didn't add it automatically - you didn't opt to use the whole disk (deleting windows) when you installed Ubuntu did you?

The code below assumes that windows is on the first partition, known as hda1 in Linux or (hd0,0) in Grub. For the second partition instead, this would be hda2 and (hd0,1).

 
```

title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by steve.horsley on 2005-11-19
As an afterthought - you can look and see what partitions are there with the command ```
sudo fdisk -l
``` post this here if you are unsure of its meaning

---

### Post by deNoobius on 2005-11-19
I will say that both the boot loader and Ubuntu are *V E R Y  S  L O W* to load up...and as Ubuntu loads I get a series of messages that say "hdd:  drive not ready for command."  I think maybe I did something with my partitions that Ubuntu doesn't like.  Has anyone see this error?  Any tips for speeding up the boot process?

---

### Post by campusloop on 2005-11-19
It usually happens when the partition has not been unmounted properly ( usually happens when the system crashes). the drive not ready error could most probably be related to dma. 

if it was an error because the partition was not unounted cleanly it will automatically be fixed when the next time you reboot.

---

### Post by deNoobius on 2005-11-19
Steve, Campus, thanks, I did call up the partition table as you suggested.  Unfortunately, I do understand the table.   It may explain some of my issues, like losing Windows (I got it back, thanks); possibly my installation problems; and definitely my "hdd-drive not ready" messages and long boot up time.  I don't know how this happened, but my second and third logical partitions are in reverse physical order on the hard disk.

Here are the gory details:

/dev/hda1   *           1        3836    30812638+   7  HPFS/NTFS
/dev/hda3            6440        9964    28314562+   f  W95 Ext'd (LBA)
/dev/hda4            3837        6439    20908597+  83  Linux

I'm omitting the remainder of the partition table, because the rest of it doesn't have this problem.  Don't ask me what happened to hda2.

I don't know exactly how this happened, but I did partition once with qparted, ran into some trouble, then repartitioned with Partition Magic and somehow I think during that process I got things flipped around.  The odd thing is that everything seemed to be in correct order in the displays in both those partition utilities, but clearly they are not.

So, here's the new question--is this the kind of thing that can be fixed, or do I just have to live with it?  Can Ubuntu be somehow made to "know" what the actual physical order of the partitions is?  Should I start over again?

---

### Post by deNoobius on 2005-11-19
OK--this is on the printer.  It does not appear that my printer will work in Ubuntu at all.  (Samsung CLP 510N) I've tried EVERYTHING.  I've untarred, run the setup program, over and over.  I've used the Linux driver that came on my install CD.  I've put the files on my desktop, in a directory.  I've tried running it from the terminal and from the file icon itself.  No matter what, it throws up some kind of error in the terminal but it only stays up for a nanosecond before it closes, so I haven't been able to read it.

Unless there's some workaround--maybe a generic color laser driver that works under CUPS or something--I won't be able to use my laser printer, and, unfortunately, that means I'm going back to Windows.  Does anyone know of a workaround for a color laser printer?

---

### Post by rjwood on 2005-11-19
what you may want to try is uninstalling the printer, turning off the power to the printer, removing the connection from the comp to the printer then shutting down for a couple of minutes. Reconnect the printer-turn it on and then restart your computer then maybe it will read. this has worked for alot of other people.

---

### Post by deNoobius on 2005-11-19
Thanks for the suggestion, but no dice.  

If anyone has figured out how to get a Samsung CLP 510N to work in Ubuntu, please respond!

Thanks.

---

### Post by campusloop on 2005-11-19
Have a look here - [http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-CLP-500](http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-CLP-500)

---

### Post by campusloop on 2005-11-19
[QUOTE=deNoobius]Steve, Campus, thanks, I did call up the partition table as you suggested.  Unfortunately, I do understand the table.   It may explain some of my issues, like losing Windows (I got it back, thanks); possibly my installation problems; and definitely my "hdd-drive not ready" messages and long boot up time.  I don't know how this happened, but my second and third logical partitions are in reverse physical order on the hard disk.

Here are the gory details:

/dev/hda1   *           1        3836    30812638+   7  HPFS/NTFS
/dev/hda3            6440        9964    28314562+   f  W95 Ext'd (LBA)
/dev/hda4            3837        6439    20908597+  83  Linux

I'm omitting the remainder of the partition table, because the rest of it doesn't have this problem.  Don't ask me what happened to hda2.

I don't know exactly how this happened, but I did partition once with qparted, ran into some trouble, then repartitioned with Partition Magic and somehow I think during that process I got things flipped around.  The odd thing is that everything seemed to be in correct order in the displays in both those partition utilities, but clearly they are not.

So, here's the new question--is this the kind of thing that can be fixed, or do I just have to live with it?  Can Ubuntu be somehow made to "know" what the actual physical order of the partitions is?  Should I start over again?[/QUOTE]

this could be normal .. for example /dev/hda1 and /dev/hda3 could be primary partitions and the rest logical partitions.

---

### Post by deNoobius on 2005-11-19
Yeah, but look at the addressing on the disk--it doesn't make sense.  It's not just the numerical order, but the start and end points.  But, maybe you're right.  

In any case, I appreciate the reference to the printer (rated a "paperweight," aaargh!) but it appears that no one using Ubuntu has been successful, although one person using Debian claims to have been.  When I have another free afternoon I'll try some of the recommendations on that page.  In the meantime, I'm just trying a bunch of different laser printer drivers via the system menu on the off chance that one of them might work.  No luck so far.

I think the hdd error that I keep getting, and which is making the bootup take so long (16 minutes or so!!!),  is a broken CD drive.  I'm going to try physically removing it from the system and see if that error goes away.

---

### Post by deNoobius on 2005-11-19
OK, I was right about the hdd error.  I've removed the problem CD drive, and the boot process is normal and the boot time is down to less than 2 minutes, including the boot loader.  That is very acceptable for this computer, which is an older machine.

That means that my main issue now is getting the printer to work.  I'm receptive to any ideas.  It is clear that the Samsung-provided linux driver is not working.

---

