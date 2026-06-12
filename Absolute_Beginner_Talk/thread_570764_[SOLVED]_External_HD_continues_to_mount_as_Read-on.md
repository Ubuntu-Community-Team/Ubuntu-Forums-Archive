---
title: "[SOLVED] External HD continues to mount as Read-only only"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Limitlesschannels on 2007-10-08
Lately my external HD (Western Digital 160GB USB passport) has been mounting as read-only.  This is strange as nothing has really changed on my system.  Also, many times this may occur after the disk is already mounted and it suddenly becomes read-only.
   This gets really annoying as I download files to a folder within the disk and many times i will get an error halfway through letting me know that the disk is read-only.  I can usually unlock the disk once i restart or remount, but it still is a big hassle.
   Another thing that I am not sure if it is related or not involves the mounting of my mp3 player.  I recently purchased a sony mp3 player that seems to have a lot of trouble mounting to my system.  I can mount it successfully and copy songs to it, but when I unmount it (and I mean unmount, not just pull out the player) and remount it it usually mounts read-only with a significant number of files corrupt.  No matter how long I wait after copying the files or making sure that the disk successfully unmounts, the files come up corrupt when remounting.  Usually I cannot even force remove these and all I can do to reuse the disk is to cleanly format it.

---

### Post by julian67 on 2007-10-08
I have had similar issues and solved them. The first thing to get right is the hardware. I pinpointed the same problems to cheap USB cables and a cheap bus powered USB hub. When I bought a powered hub and checked my USB cables one by one I eliminated the problems of data corrupting on transfer and of drives suddenly becoming read only. I have also had the same issue with a cheap external 2.5" drive caddy with a lousy USB controller on it. 

On a different PC I worked on there were similar bizarre issues with USB peripherals. It turned out that a small metal piece of the rear slots of the PC case was shorting out a USB port.  

As for the Sony mp3 player it could be a fake with a hack to make the flash memory look bigger than is the case, or it could be a real Sony mp3 player but with the good flash removed for resale and hacked smaller size substituted. But probably it's OK and actually you have at least one piece of problematic USB hardware. I hope it isn't your main board.

---

### Post by Limitlesschannels on 2007-10-08
Yeah, It sounds like you might be right on the cheap USB cables.  I don't really know for sure, but i have a couple extras to try out.
   I do have a laptop, so the rear slot shortage problem is probably not it, but that just makes the idea of having a messed up main board much worse.  I have 3 USB ports across my laptop and have tried multiple ones to see if it is the specific port.  It doesn't appear to be.  Also, I dual boot to windows and it seems like that the problem goes away once in windows; something i hate to admit, but definitly interesting.

My mp3 player is most definitly a fake sony, but just like the external HD, when i boot into windows i can access the files; so, apparently, we have a problem with linux and my USB devices.  I still need to reformat the mp3 player under windows to get the corrupted files off, but at least I can do that.

To start off, what is the command syntax for remounting a drive with read AND write priviliges?  Maybe it is as easy as unmounting and remounting the drive with the correct priviliges, but i doubt it.  The drive is sdb1.

Anyone else have any ideas?

---

### Post by julian67 on 2007-10-08
It could be a problem with the way Linux manages your onboard USB controller, perhaps not enough power to the bus,  but I wouldn't know enough to really help. Do you have a hub with external power you can try?

To make sure you have write permissions is easy enough. I'll assume your external drive is mounted on /media/disk

```
sudo chown -R yourusername /media/disk/
```

You might need to unmount/disconnect and remount it.

btw did these problems occur before you used the mp3 player?

---

### Post by Limitlesschannels on 2007-10-09
I don't think that it is a problem with my drive not receiving enough power as another USB-powered HD I have has had no problems so far.  No, i have no powered hub to try, maybe I will have to pick one up soon, but, again, I somewhat doubt that is it since my other external works fine.

The problem has been around before my mp3 player, I only got the mp3 player a couple weeks ago, but have had the permission issue for about 2 months.  Usually I could remount it and fix the issue, but since I posted my first message, it has stayed locked the entire time, even with several reboots and USB port switches.  I can still modify the files in windows, though.

