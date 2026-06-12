---
title: "Netgear SC101"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-11-19
Hello all,
I just purchased a Netgear SC101 for my Linux-only network. I've got it put together, but I can't communicate with the goofy thing. They didn't bother to tell what the default IP address is for this device. Worse, I'm starting to see threads that indicate that it doesn't work with Linux. Does anybody have guidance on this one? I can't even figure out how to connect to it.

---

### Post by Pumalite on 2007-11-19
This might be relevant (not sure):
[http://ubuntuforums.org/showthread.php?t=87480](http://ubuntuforums.org/showthread.php?t=87480)

---

### Post by gn2 on 2007-11-19
AFAIK it will not work with Linux. 
I have been looking for just such a device and have my heart set on a Linksys NSLU-2 which I will treat myself to over Xmas.
During my research I specifically looked at the Netgear SC101, as I have a Netgear Router and am very happy with it.
All the info i could find was that the SC101 just doesn't do Linux.

---

### Post by gantww on 2007-11-19
Ok,
It looks like it's going to have to go back to CompUSA. I can't believe they made this crap proprietary - looks like they could have saved some R&D effort by just licensing some lightweight Linux variant for this. I'll check out the NSLU-2.

---

### Post by gantww on 2007-11-19
On the NSLU-2, I have a few questions:
1) Can I configure it solely from a web interface or do I have to install some windows-only crap to get it running?
2) Does it use a standard harddrive format? In other words, if the device goes bad and the drive is still good, could I move the drive to another machine to get the data off?

Thanks,
Will

---

### Post by gn2 on 2007-11-19
> **gantww said:**
> 
1) Can I configure it solely from a web interface or do I have to install some windows-only crap to get it running?
2) Does it use a standard harddrive format? In other words, if the device goes bad and the drive is still good, could I move the drive to another machine to get the data off?


1) Yes.

2) Yes, ext3 by default, possible to run other file systems. (XP can read ext3 by adding free driver)

[http://tinyurl.com/b22gt](http://tinyurl.com/b22gt)
[http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)
[http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)

---

### Post by mikeincal on 2007-11-28
I have been able to make the SC101 work in Ubuntu 7.10. I went to the following web page  [http://code.google.com/p/sc101-nbd/]("http://code.google.com/p/sc101-nbd/") , and proceeded to download the debian package. I highly suggest both of the "how to guides", I found the quick start guide to be of most benefit to me. Apparently there are a few caveats to take note of:

1. I was only able to connect to previously made partitions from the Windows world. It seems that the file structure was changed from the proprietary Zetera format to a  linux format.

2. With that being said, it seems that you cannot use this partition to bridge between Ubuntu and Windows, the partition becomes either/or. The partition was dropped immediately from a second computer running XP, yet would still show up in SCM. 

3. If the partition has a password associated with it in the SCM manger in Windows, it will not connect in linux. Simply resetting the password option in SCM worked for me. SCM did not work for me in Ubuntu, seems Windows has some use.

4. The created partition does not show up as a physical drive, but as a folder in the root of my file system called "mount". After a review of the outcome, it seems relatively simply to name it whatever you like and put it where you please. I followed the quick start guide very closely. 

5. The folder mnt was created with an owner of root, once this was changed back to me, everything worked for me. I moved about a gig worth of files back and forth with no problems at all. 

Please note that this program was found on google, and I assume there may be risks involved since it is not part of the Ubuntu community files. 

Best of luck.

---

### Post by gantww on 2007-11-29
I ended up getting a linksys network storage system (it's the one with two SATA bays and two USB ports). I had it set up in less than half an hour, including shares, network address, and security. It is a bit slow (maybe because I'm hitting the shares as windows shares...?), but other than that, I have absolutely no complaints on this thing. It's like night and day when comparing the ease of use between this and the netgear box I had.

Now if I can just get the stupid print server I bought along with it to work, it'll be totally awesome.

---

### Post by ginestre on 2007-12-22
> **gantww said:**
>  Now if I can just get the stupid print server I bought along with it to work, it'll be totally awesome.

Just in case you haven't- I got my stupid print server to work under CUPS after six months without being able to print a single thing, by the simple expedient of changing the protocol prefix from http: to sockets: (I found this suggestion after months of other experiments, and god knows how much  searching the web, I forget where) but leaving all of the other settings in the stupid print server unchanged. Works like a dream.  Hope that helps. Now I'm off to try out my new NSLU2.

---

### Post by magicfab on 2008-06-13
Works fine in Hardy for me with the nbd module. mikeincal is correct in his comments. Also see:
[http://ubuntuforums.org/showpost.php?p=4151832&postcount=15](http://ubuntuforums.org/showpost.php?p=4151832&postcount=15)

If you'd like to know if/when this makes it into Ubuntu, please subscribe to this bug:
[https://bugs.edge.launchpad.net/ubuntu/+bug/213744](https://bugs.edge.launchpad.net/ubuntu/+bug/213744)

Cheers,

---

### Post by magicfab on 2008-06-13
Works fine in Hardy for me with the nbd module. mikeincal is correct in his comments. Also see:
[http://ubuntuforums.org/showpost.php?p=4151832&postcount=15](http://ubuntuforums.org/showpost.php?p=4151832&postcount=15)

If you'd like to know if/when this makes it into Ubuntu, please subscribe to this bug:
[https://bugs.edge.launchpad.net/ubuntu/+bug/213744](https://bugs.edge.launchpad.net/ubuntu/+bug/213744)

Cheers,

---

### Post by vlandi on 2008-07-03
I bought it a while ago and it so far is absolutely the worst piece of crap I ever had. I returned it the next day.
It can't even be named as a SAN or NAS. Guys at netgear seems to get the approach of reinventing the wheel. Instead of just putting a few chips with web server + CIFS + FTP they introduced non-documented protocols (that btw don't work sometimes). Another win-only device not compatible with any standards.

Piece of junk. Scrap it and buy a proper storage device. (even cheap Chineese ones have more options and work better than this).

---

