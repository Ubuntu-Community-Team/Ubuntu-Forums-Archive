---
title: "Drive partitioning..."
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by bidget on 2008-04-02
Ok so first off, I HAVE read the tutorials on dual boot installations and I have read a few other forum threads on it as well, I just have a few questions... I'm wanting to set my drive up as follows, 1 partition for windows, 1 partition for ubuntu, 1 large NTFS partition for shared files, 1 partition for home directory, and 1 for the swap partition. I have a 320GB drive, I figured I would make like 40GB for Windows, 60 or so for Linux, I guess the swap partition would be around 4GB, the home directory would get I dunno 15 or so and then a 200GB partition for my other files like music, pictures, video, etc. One thing I am not sure on is if I should make the partition for my home directory the larger ext3 partition, or if I should make the Ubuntu partition the larger... I'm not very familiar with Linux :( All of my applications and such will be installed into the Ubuntu partiton, and not the home directory partition... Right? Also, does it really matter if I install Ubuntu or Windows first? I have all of my files backed up onto an external hard drive so I can format my drive without worrying about loss of files... Just not sure exactly how it should be set up. I apologize if I missed a tutorial on this or if maybe there's another forum post with exactly the same problem so please don't flame me!! :oops: 


Oh and also if anyone thinks maybe I am allocating too much space for the Ubuntu partition then please speak up as I'm not really sure how much space it really  needs :)

---

### Post by AndyCooll on 2008-04-02
> **bidget said:**
> Ok so first off, I HAVE read the tutorials on dual boot installations and I have read a few other forum threads on it as well, I just have a few questions... I'm wanting to set my drive up as follows, 1 partition for windows, 1 partition for ubuntu, 1 large NTFS partition for shared files, 1 partition for home directory, and 1 for the swap partition. I have a 320GB drive, I figured I would make like 40GB for Windows, 60 or so for Linux, I guess the swap partition would be around 4GB, the home directory would get I dunno 15 or so and then a 200GB partition for my other files like music, pictures, video, etc. One thing I am not sure on is if I should make the partition for my home directory the larger ext3 partition, or if I should make the Ubuntu partition the larger... I'm not very familiar with Linux :( All of my applications and such will be installed into the Ubuntu partiton, and not the home directory partition... Right? Also, does it really matter if I install Ubuntu or Windows first? I have all of my files backed up onto an external hard drive so I can format my drive without worrying about loss of files... Just not sure exactly how it should be set up. I apologize if I missed a tutorial on this or if maybe there's another forum post with exactly the same problem so please don't flame me!! :oops: 


Oh and also if anyone thinks maybe I am allocating too much space for the Ubuntu partition then please speak up as I'm not really sure how much space it really  needs :)

Since you're making a separate home directory partition, for the main Linux partition you are unlikely to need more than 10gb, in fact probably more like 5gb.

What goes into your home directory are your personal config files, personal settings etc, documents you create (though it seems you may well be keeping these on a separate partition). Since I keep all my personal files, music, documents etc on my server my actual home directory on my pc itself is only about 1gb in size

:cool:

---

### Post by The Cog on 2008-04-02
You are unlikely to need more than 10G for the Ubuntu sysytem partition. I use slightly more but that's because of Unreal Tournament and UT2004. Certainly no more than 20G. Your home partition is the one that will grow uncontrollably as you donwload all that stuff. Your home directory is like the Documents and Settings directory on Windows. So that needs to be bigger.

---

### Post by bidget on 2008-04-02
Ah I see... So..... When I download and install apps in Ubuntu they are installed into my home directory, and the actual system partition doesn't ever grow in size? Am I right?

---

### Post by mikewhatever on 2008-04-02
> **bidget said:**
> Ah I see... So..... When I download and install apps in Ubuntu they are installed into my home directory, and the actual system partition doesn't ever grow in size? Am I right?

No quite. Only config files are in /home. The applications are usually in the system partition, but you should be safe in making it about 10 - 20 BG. 60 seems way to much. You'll probably never need more then 1-2 BG of swap.

---

### Post by bidget on 2008-04-02
Ok I see... I am planning on installing a few games so I will make the system partition a little bit bigger. Now one more question before I format and start the whole installation process... I am going to be installing Windows first, but I can't make ext3 partitions with the windows xp installation. If I just make the NTFS partitions, and leave the rest unallocated, will I have any problems creating the swap, home directory, and system partitions with the Ubuntu installation cd?


Agh I can't wait until I can finally use something that wasn't made by microsoft :D



**EDIT**

 Oh and I notice that you said I will only need 1-2GB for a swap partition, but I read that it should be around twice the size of my RAM. I have 2GB of RAM so I just automatically assumed that it would need to be double that. But I guess it is unnecessary? I am really not worried so much about performance being an issue, but I am planning on using the beryl interface, and it looks like it would be a bit resource intensive... I saw a video of it on youtube and it looks amazing :)

---

### Post by mikewhatever on 2008-04-02
No, there shouldn't be any problems. In fact, that way is safer, because you do not need to resize partitions, yet, you'll need to manually partition unallocated space.
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by Victormd on 2008-04-02
> **bidget said:**
> 60 or so for Linux, I guess the swap partition would be around 4GB
60GB for Linux... I don't know, I would probably use 15GB(/) and 10GB (home) since you will be using the larger partition for personal files and such. For your swap partition, 4GB is wasted space. You can use ~1GB for your swap.

> **bidget said:**
> Also, does it really matter if I install Ubuntu or Windows first?
Yes, you should install Windows first because Windows will not recognize ubuntu and ruin your boot. So always try to install the OSs in ascending order of "goodness", i.e., Win95>Win98>Win ME> Win XP> Win Vista> Linux!

---

### Post by Victormd on 2008-04-02
> **bidget said:**
> Ok I see... I am planning on installing a few games so I will make the system partition a little bit bigger. Now one more question before I format and start the whole installation process... I am going to be installing Windows first, but I can't make ext3 partitions with the windows xp installation. If I just make the NTFS partitions, and leave the rest unallocated, will I have any problems creating the swap, home directory, and system partitions with the Ubuntu installation cd?
That's probably the best way to go as long as you use manual partitioning during Ubuntu install.

> **bidget said:**
> Agh I can't wait until I can finally use something that wasn't made by microsoft :D
I know EXACTLY how you feel! :)

