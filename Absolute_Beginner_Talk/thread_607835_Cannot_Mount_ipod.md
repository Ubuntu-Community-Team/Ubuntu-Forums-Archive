---
title: "Cannot Mount ipod"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-11-09
What am I doing wrong?

```
lydia@lydia-desktop:~$ sudo mount -a /media/ipod
Password:
mount: can't find /media/ipod in /etc/fstab or /etc/mtab

```

I have done numerous searches and cannot find a solution.  I am running Feisty, if that helps.

---

### Post by bean77 on 2007-11-09
When I try to drag a song into the ipod in Rhythmbox, I get this:

**Could not open file "/media/IPOD/iPod_Control/Music/F22/Wu-Tang Clan Old Dirty Bast.mp3" for writing.**

---

### Post by bean77 on 2007-11-10
Anyone?

---

### Post by Joakim Stokland on 2007-11-10
You could have a look at this:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by mcduck on 2007-11-10
> **bean77 said:**
> What am I doing wrong?

```
lydia@lydia-desktop:~$ sudo mount -a /media/ipod
Password:
mount: can't find /media/ipod in /etc/fstab or /etc/mtab

```

I have done numerous searches and cannot find a solution.  I am running Feisty, if that helps.

Unless you have configured the ipod in /etc/fstab/ you have to tell 'mount' 2 things, what you want to mount, and where you want to mount it. Right now your command only tells where you wish to mount your ipod, but not actually what device you are trying to mount.