---

### Post by julian67 on 2007-10-09
You don't mention if you did this ```
sudo chown -R yourusername /media/disk/
``` and if you did what was the result/output?

How is the external drive formatted? ntfs?

---

### Post by lionround on 2007-10-09
Julian,

I have an external USB Lacie HD (with Seagate drive) 250 gig, fat32. It is mounted at /media/LACIE with a folder on it at /media/LACIE/music. I have about a gig of music in the folder.

I want to be able to share/read/write files to and from the drive from my XP and 98 machines.

I am using Ubuntu Feisty Fawn 2.6.20-16-generic.

I have Samba installed and properly configured (I hope.)  I have a share folder in my home directory that is accessible through the network with read/write permissions that works fine.

The problem is that when I try to access it from either my XP or 98 machines, it shows up in Network Neighborhood under \\Ubuntu\Lacie  and when I click on it is "inaccessible." The owner permissions are set to david (that's me) with read and write and the root group. It won't allow me to change ANY of these options.

I tried gksudo nautilus and could not change anything.  I tried chown with no effect either.

---

### Post by julian67 on 2007-10-09
> **lionround said:**
> Julian,

I have an external USB Lacie HD (with Seagate drive) 250 gig, fat32. It is mounted at /media/LACIE with a folder on it at /media/LACIE/music. I have about a gig of music in the folder.

I want to be able to share/read/write files to and from the drive from my XP and 98 machines.

I am using Ubuntu Feisty Fawn 2.6.20-16-generic.

I have Samba installed and properly configured (I hope.)  I have a share folder in my home directory that is accessible through the network with read/write permissions that works fine.

The problem is that when I try to access it from either my XP or 98 machines, it shows up in Network Neighborhood under \\Ubuntu\Lacie  and when I click on it is "inaccessible." The owner permissions are set to david (that's me) with read and write and the root group. It won't allow me to change ANY of these options.

I tried gksudo nautilus and could not change anything.  I tried chown with no effect either.

ah.... that's a bit of a surprise as no previous mention of samba, only USB drive and I assumed you were dual booting one PC. I use samba but via pyneighborhood as I use Xfce (which uses Thunar and doesn't have Nautilus's built in ability to browse shares) and I'm probably not knowledgeable enough about it to help you. I understand that the drive is writeable from within Ubuntu and that if you boot into Windows on the same machine it is also writeable, and that another share in your Ubuntu /home is accessible across the network. So the issue would seem to mounting the share in samba. The root of the drive is mounted in /media and I'm not sure how this affects the permissions of the folders subsequently mounted in /home. 

You'll need someone with more experience in this than me to help you any further I suspect.

---

### Post by lionround on 2007-10-09
I guess the crux of my questions is:

a) how do I force the external to mount in my /home directory?

b) if I mount it in my /home directory, will it still be read only?

---

### Post by julian67 on 2007-10-09
You can just edit /etc/fstab to change the mount point. I'm not sure what would happen though if your external drive was not connected on boot. 

I do something similar but with a second internal drive /dev/hdb. You can see that it's in 3 partitions and all 3 are mounted in /home/julian. The music partition is shared in the same way as some other folders which are physically on the 1st drive and are under /home/julian/ 
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    defaults        0       0
#Entry for /dev/hda1 :
UUID=8f6307ff-0fd3-4466-8c4b-7a18b001c2dd       /       ext3    defaults,noatime,errors=remount-ro      0       1
#Entry for /dev/hda3 :
UUID=66d148ff-6f59-41b2-9dca-c3c7dbe659d8       /home   ext3    defaults,noatime0       2
#Entry for /dev/hdb2 :
UUID=aacc74c6-678a-4612-8304-2e9eadbf8b80       /home/julian/lossless   ext3   defaults,noatime 0       2
#Entry for /dev/hdb1 :
UUID=29114b58-8387-411e-a099-9fde9cf12be1       /home/julian/music      ext3   defaults,noatime 0       2
#Entry for /dev/hdb3 :
UUID=cf5e0cc2-8713-410e-a3fd-73851132203c       /home/julian/Photos     ext3   defaults,noatime 0       2
#Entry for /dev/hda2 :
UUID=c669cd77-10b6-4274-9c8e-fb494f6e34e2       none    swap    sw      0      0
/dev/scd1       /media/cdrom0   udf,iso9660     user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660     user,noauto     0       0


But once again I think you should get some advice from someone more knowledgeable than me. Perhaps if nobody else joins this thread you can search the forums here and at places like linuxquestions and also have a good read of all docs on samba.

---

### Post by Limitlesschannels on 2007-10-09
> **julian67 said:**
> You don't mention if you did this ```
sudo chown -R yourusername /media/disk/
``` and if you did what was the result/output?

How is the external drive formatted? ntfs?

When I tried the command I received  ```

