---
title: "Please keep me right before I go any further"
date: 2006-06-08
forum: Apple PPC Users
---

### Post by rshd301 on 2006-06-08
OK, I have a Powerbook G4 running OSX but I am considering installing Ubuntu onto it. I have a few questions (newbie type) before I proceed....
(1) Can I make an image of my OSX apps in case I want to go back ? I have a few apps which were downloaded and fro which I don't have CD's to reinstall with.
(2) Can I dual boot with OSX so as to avoid (1) ? This would be my preferred option but as yet havn't come across any posts detailing the procedure.
(3) Will the Ubuntu installer take care of all the usual formatting etc ?
(4) If I do return to OSX, will the install disk from Apple reformat to suit itself ?

Thanks in advance to anyone who can assist.

---

### Post by swartzfeger on 2006-06-08
> **rshd301](1) Can I make an image of my OSX apps in case I want to go back ? I have a few apps which were downloaded and fro which I don't have CD's to reinstall with.[/QUOTE]

Should be ok for most apps, but some programs do have critical preference, .plist and other support files that may be buried in your system folder

> (2) Can I dual boot with OSX so as to avoid (1) ? This would be my preferred option but as yet havn't come across any posts detailing the procedure.

Yes, you can dual boot, with big caveats in regard to 6.06. I insalled 
6.06 close to a dozen times before I finally got a bootable system said:**
> (3) Will the Ubuntu installer take care of all the usual formatting etc ?

The one thing you *will* have to do is create a small bootloader HFS+ partition, since the 6.06 gui installer seems to have problems creating one. Once your bootloader/yaboot partition is created, 6.06 can handle creating the root and swap partitions.

> (4) If I do return to OSX, will the install disk from Apple reformat to suit itself ?

Yes, you can boot from the 10.3/10.4 disk can reinitialize and install with no problem.

---

### Post by rshd301 on 2006-06-08
I don't suppose you have links to pages giving further details on the dual boot scenario ?

---

### Post by swartzfeger on 2006-06-08
[QUOTE=rshd301]I don't suppose you have links to pages giving further details on the dual boot scenario ?[/QUOTE]

Not specifically, no -- I did a lot of searches/research here, and asked a lot of questions. :)

Basically, you need to:

1. clear as much space as possible from Powerbook HD

2. boot from OS X CD

3. defrag disk to make a large contiguous free area of drive to partition

4. using Disk Utility, create 2 partitions: 1 as large as possible (ie, 40GB), the other 4MB and name it 'newworldmac' (no quotes)

5. the large partition will be the main partition Ubuntu will use for root and swap; newworldmac will be the bootloader/yaboot partition

6. shutdown, then reboot from Ubuntu 6.06 CD and install

7. pray

---

### Post by je m'ennuie on 2006-06-08
Have a look at this breezy "How to"
[http://www.ubuntuforums.org/showthread.php?t=89960](http://www.ubuntuforums.org/showthread.php?t=89960)
 to make free space for Ubuntu on your HD without reinstalling OSX

---

### Post by scalvin on 2006-06-09
I have a Powerbook 1.67mhz, 15-inch. I have a 200gb backup drive so I was able to duplicate my HD to it, wipe the HD then partition for OSX leaving a large free space of 5GB. Restored my OSX from the backup drive, using Super Duper. Then I installed Dapper using "free space" option. By holding down the opt key when booting I can go into the OF selector screen and boot into linux or osx.

What doesn't work for me are my airport extreme, bluetooth mouse and keyboard and iMic sound. Bluetooth workaround is to "sudo hidd --search" in terminal.

Ubuntu on this Powerbook has been poorly developed in my opinion, too many major things just not working adequately as noted above. And judging by the sticky topics and other topics, Ubuntu on PPC is looking a little bleak. Be careful.

---