The right command would be something like this (although the actual device/partition depends on your system so I can't possibly tell what it is..):
```
sudo mount /dev/sdb2 /media/ipod
```

---

### Post by Slipmyknot101 on 2007-11-10
What generation is your Ipod? It's easier to figure it out based on how old or new your ipod model is.

---

### Post by bean77 on 2007-11-10
It's a 4GB pink Nano...Maybe the 6th generation?

---

### Post by bean77 on 2007-11-10
> **mcduck said:**
> Unless you have configured the ipod in /etc/fstab/ you have to tell 'mount' 2 things, what you want to mount, and where you want to mount it. Right now your command only tells where you wish to mount your ipod, but not actually what device you are trying to mount.

The right command would be something like this (although the actual device/partition depends on your system so I can't possibly tell what it is..):
```
sudo mount /dev/sdb2 /media/ipod
```

If I go look in /dev, I see several "sbd" files.

Sorry I'm such a noobie at this...

---

### Post by bean77 on 2007-11-10
```
lydia@lydia-desktop:~$ pmount /dev/sdb2 data
Error: device /dev/sdb2 is already mounted to /media/IPOD

```

---

### Post by mcduck on 2007-11-10
> **bean77 said:**
> If I go look in /dev, I see several "sbd" files.

Sorry I'm such a noobie at this...

You can get the correct device if you open a terminal, run 'tail -f /var/log/messages' and then plug the ipod in. It should output something like this:

```
Nov 10 17:38:02 Hyperion kernel: [13667.304000] usb 3-1: new high speed USB device using ehci_hcd and address 5
Nov 10 17:38:02 Hyperion kernel: [13667.436000] usb 3-1: configuration #1 chosen from 1 choice
Nov 10 17:38:02 Hyperion kernel: [13667.436000] scsi3 : SCSI emulation for USB Mass Storage devices
Nov 10 17:38:07 Hyperion kernel: [13672.436000] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Nov 10 17:38:07 Hyperion kernel: [13672.436000] sd 3:0:0:0: [sdb] 12000555 512-byte hardware sectors (6144 MB)
Nov 10 17:38:07 Hyperion kernel: [13672.436000] sd 3:0:0:0: [sdb] Write Protect is off
Nov 10 17:38:07 Hyperion kernel: [13672.440000] sd 3:0:0:0: [sdb] 12000555 512-byte hardware sectors (6144 MB)
Nov 10 17:38:07 Hyperion kernel: [13672.440000] sd 3:0:0:0: [sdb] Write Protect is off
Nov 10 17:38:07 Hyperion kernel: [13672.440000]  sdb: sdb1 sdb2
Nov 10 17:38:07 Hyperion kernel: [13672.680000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Nov 10 17:38:07 Hyperion kernel: [13672.680000] sd 3:0:0:0: Attached scsi generic sg2 type 0
```
This tells that the ipod is detected, and it's assigned as /dev/sdb. As the first partition on ipods actually contains the system data, and the music is on second partition, the one that would be mounted in this case would be /dev/sdb2.

The device name comes from the order in which the disks on your computer are detected, the first disk is /dev/sda, second is /dev/sdb and so on. And the number in the end tells which partition on that disk we are talking about. So because I don't know how many disks you have on your computer I can't tell what device the ipod would be on your machine..

---

### Post by bean77 on 2007-11-10
```
lydia@lydia-desktop:~$ sudo mount /dev/sdb2 /media/IPOD
mount: /dev/sdb2 already mounted or /media/IPOD busy
mount: according to mtab, /dev/sdb2 is already mounted on /media/IPOD

```

---

### Post by mcduck on 2007-11-10
> **bean77 said:**
> ```
lydia@lydia-desktop:~$ sudo mount /dev/sdb2 /media/IPOD
mount: /dev/sdb2 already mounted or /media/IPOD busy
mount: according to mtab, /dev/sdb2 is already mounted on /media/IPOD

```

That would tell that you already have mounted your ipod (or at least something) in /media/ipod. Is there some problem still? What does 'ls /media/IPOD' say?

---

### Post by bean77 on 2007-11-10
```
Calendars  Contacts  iPod_Control  Notes  Photos  Songbird

```

---

### Post by mcduck on 2007-11-10
> **bean77 said:**
> ```
Calendars  Contacts  iPod_Control  Notes  Photos  Songbird

```
Your iPod is correctly mounted.

---

### Post by bean77 on 2007-11-10
But when I go into my ipod I have no songs listed there and when I have it set up in Rythmbox, it doesn't see it.

---

### Post by bean77 on 2007-11-10
Is Songbird something I need to have on my computer?

---

### Post by mcduck on 2007-11-10
> **bean77 said:**
> But when I go into my ipod I have no songs listed there and when I have it set up in Rythmbox, it doesn't see it.

All the music should be inside the iPod_control directory, but you need to use some program to add/remove the songs so that the iPod's database gets updated correctly.

I have no idea why Rhythmbox doesn't see the ipod, I've never really used Rhythmbox myself. But you could try some other program, at least GTKPod has always worked for me..

(No, you don't need Songbird to use iPod. Any program that has iPod support should work.)

---

### Post by bean77 on 2007-11-10
So 2 more questions:

1.  How do I make so Rythmbox does NOT automatically open when I plug in my ipod

2.  Somehow I've imported songs into Songbird that I thought I was not able to get into on my ipod.  So the problem now seems to be that the songs are there but I can't see them.  However when I get into the Settings section of the ipod menu, it says I have 0 songs, 1.4 GB available, 3.6GB capacity.

Says I have version 1.1.1

I'm not sure what to do now.

---

### Post by mcduck on 2007-11-10
> **bean77 said:**
> So 2 more questions:

1.  How do I make so Rythmbox does NOT automatically open when I plug in my ipod

2.  Somehow I've imported songs into Songbird that I thought I was not able to get into on my ipod.  So the problem now seems to be that the songs are there but I can't see them.  However when I get into the Settings section of the ipod menu, it says I have 0 songs, 1.4 GB available, 3.6GB capacity.

Says I have version 1.1.1

I'm not sure what to do now.

1. System/Preferences/Removable Drives and Media, on the Multimedia-tab.

2. I've never used Songbird myself. What program did you use to load the songs into the iPod? Does the iPod itself find the songs and play them correctly? You could try loading some songs to the iPod with Rhythmbox or GTKPod to see if they work correctly that way..

---

### Post by bean77 on 2007-11-10
Doesn't matter what program I've synced with, nothing is showing up in my ipod under songs, artists, playlists, etc.  But somehow Songbird got songs that I tried to download a while ago!  

I also clicked on my ipod on my desktop and I can see folders with my music in them but they are not named correctly

**/media/IPOD/iPod_Control/Music**

---

### Post by mcduck on 2007-11-10
> **bean77 said:**
> Doesn't matter what program I've synced with, nothing is showing up in my ipod under songs, artists, playlists, etc.  But somehow Songbird got songs that I tried to download a while ago!  

I also clicked on my ipod on my desktop and I can see folders with my music in them but they are not named correctly

**/media/IPOD/iPod_Control/Music**

They are not supposed to be named correctly. That's how Apple made the iPod to work. The songs are distributed into different directories and given strange names, but that doesn't really make any difference as you could not anyway just drop new songs there. You need to manage music on your iPod with some program that also handles updating the song database on the iPod.

I still know nothing about Songbird, and I'm not even sure what you mean with "Somehow I've imported songs into Songbird that I thought I was not able to get into on my ipod". Did you use Songbird to load the music into the iPod? And does the iPod play those finds (without your computer)?

---

### Post by oberg on 2007-11-10
I installed and used amarok because i was having issues with rythmbox and my ipod.  Amarok accepted my ipod perfectly fine and allowed me to upload all my songs.

---

### Post by bean77 on 2007-11-10
I opened up Amarok, and it can't find my ipod.

Grrr-this is the one thing that makes me not love linux 100%.  Ive completely switched over and this aspect of it has eaten up SO much of my time!!!

---

### Post by mcduck on 2007-11-10
> **bean77 said:**
> I opened up Amarok, and it can't find my ipod.

Grrr-this is the one thing that makes me not love linux 100%.  Ive completely switched over and this aspect of it has eaten up SO much of my time!!!

Again, what program did you use to upload the songs to the iPod? If GTKPod recognized the iPod, did you try uploading some songs to the iPod with it? It could be that the problem is caused by the program you used to upload the music in the first place.

---

### Post by bean77 on 2007-11-25
I think I originally used Rythmbox.  I've reinstalled Ubunt since then though.

---