> **bidget said:**
> Oh and I notice that you said I will only need 1-2GB for a swap partition, but I read that it should be around twice the size of my RAM. I have 2GB of RAM so I just automatically assumed that it would need to be double that. But I guess it is unnecessary?

This is a rule of thumb for windows because it uses swap so much. Ubuntu manages your memory resources much better than windows so 1GB will be fine.

---

### Post by bidget on 2008-04-02
Ok well I'm about to format and get rid of Vista :) If all goes well my next post will be from Ubuntu in a few hours:D


Wish me luck hahahaha

---

### Post by bidget on 2008-04-02
Ok sooooo serious problem... I finally got Windows XP installed (Windows Vista seriously screwed with my boot drive and the xp install wouldn't detect it so I'm using one of my other hard drives), BUT it turns out Ubuntu won't install on my computer. I boot from the cd fine, I choose "Start or install Ubuntu," and then a message pops up, its too fast for me to read the entire thing, but it's something about loading a kernel, 2.6.something... Anyway... after that... nothing happens. My monitor for some reason shuts off, almost like a computer is going into hibernate or standby mode. Then it just sits there. I let it sit for about 10 minutes and nothing happened. Rebooted, tried it again, same thing. Is some of my hardware incompatible maybe? Here are my specs:

AMD Athlon64 X2 5000+ Black Edition
Gigabyte GA-M57SLI-S4
2GB OCZ Plantinum XTC PC2-6400 DDR2-800
320GB Seagate Barracuda 7200RPM SATAII
120GB Seagate Barracuda 7200RPM SATA
80GB Seagate Barracuda 7200RPM SATA
eVGA Geforce 8800GT


Sooo... I don't really know where to go from here haha it just doesn't seem to be working. I have Ubuntu 7.10 if that helps at all. Oh and I also don't have any PCI cards or anything like that, I listed everything above. Help! :'(

---

### Post by bidget on 2008-04-02
Any ideas....??

---

### Post by Victormd on 2008-04-03
Ok. a thought is your graphics card. I have a Geforce 8800GT and had to install using safe graphics mode. Another thing you might want to try, is disconecting all your HDs and leaving only the one you're going to install Windows (or have installed) and Ubuntu, and later, connect them and let ubuntu automount them. But I would try the safe graphics mode first...

BTW, nice setup! :)

---

### Post by bidget on 2008-04-03
Thanks, just put it together in february :D

I didn't even think about safe graphics mode hahaha. I just sort of assumed that it was for lower end graphics cards. I'll remember to try all of the options in case I have any other problems like this again haha. I'll try it out and post results later:)

---

