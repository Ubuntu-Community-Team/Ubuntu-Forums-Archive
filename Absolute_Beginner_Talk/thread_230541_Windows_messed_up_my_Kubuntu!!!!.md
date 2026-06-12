---
title: "Windows messed up my Kubuntu!!!!"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-08-06
Hmmm..... I wanted some files from my downstairs computer so I used a crossover cable and created a small network. That buggered up my wireless connection when I disconnected the crossover cable (when I used the wireless repair function it said 'Windows cannot clear the ARP cache'). I fixed that by restoring my settings to default, but now my wireless in Kubuntu won't work, it doesn't connect! I tried setting the file sharing permissions to 'not allowed' in Kcontrol, but it won't let me change them, even in administrator mode - the area stays 'grayed out'!!!
Help!
Thanks!

---

### Post by bscbrit on 2006-08-06
I think that I will need some more details before I can even begin to suggest what happened.  Which computer is your Windows installed on, which one did you transfer files from, how did you do it, what settings did you change to enable your mini network, why couldn't you simply use the wireless network to move the files?  Where is your wireless access point?

Windows cannot even see a linux partition usually, let alone write to one or change its contents.  Now you might have installed an ext3 driver for use under Windows but, unless you have, it is most unlikely that it will have changed the contents of your kubuntu installation.  There may be a hardware error (network cards misconfigured?) or you may have corrupted your hard drive by switching off the power during a 'write' but, other than that, you should be able to recover to a working system.

So, more details please...

---

### Post by tartarian on 2006-08-06
Sorry, I should have been more specific. I created the network using the Windows wizard 'create a new connection' and selecting advanced connections>connect directly to another computer. I then transfered the files using a shared folder. I couldn't do it via my wireless connection because we're with Wanadoo, who provided us with a wireless router built into the package (aka a livebox). Unfortunatly, the livebox doesn't support home networking so (unless I overlooked something) I cant do it by that. Yes, windows could write to my Kubuntu installation because I installed the ext2/ext3 drivers (3 hard drive partitions - windows, kubuntu, files) so It could have happened. My internet worked before I did that network thing, but I've managed to fix it on Windows by setting network settings back to default...

---

### Post by bscbrit on 2006-08-06
You might not be the only person having problems with the LiveBox:

[http://labs.pcw.co.uk/2005/03/wheres_the_cust.html](http://labs.pcw.co.uk/2005/03/wheres_the_cust.html)

[http://www.webuser.co.uk/forums/showflat.php/Cat/0/Number/200314/an/0/page/3](http://www.webuser.co.uk/forums/showflat.php/Cat/0/Number/200314/an/0/page/3)

Anyway, the short answer for the future is that you can use wireless and network at the same time using LiveBox but it is not easy unless you know a bit about networking in general.

As for getting it working again - did you have a backup of your working installation - No, I thought not but it is always worth asking.  When we get it working again the first task is to BACK IT UP!

I'm not a Kubuntu user so you will have to tell me exactly what error conditions and messages you are seeing.  Why were you trying to change file permissions to get the LiveBox to work, and which file was it?

Can you boot back into Windows and give me the output of IPCONFIG in a DOS window?  That should tell us some of the working values that we need.  Then we can try to reproduce them in Kubuntu and get the link up and running again.

---

### Post by tartarian on 2006-08-06
I wasn't trying to change filesin Kubuntu. I had a working internet in kubuntu, went over to windows to get those files, then went back to kubuntu and found I didn't have an internet connection. 

I don't have any error messages to post. In Kubuntu there's this cool little app that connects to the network (a bit like the wireless network connection in windows). So it just says connection failed. I tried re-inputting the WEP key, and putting the IP, gateway, etc etc in (there's a wizard to do it with). 

The output in DOS is :
```

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Oliver>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.1.24
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1

```

Btw, I can live without a home network, I'll just wait untill my year is up and then change ISP's

Thanks for all your help!

---

### Post by bscbrit on 2006-08-06
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

OK, I recommend that you go back into Windows - which is where you are now presumably, otherwise you will not be able to read this - and download the link.  If you have a thumbdrive / usb memory drive / flashdrive or whatever you call it, copy the guide onto it otherwise you are stuck with printing it out or saving it onto a floppy.
Go back into Kubuntu and start following the guide.  It can be tempting to miss some of the earlier stages out and jump to where you 'think' the problem might be but I would strongly advise against it.  When you come to the bit that doesn't do what the guide says it should you have probably found your [first] error.  If you can fix it, then so much the better, but if not then come back and I'll try to overcome that particular problem.
Good Luck!

---

### Post by tartarian on 2006-08-06
Hey! thanks for the help.... got there in the end.... needed to manually put in my access point physical address (sudo iwconfig ra1 ap .....)
Thanks for the help!

Just out of interest.... you mentioned backing up my internet settings... how would I do that?

---

### Post by bscbrit on 2006-08-07
Great - I'm glad that you've solved your problem!

There are many different strategies for backing up your data.  Search the forums if you want to learn about the subject in detail and see what others recommend.

The easiest method involves making a copy of /etc/hosts, /etc/dhcp3, /etc/dhcp3.conf, /etc/network, /etc/networks etc

or simply make a compressed tar of the /etc directory

tar -cvzf ~/mybackup.tar /etc

It is simple at a later date to extract a few files to see what has changed, or even to restore the /etc to exactly what it is now.

There are a few gotchas - if you restore everything then you not only fix your problem but might undo loads of improvements that you have made since making the backup.  Hint - if you change the contents of /etc make a new backup!

---

### Post by bscbrit on 2006-08-07
And please don't take my next comment the wrong way :)  but it is _unlikely_ that 'Windows messed up my Kubunut'.  It is probably true that changing the network configuration resulted in the network becoming unusable under Kubuntu, but that is not quite the same thing.

Linux will play very well alongside Windows, although the latter does sometimes decide that it is the only operating system in the world and so completely remove any references to Linux by deleting your grub/lilo configuration.  But it is extremely rare for an action in Windows to corrupt a single file or some item of data.  However, by installing the ext3 drivers you have made such an event much more likely.  Please take care. :-D :-D

---

### Post by tartarian on 2006-08-08
Thanks for the advice!! I've got a 'backup' of my /etc directory now incase it does happen again! Ok, that is probably what happened, and windows didn't mess up my kubuntu, but it seemed like a dramatic title ;) I need the ext3 drivers tho, so I can access my files, but I will be careful! Thanks!

---

### Post by bscbrit on 2006-08-08
A safer way, if slightly less convenient method, when using files in both Windows and Ubuntu is to have a shared partition called, say, "data", and formatted as FAT32.  Both operating systems can read this format and you access it whenever you want.  But it prevents Windows from be able to write to your linux partitions.  After all, if a Windows program runs wild, it is unlikely to respect access privileges and could - in theory at least - delete critical files.  The linux kernel can prevent many accidents of this nature but, if you are using Windows to access your linux partitions then there is nothing between you and disaster other than taking care!

Good Luck and see you around the Forum.

---