chown: changing ownership of `/media/BLACK_BOX/.Trash-1000/x&#9500;Tzèæ&#9496;é.yq&#9524;': Read-only file system
chown: cannot access `/media/BLACK_BOX/.Trash-1000/\035ü\002.a&#9612;æ': Input/output error
chown: cannot access `/media/BLACK_BOX/.Trash-1000/&#9524;&#937;3&#960;\nhµ¼.&#9492;Ä&#9570;': Input/output error
chown: cannot access `/media/BLACK_BOX/.Trash-1000/mbd&#9563;æy&ß.²it': Input/output error
chown: cannot access `/media/BLACK_BOX/.Trash-1000/&#9554;p&#9579;h~\\t\025.Ö"_': Input/output error
chown: changing ownership of `/media/BLACK_BOX/.Trash-1000/:0\\·)\035BD.&\031E': Read-only file system
chown: changing ownership of `/media/BLACK_BOX/.Trash-1000/&#9564;N?&#9600;·&#8359;(&#9552;.&#8319;B': Read-only file system
chown: cannot access `/media/BLACK_BOX/.Trash-1000/&#9557;&#8805;n&#9488;|&#9560;&#9567;\t.&#8359;æa': Input/output error
chown: cannot access `/media/BLACK_BOX/.Trash-1000/&#9600;rt&#9579;yg£5.^s{': Input/output error
chown: cannot access `/media/BLACK_BOX/.Trash-1000/F*\bnG#h@.öa&#934;': Input/output error

```

so it looks like i might have some corrupt files in my trash.  Even a force remove doesn't seem to get these off, maybe i have to get onto windows to do it, any ideas?

also,
```

ah.... that's a bit of a surprise as no previous mention of samba, only USB drive and I assumed you were dual booting one PC.

