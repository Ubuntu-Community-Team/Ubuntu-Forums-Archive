---
title: "Limit of Wireless Support?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by 322 on 2006-06-26
I've yet to make the switch to Ubuntu (limited hard drive space, will be buying a new one soon), but I've been toying with some simpler distros such as Puppy and I was wondering what the limitations of wireless internet support are for Ubuntu. I know Puppy has some limited support, and it's quite complicated to get it running, but I would like to know what Ubuntu has to offer. I have a Linksys Wireless-G PCI adapter, and so far I can't get it to work with Puppy. Will I fare any better with Ubuntu.

---

### Post by Jagot on 2006-06-26
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by DarthMandeep on 2006-06-26
Chances are good that if there is no native driver for your card, you'll still be able to get it up and running using ndiswrapper.

---

### Post by jpkotta on 2006-06-26
You can try the running the Live CD and see if it works.

---

### Post by 322 on 2006-06-26
Thanks for the link, Jagot. 

jpkotta: Do I need to create a FAT32 partition to run the LiveCD? Because right now all I have is just one NTFS partition.

---

### Post by 322 on 2006-06-27
Alright, I just ran the live CD and it recognized the connection, but it says it's not configured. The information it needs is: network name, key type, WEP key, IP address, subnet mask, and gateway address. Where do I find all of this?

More noob questions: I have Windows and all its excess on my single 80gb hard drive, one NTFS partition. If I choose to install Ubuntu alongside Windows, will 8gb of hard drive space be enough to do it? Because Windows and all of my documents is using up 72/80gb of my hard drive.

---

### Post by Apple 101 on 2006-06-27
8 GB is not enough for Ubuntu as you need hard disk space for the / partition, /home partition (optional, but recommended), and swap partition.

---

### Post by fridayxiii on 2006-06-27
[QUOTE=322]Alright, I just ran the live CD and it recognized the connection, but it says it's not configured. The information it needs is: network name, key type, WEP key, IP address, subnet mask, and gateway address. Where do I find all of this?
[/QUOTE]
This info comes from your router config.  I have a D-Link wireless router w/a browser-based interface for configuration.  Open that interface for your router you should find all the specs there.  Only thing you might not find, and need to reset, might be the WEP key.

---

### Post by 322 on 2006-06-27
[QUOTE=fridayxiii]This info comes from your router config.  I have a D-Link wireless router w/a browser-based interface for configuration.  Open that interface for your router you should find all the specs there.  Only thing you might not find, and need to reset, might be the WEP key.[/QUOTE]

Yeah, I just had to go into Windows and run "ipconfig /all" in cmd to find all of the information except for the WEP key. How do I reset it in Ubuntu? I've found a script to set a WEP key, but it told me that there was one already set. I wasn't the one that set up my home network, my cousin did it for me.

---

### Post by SteveHoffmanUK on 2006-06-27
Either ask your cousin if he printed out the wireless network configuration details (Windows XP wireless setup wizard has a built-in step for doing this) when he set up the network. If he did and left it somewhere, find it -- it will have the WEP key printed there.

If not you'll have to log into your router using your web browser (see instructions that came with the router for the exact address, username and password to use), and it should have a facility for setting the WEP code. Set it and then input it into the Ubuntu networking setup program (System, Administration, Networking, Wireless connection, Activate) and you should be OK.

---

### Post by djsroknrol on 2006-06-27
> 8 GB is not enough for Ubuntu as you need hard disk space for the / partition, /home partition (optional, but recommended), and swap partition.

That's not entirely true..I've run Breezy & Dapper on 8 GB. Not the most roomiest place to call home, but it does work...I would suggest alot more...I've expanded my partition to 13GB just recently

---

### Post by az on 2006-06-27
[QUOTE=Apple 101]8 GB is not enough for Ubuntu as you need hard disk space for the / partition, /home partition (optional, but recommended), and swap partition.[/QUOTE]
Actually, you need 2 gigs for the install.  If you just want to play around, give yourself three or four gigs.  Eight gigs should be fine.  Now, if you download things left and right and will fill up your drive fast, that is a differnet story.  It depends on what you do.

Never mind about complex partitioning - you won't need it - just use the default partitioning the installer does for you.

All you have to tell the installer is the new size you are going to want your old partition to be( Example: 72 Gigs)  Done.  Simple.  Don't worry.

---

