---
title: "Moving my mother to Ubuntu Live from XP"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Stuperfied on 2006-04-28
Hi, I am about to go to my mothers house to move her to Ubuntu Live from XP at her request. A few concerns I have are accessing the NTFS file system and support for her dial up modem. I will be taking her all the way accross to the full install adventually but I want to leave XP there just incase she cant handle it.

She has 2 partitions of 10 and 30 gig roughly as I recall, both NTFS. The smaller one is for the OS. The modem is most likely a software one. Can anyone tell me how to interface with the NTFS file system and connect her to the internet?

---

### Post by iball on 2006-04-28
Linux currently can read NTFS but writing to it is a bit buggy.  If you can, try to create a FAT32 partition for her documents.  FAT32 can be read and written to by both Linux and Windows.  

Go to [www.linmodems.org](www.linmodems.org) and see if your modem is listed there.  If not, you may need to get an external modem.  They aren't expensive, but will be able to be used by Linux.

I hope this helps
--Ian

PS: My mum uses Ubuntu Breezy and loves it :)

---

### Post by yager on 2006-04-28
Wow, I hope your mom loves you alot.  You can play around with accessing the NTFS partitions from the live disk but you have to issue the commands to mount them directly.  I did this on my dad's laptop as a demonstration.  If your mom is really good with computers then you could leave here detailed instructions with all of the Terminal commands to make this happen.  I only had to do this manually once for my dad as he decided that he did not need the access after all and could live on the Live CD with no need to access Windows until he was ready.

I suggest that you burn the DVD version of the Live disk as this will cut way down on the number of files that she will have to download when time comes to install if all she has is a modem.  You may want to hook it to an ethernet port when you do the deed and set her up for dual boot or wipe Windows all together.

As for the modem.  No clue....

---

### Post by gr0kzer0 on 2006-04-29
It's a bit difficult to give authoritative advice on the modem as you didn't give any details other than it's probably a winmodem.

The best thing to do, probably, is download scanModem. That will look over your system and tell you which (if any) drivers you need and where to get them from. There's a thread about doing this over on the Hardware-Networking forum.

---

### Post by Stuperfied on 2006-04-29
Identifying the modem was the least of my problems, im a bit of a tech head under windows but when it comes to linux, im lost. I went back to windows, downloaded the linux drivers for the modem (hsfmodem-7.47.00.00full-1.i386.rpm.zip) put them on a floppy disk and went back to linux to install them. Needless to say, im back in windows talking to you again because I cant access the floppy drive. So firstly, how do I access the floppy drive to install the drivers?

What I would like to do is have all this on a floppy disk for her as a script she can run after boot. Idealy, it would mount the NTFS drive, then retrieve the modem drivers off the NTFS disk and install the modem. Then it would setup her internet connection and LAN so my sister can get online from her computer. Then it would install her printer. This should all be done by default, I dont know what the developers were thinking, how is a noob supposed to make the switch if they cant even access their disk or the net?

Anyway, if someone can help me get access to her floppy drive, get the driver installed, access the net, mount her NTFS and then make a start on that floppy disk, that would be great, thanks.

---

### Post by Stuperfied on 2006-04-29
Good news, I am now talking to you from my mothers computer under Ubuntu. Got some bad news too though, the second I turn off the computer, all these changes will be lost.

Ok, so I can get my mother to enter the simple instructions to mount the floppy drive but I need to create a script on a floppy disk that will:
Create directory /media/hda1
Mount NTFS hda1 /media/hda1
Create directory /media/hda5
Mount NTFS hda5 /media/hda5
Unzip /media/hda5/temp/hsfmodem_7.47.00.00full_k2.6.12_9_386_ubuntu_i386.deb.zip to /home/ubuntu/

The next part is a little complicated so I hope there is someone up to the challenge. I used dpkg -i [filename].deb to install the driver and this was the output complete with prompts.