```
I don't know if you noticed, but lionround is not me.

Lionround:  Your issue doesn't seem to be related, you would probably have more success starting a new thread.

---

### Post by julian67 on 2007-10-09
> **Limitlesschannels said:**
> 
I don't know if you noticed, but lionround is not me.

Lionround:  Your issue doesn't seem to be related, you would probably have more success starting a new thread.

You're right, I simply read the post assuming it was from you and didn't spot the stowaway who had climbed on board :) Lionround please don't hijack other people's threads, it wastes everybody's time including your own.

Yes you've got a lot of corrupted files. I had exactly the same experience with my USB problems. I would back up the good data *if possible* and format the drive with something like GParted which *I believe *will also check for bad sectors. You should check this yourself. I had one drive which appeared to be irretrievably bad until I spent the $ and tried it in a different caddy and found that after a format it was perfect. So I think you can try all kinds of things but  you need to pinpoint the faulty hardware and discard it, which is likely a trial and error (lots of errors!) process.  Why not use different cables first as they are the cheapest part of the whole set up. I lived for a while in SE Asia, it's extremely humid, and cheap cables tended to corrode very fast. You should examine your hardware for obvious physical problems like this or a snick in the insulation and so on.

---

### Post by Limitlesschannels on 2007-10-11
Yeah, I have been having these corrupt files issues for a while now.  Like I said before, whenever I attempt to remount that mp3 player it comes up read only and will corrupt files with any more additions.
   Anyway, I am thinking that the backup and reformatting of the external is not really an option as I have about 150 of the 160GB filled up.  And I use the drive itself as a backup device.  But, the ability to freely modify the files off this drive inside of Windows still makes me think that I am having some sort of problem with linux and not with the drive itself.  So, it looks like rather than wade through all the system files I can and try and fix something, I will just reinstall the system.  Plus, the release of Gusty in about a week sounds like a good opportunity to to a clean system wipe.  I just hope I can reload some of the usual custom modifications that I need on my install.
   That's interesting what you said about living in Southeast Asia with the humidity.  I just recently moved (within the last month or so) to South America where I am living much much closer to the Equator and in fact in much greater humidity than before.  Thanks for the suggestion as I will have to rethink the effect of the atmospherical conditions on my hardware.  But, again, my other external is fine, so I am assuming that the problem lies within my system and not the drive itself.

---

### Post by lionround on 2007-10-11
My apologies for hijacking:(

I have been following the thread and THOUGHT it was related.

:confused:

---

### Post by julian67 on 2007-10-11
I don't think it's a Linux issue that will be solved by re-install, only that the corruption is not causing such obvious problems in Windows yet, but good luck. If it was me I would be not be using this drive for important storage or any kind of back up until the problem is solved or at least identified for sure. Disks are very cheap right now, it might be worth considering buying another.

---

### Post by Limitlesschannels on 2007-10-24
Yay!

Great, after the install the drive was still mounting as read only but this time I rebooted into windows and worked checkdisk over both of my disks (just to make sure the other didn't have any corrupt files on it).  After converting the broken chains to files, I was able to delete the corrupted trash I had and I repair the disk to a writeable state.  After that, I can successfully mount it in both linux and windows to trade files.  Thanks for the suggestions, Julian, but it looks like the corrupt trash was the issue all along.
  I agree, though, about keeping too important files off these disks.  I have never felt safe without at least two backups of  my files, but especially if the are on passport harddrives (both easily transportable and easily damageable).

---

### Post by julian67 on 2007-10-24
Glad to see you got your drive working again. Any idea what caused the corruption? It might be something that could happen again.

---

### Post by simonrack on 2007-11-07
I am not sure if I am having the same problem or not - I have a WD Passport drive that I loaded with files form XP before switching over to Ubuntu Feisty Fawn. 

So, now all my old docs and mp3s are on this drive... It "mounts" but i cannot navigate to the files. All I see are WD Sync exe files that I cannot run.  I am wondering if they are somehow obscured by me not being able to use the "sync" option. 

Am I missing something basic? are my files trapped?

Update: I have found my files, saved in a folder as .dml and .dml.rmv  I understand that .dml is used when storing data and the .rmv may be ream meadia files? Is there a way to manipulate/recover these files and just circumvent the use of the wd sync interface?

---

### Post by DarinB on 2007-11-08
i did reformat the external hard drive as well but it didn't help it would even be seen by the windows box.
this below helped
sudo chown -R yourusername /media/disk/
now it is copying the music lets see if it works.
Thanks every body.
D

---

### Post by campero on 2007-11-10
I just recently switched to Ubuntu from XP, before the changeover I used the WDSync tool that comes with my WD External HD. Well, it turns out this is a .exe and Ubuntu doesn't run it. Is it there a way to recover my files? or do I have to go to a windows machine and take them all out from the WDSync file? Any ideas?

Thanks

---

### Post by Limitlesschannels on 2007-11-25
Hm, that is strange that so many people are having troubles with their files showing up on ubuntu from XP.  I always use my WD Passport HD on both, just chucking files onto it and pulling them off on the other OS, but I have never had a problem with it.  The WDsync.exe and related files are just on there and I have never bother with them at all.  I hate all that extra pseudo-useful software that comes with new hardware.  Just stick the files on through the explorer and pull them off through thunar/nautilus/konqueror, it always works fine for me.

---

