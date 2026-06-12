---
title: "ndiswrapper"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by FrustratedGuy on 2006-08-31
OK, I'm a long-time Windows expert and I've installed Kubuntu on my second hard drive. :)

Problem is, I could probably make a million posts on this forum for beginners. Now, first thing I want to do is get my Internet connection up and running. Easy, right? No...

See, I have a Linksys Wireless Adapter. The drivers that I have for it only work on Windows. No Linux support whatsoever. Obviously, since my PC isn't even close to the router this presents a problem. However, I used Adept to install ndiswrapper. I know that it's a platform for using Windows apps on Linux and that's about all I know. I have two major questions:

1. I have downloaded the latest driver for my adapter, and it's sitting on my Windows desktop. How do I get this .exe file onto my Linux drive? I've tried my flash drive, but Kubuntu won't recognize the format. (Actually, how the heck to I get *any* files onto the Linux partition?)

2. Once the driver is on the Linux partition, how do I use ndiswrapper to install it? Or if that's not what it does, how do I install this thing?

Right now the Setup Wizard and all files associated with the setup are in a seperate folder on my Windows desktop. (It was a WinZip exe file that I extracted to my desktop.)

---

### Post by Bachstelze on 2006-08-31
[Here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) you go :)

---

### Post by benfindlay on 2006-08-31
Your best bet is to reformat the flash drive as FAT or FAT32 if possible. As far as I know FAT is the only filesystem that is readable from and writable to in all major OSs.

Another possibility is that kubuntu has mounted your windws partition as a drive, probably under /mnt/hda1 or /mnt/hdb1. If this is the case then you should just be able to browse through and copy it off, as you can still read from ntfs.

The third possibility I can think of is to install ext2fs onto your windows partition. This will allow windows to recognise your linux partition and read from and write to it. Try going to [http://e2fsprogs.sourceforge.net/ext2.html]("http://e2fsprogs.sourceforge.net/ext2.html") for more info.

As for how ndiswrapper works, sorry mate, no idea! The only time I've used it was under SuSE, and it just worked without any configuration needed! However, if you installed ndiswrapper via Synaptic Package Manager, if you find it in Synaptic, you can right click on the package and choose properties. In here you can find out where it installed files to, and see if you can find a config file or anything else that might look useful!

Hope this helps!

---

### Post by FrustratedGuy on 2006-08-31
Thanks for the replies. I'm a bit busy right now, but I'll do what's outlined in the tutorial, once I get a chance. :)

Oh, I should also point out that I have two seperate hard drives - Windows is on one physical drive, Linux is on another. But it'll still apply, I'm sure. Though I may just reformat my Flash Drive. :)

EDIT: My flash drive is already FAT32. I'll try FAT, but if that doesn't work I'll check out Ext2fs. ;)

---

### Post by benfindlay on 2006-08-31
Yes it should work fine. If you used the partition manager during your ubuntu install it should have automatically mounted the windows drive *somewhere* ;)

This means you can read from it, so just copy any files you need onto your ubuntu hard drive then you can edit all you want! ;)

Hope this helps!

---

### Post by FrustratedGuy on 2006-08-31
I hate to say it, but I can't. Every time I try to copy something over, I get errors.

Windows XP is my *first* OS, on a 200 GB Maxtor. Linux is on a separate 60 GB Maxtor. Now, I used Ext2fs to temporarily mount D: (my Linux drive) onto a H: drive. I was able to copy it to Kubuntu and when I booted Linux it was there. However, attempting to do anything with it gives me read/write errors.

I'm thinking that I should just use a CD-RW as the mediary between these two OS's... for now, anyway.

See, Linux can only *see* a small portion of C:, my Windows drive. Using that program I downloaded to mount D: in a way that Windows can read, I am able to access these scant few folders. I thought that putting the driver in that folder would allow me to move the stuff off that area to wherever I chose. Maybe I was incorrect.

Yes, I remember in an earlier attempt at Kubuntu that CD-RW's worked. Maybe I can use that to copy over the driver, and/or give back the error messages I've been getting. Be back later...

---

### Post by FrustratedGuy on 2006-08-31
Hello again,

I got ndiswrapper to work, but now I'm having trouble with the driver. I'll go take it up with the Linksys board guys, since it's a specific problem. But at least I got ndiswrapper to work. :)

EDIT: When I try to put ndis.tar.gz on hd1 (windows) I get this:

[img]http://img169.imageshack.us/img169/8742/erroroz8.png[/img]

I *can* use my floppy. However, that is no consolation if anything's 1.45 MB or larger... :-/

---

### Post by benfindlay on 2006-09-01
Yeah, you can't write to ntfs based drives. Well, if we're being strictly honest, you can by installing various programs so I've heard, but it's apparently really buggy and crashes a lot. Your best bet is to install the ext2fs stuff into windows which will allow you to assign drive letters to your linux partition and read/write all you want!

---

### Post by FrustratedGuy on 2006-09-01
Okay, I just used

ndiswrapper -l

to test my installed driver and it said

> rt2500
invalid driver!

I'm sure I got the right driver, and I followed the instructions given... did I mess up? Google isn't revealing much.

---

### Post by benfindlay on 2006-09-01
If theres an option to allow linux to sort the driver I'd use that. Seems to me it's trying to use a ralink driver, which I believe are very generic drivers. If your card is based on PRISM chipset then linux shouldn't have a problem running it.

---

### Post by benfindlay on 2006-09-01
theres a pretty good looking guide here: [http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto]("http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto")

Hopefully that will give you some more insight!

---

### Post by FrustratedGuy on 2006-09-01
OK... I'm not sure I understand that tutorial, but I can try it out... (after all, I just installed Kubuntu a few days ago, so no clue about most of this).

Thanks, I'll report back.

---