```
ubuntu@ubuntu:~$ sudo dpkg -i /home/ubuntu/hsfmodem_7.47.00.00full_k2.6.12_9_386_ubuntu_i386.deb
Selecting previously deselected package hsfmodem.
(Reading database ... 56801 files and directories currently installed.)
Unpacking hsfmodem (from .../hsfmodem_7.47.00.00full_k2.6.12_9_386_ubuntu_i386.deb) ...
Setting up hsfmodem (7.47.00.00full_k2.6.12_9_386_ubuntu) ...
Conexant HSF softmodem driver, version 7.47.00.00full

If you need license keys, assistance or more information, please go to:
        http://www.linuxant.com/

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

Pre-built driver modules that seem compatible with your system were found under
/usr/lib/hsfmodem/modules/binaries/linux-2.6.12-9-386.
Would you like to use them? [yes]

Unable to determine region, defaulting to "USA"

Please enter region name for modem unit 0 [USA]: Australia

Setting region for modem unit 0: "AUSTRALIA"

To change, use "hsfconfig --region" or "AT+GCI=<T35code>"
The current region can be displayed by entering "ATI9" in a terminal program.

Note: we respect user privacy. Email addresses are not communicated
nor used for any purpose other than to manage licenses!

Please enter your email address [unknown]: vera.hurt@gmail.com

License keys can be obtained from http://www.linuxant.com/
Without one, the modem operates in FREE mode (max 14.4Kbps data only, no fax)

The registration ID for modem unit 0 is: 9597-69BB-4644

Please enter license key [FREE]:

Setting license for modem unit 0: "vera.hurt@gmail.com/FREE"

Note: kernel module snd-via82xx-modem overridden by hsfmc97via
Note: kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati

Current parameters: ("hsfconfig --info")

Config for modem unit 0: /dev/ttySHSF0
        Device instance: 0-PCI-14f1:2f00-14f1:2004
        HW revision    : Basic2 2.18 Standard DAA 3VoltsIA
        HW profile name: hsfpcibasic2hsfi
        Registration ID: 9597-69BB-4644
        License owner  : vera.hurt@gmail.com
        License key    : FREE
        License status : FREE (max 14.4kbps data only)
        Current region : AUSTRALIA (T.35 code: 0009)

The /dev/modem alias (symlink) points to ttySHSF0

To enable full 56K modem and FAX functionality, enter your license information
with "hsfconfig --license".

License owner and key data must EXACTLY match the information respectively
provided to and by Linuxant. Otherwise, license status will remain "FREE"!

ubuntu@ubuntu:~$
```

It will have to pass the responses to it automatically and then when finished, will have to configure the modem with my mothers connection information so she can connect. Then it will have to configure the network so my sister (on WinXP) can connect through my mothers computer to the internet.

Can anyone help me with this please? Also if there are any developers present, I appologise about my previous statements, im really just glad to even have an alternative to Microsoft. It just gets frustrating when you dont know what you are doing, my mothers phone bill will be huge with the amount of times I had to switch back and forth dialing in again to get more info when I hit a wall, lol.

---

### Post by Stuperfied on 2006-04-29
Well im back home again and theorising, doing a little behind the scene's as it were.

Ok, ive tried to make a start on the shell script but I dont know if ive made any mistakes. I dont know if I can just pass arguments to the dpkg command simply by tacking them onto the end seperated by spaces but I have put it like that to at least symbolise what I want to happen.

```
#!/bin/sh
sudo mkdir /media/hda1
sudo mount /dev/hda1 -t vfat -o iocharset=utf8,umask=000 /media/hda1
sudo mkdir /media/hda5
sudo mount /dev/hda5 -t vfat -o iocharset=utf8,umask=000 /media/hda5
sudo unzip /media/hda5/temp/hsfmodem_7.47.00.00full_k2.6.12_9_386_ubuntu_i386.deb.zip -d /home/ubuntu/
sudo dpkg -i /home/ubuntu/hsfmodem_7.47.00.00full_k2.6.12_9_386_ubuntu_i386.deb y Australia vera.hurt@gmail.com FREE

```
Under Knoppix, maybe I could pass commands to netcardconfig but under ubuntu, I wouldnt have the faintest idea about how to go about setting up the LAN from the console, let allone from a shell script. I think I will need some help with that one, also with configuring the dial up connection with her connection details.