### Post by bidget on 2008-04-03
Tried the safe graphics mode, but still nothing. I'm pretty sure it must be the graphics card though... Because after the screen goes blank, I can still hit ctrl+alt+del to restart the computer... So it's not frozen... I just can't see what's on the screen :( Is there a different version of Ubuntu that would work with this graphics card? Also if it's not the graphics card and someone does know the problem any help is appreciated :)

---

### Post by Victormd on 2008-04-03
I have the same graphics card (XFX though) and Ubuntu Gutsy (7.10) it works fine. You can try to install from the alternate CD (text mode install) or if you're feeling luck, try Hardy (8.04) Beta I've read that it has much better hardware compatibility...

EDIT***
Just occurred to me, did you check the integrity of the CD (from the boot menu)?

---

### Post by Bartender on 2008-04-03
Victor brings up a good point.  How did you create the Ubuntu CD?  Try it in another machine, and see if it gets to the desktop.
Did you -
Burn the .iso at 4X or so?
Use a good quality, name brand CD-R, not CD-RW?

Can you download/burn a GParted Live CD and boot from that?  Try pre-formatting your Linux partition to ext3.

---

### Post by bidget on 2008-04-03
Ok so I got the alternate cd and it works fine. But there's one problem... I get all the way through the installation, and it tells me that its detected 2 copies of windows xp installed (there is only one though). So I tell it to install grub, BUT it install grub onto the wrong hard drive hahaha. I have my drives set up like this:
320GB SATAII is in the first sata connector on my motherboard (I assume that this would be hdd0)
120GB SATA (This is the drive where windows and ubuntu are) in the second connector, and
80GB SATA in the third slot.

Now... if I just open my case and switch the sata connectors going to my 320 and 120gb hard drives, it should fix this problem and grub should be loaded onto the proper drive, correct?

---

### Post by Victormd on 2008-04-03
I'm not sure but you might be right. With SATA drives, I think it will try install the files on the first drive on the chain. You might have been better off trying my previous suggestion, leaving only the HD you were going to use to install the OSs, and after installing Ubuntu, reconnect the other drives (I've heard of a lot of issues installing on multiple SATA drives).

Can you access the grub menu? Because, if so, you can edit the lines and direct the boot to the proper drive...

Also, I think you can download some kind of liveCD grub installer but I'm not sure, this might be my imagination) :D

---

### Post by Victormd on 2008-04-03
Or try this:
[http://ubuntuforums.org/showthread.php?p=4646870#post4646870](http://ubuntuforums.org/showthread.php?p=4646870#post4646870)

---

### Post by bidget on 2008-04-03
I INSTALLED UBUNTU YAAAAYYYY. I just switched the plugs going to each hard drive, problem solved. The weird thing is that I have 2 Windows XP entries in the grub menu... I&#314;l have to see what each of them do later haha. Now on to installing nvidia graphics drivers woo!! :D Thanks for the help everyone!

**EDIT**

Ah and I just realized that maybe Grub thinks that there are 2 windows installations because one of my drives that I THOUGHT was empty actually has ntldr and ntdetect.com in it, I assume that by formatting it and removing those files Grub will realize there is only one Windows installation?

---

### Post by Victormd on 2008-04-03
> **bidget said:**
> I INSTALLED UBUNTU YAAAAYYYY. I just switched the plugs going to each hard drive, problem solved. The weird thing is that I have 2 Windows XP entries in the grub menu... I&#314;l have to see what each of them do later haha. Now on to installing nvidia graphics drivers woo!! :D Thanks for the help everyone! 

Good job, now all you have to do is enjoy... just a tip to install your graphics card, use envy... It's the easiest way to go to get the most up-to-date drivers.

> **bidget said:**
> Ah and I just realized that maybe Grub thinks that there are 2 windows installations because one of my drives that I THOUGHT was empty actually has ntldr and ntdetect.com in it, I assume that by formatting it and removing those files Grub will realize there is only one Windows installation?
Yeah, that will do it. To remove the one of the entries, open the terminal and type
```
sudo gedit /boot/grub/menu.lst
```
and scroll to the end of the file.  There you'll find two instances of your windows and you'll be able to tell for sure what happened. Since you might not know which one to remove, comment them out using # so one of the entries looks like this: 

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Microsoft Windows XP Professional
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1

Restart the computer and try to boot to windows (there should only be one now) and see if it works.  If it does, then you can delete the previous lines, otherwise, uncomment them and comment the other instance of Windows, reboot... again... and see if it works... I think you get the picture...

Good luck and let us know if you need any thing else...

---

### Post by bidget on 2008-04-03
Cool thanks :) For some reason it wont let me install a restricted driver because it&#347; said that it isn´t needed.... I&#314;l figure that out though. Im sure that I can find another forum user thats having the same problem.

---

### Post by Victormd on 2008-04-03
Yeah, that's why you need Envy... :)
Check this out:
[http://ubuntuforums.org/showthread.php?t=734172](http://ubuntuforums.org/showthread.php?t=734172)

---