Any help would be appreciated.

---

### Post by Stuperfied on 2006-04-29
Whoops, those file systems should be NTFS but then I dont know how to handle NTFS file systems yet so I will have to get someone to show me that one too.

---

### Post by Joey French on 2006-04-29
It seems that if you want to keep the XP partition on your mother's computer along with trying Ubuntu, much less effort could go into just dual booting-  especially since you will be rebooting the box between live sessions. Why not just defragment XP, resize the win partition, then install ubuntu on a small partition? Especially since you know now that the modem can be made to work under Ubuntu? Not trying to mess up your plans, just deems that there is a much easier way, and less confusing for your Mom as well.

---

### Post by Stuperfied on 2006-04-29
Well, when I wanted to experiment with resizing partitions about 2 years ago, I couldnt find any free programs that would do it and I was told by many of my knowledgable peers that in most cases it makes a drive unsatble and in some cases unreadable at best. I would rather not take that kind of chance with my mothers hard drive.

This topic seems to be getting a little long in the tooth, I might start a new one.

---

### Post by catlett on 2006-04-29
Dual booting hasn't made any of my drives unstable and most people start by dual booting. Data is data. Your drive doesn't really care what data it is. It will have a partition  with one data and another partition with other data. It just accesses when commanded. Use the 30gig for Ubuntu. It is already there.The install will give you the option to use it, and that's it. A bootloader will be installed to allow you the choice of OS. When you pick an operating system the partition with the OS's files on it  will be accessed. How does this make a drive unstable? Are you saying that having partitions with different data on them makes a hard drive unstable?
Make sure you're "saving current setup" when shutting down your computer so changes will be saved.(This applies to an installed system,I don't know if it affects live cds. my assumption would be no)
This is a link for ext2 (and can be used for ext3) drivers. Which will allow you to see linux partitions that are formatted ext2 and ext3, in windows.[http://www.fs-driver.org/](http://www.fs-driver.org/)
Here is a link for accessing NTFS from ubuntru with read and write access. It is a forum thread with the process an Ubuntu user used to access ntfs.[http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)

To check the make up of your drive, you can use disk management in windows or you can run the partitioner in Ubuntu live. It can partition your drive but it will also give you a picture of your drive. You can start the program and then get a look at the makeup without doing anything to the drive. The program is "gparted" it is in the "applications" at the top of the screen. applications<system tools<gparted.
You can aprtition with this or a trial version of Partition Magic from CNET Downloads but the install can do it all. If you do have a 30 gig seperate from a 10gig with XP on it, the install can use that to install Ubuntu on.

If you are still a little concerned just make sure you have a backup of her XP install. If you don't have a program, CNET download has hundreds of free or 30day free trial software programs. You can always download a freeware or trial backup program to make the backup. Then your covered.

---

### Post by iball on 2006-05-01
Is there any reason why you can't reinstall Windows?  Then you can repartition the harddrve, install Windows to the 1st primary partition, install Ubuntu next (to any partition other than Windows) and let Ubuntu install its boot loader to the MBR.  You will be able to dual boot Windows and Ubuntu then with no problem, and you can make all your settings permanent.

--Ian

---

### Post by Stuperfied on 2006-05-04
For 1, this is something that it doesnt appear is available so maybe its time someone did it. 2, im almost finished and to re-install her entire computer is not feasable at this point so this is the quick fix till a more suitable time can be found. 3, im really interested in seeing if we can actually get this done. 4, a lot of live CD users can really benefit from this if it works. 5 why not do it?

---

