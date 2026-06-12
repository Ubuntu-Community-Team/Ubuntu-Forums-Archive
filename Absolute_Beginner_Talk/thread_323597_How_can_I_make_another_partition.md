---
title: "How can I make another partition?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2006-12-22
I've been thinking that I could do more on Windows XP (i know, :( )...So please help keep me on ubuntu, and if possible is there any way to make another partition w/o reinstalling ubuntu?

---

### Post by dbbolton on 2006-12-22
you could use "Gparted", a partition editor. i prefer it to Qparted

---

### Post by 454redhawk on 2006-12-22
> **zetsumei said:**
> I've been thinking that I could do more on Windows XP (i know, :( )...So please help keep me on ubuntu, and if possible is there any way to make another partition w/o reinstalling ubuntu?


You're kidding right?

download burn and boot this ISO.

Gparted


[http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=umn&filename=gparted-livecd-0.3.3-0.iso&91401856]("http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=umn&filename=gparted-livecd-0.3.3-0.iso&91401856")

---

### Post by raul_ on 2006-12-22
> **zetsumei said:**
> I've been thinking that I could do more on Windows XP (i know, :( )...So please help keep me on ubuntu, and if possible is there any way to make another partition w/o reinstalling ubuntu?

more what?

---

### Post by JayTee on 2006-12-22
zetsumei, hi! we chatted the other night in #ubuntuforums on IRC. I'd take the advice of the previous posts and use the Gparted cd but with this one caveat. FIRST, if you've got Windows installed already and are thinking of installing Ubuntu now, before you use Gparted run chkdsk /f from a command line window in Windows XP and then run Disk Defragmenter. Running chkdsk will force you to do a restart to run the chkdsk as chkdsk cannot run against a mounted volume with the /f parameter. This ensures that there are no disk errors and that all the data on your XP partition is compacted as much as possible. This makes it safer to shrink the Windows partition to accomodate a new partition for Ubuntu.

---

### Post by bulldog on 2006-12-22
Understand it wrong I think.

---

### Post by Pauliniho on 2006-12-22
> **JayTee said:**
> zetsumei, hi! we chatted the other night in #ubuntuforums on IRC. I'd take the advice of the previous posts and use the Gparted cd but with this one caveat. FIRST, if you've got Windows installed already and are thinking of installing Ubuntu now, before you use Gparted run chkdsk /f from a command line window in Windows XP and then run Disk Defragmenter. Running chkdsk will force you to do a restart to run the chkdsk as chkdsk cannot run against a mounted volume with the /f parameter. This ensures that there are no disk errors and that all the data on your XP partition is compacted as much as possible. This makes it safer to shrink the Windows partition to accomodate a new partition for Ubuntu.

I installed Dapper a few days ago after a few weeks plucking up the courage. I've heard a lot of scare stories when it comes to resizing partitions, but the other day, I went for it.

I defraged my hard drive about 5 times which compacted the data to the "front" of the drive. When I resized the partition I had no problems at all. Kinda wondered what all the fuss was about in the end ;)

---

### Post by MrKlean on 2006-12-22
The fuss is simple... You HAVE to defrag first...if ya don't.. you may mess up yer XP.  Trust me... I did it LOL!!!

---

### Post by maddog39 on 2006-12-22
The simple way to install gparted on ubuntu:
```
sudo apt-get install gparted
```
Then run it as root:
```
sudo gparted
```

---

### Post by raul_ on 2006-12-22
But he can't use GParted on a mounted partition so if wants to take space from the Ubuntu partition that wouldn't help...I think he should use the GParted live cd

---

### Post by jvc26 on 2006-12-22
Another question is... do more what? What is it that you're lacking in ubuntu that you need/cant find an alternative to - people might be able to help you out with that if you wanted.
Il

---

### Post by aysiu on 2006-12-22
No one should need to convince you to stay on Ubuntu. If you can do more on Windows, use Windows. If you need help with something on Ubuntu, ask for help. I've retitled your thread to describe the only problem you've mentioned.

---

### Post by zetsumei on 2006-12-22
the only main thing thats making me go back to windows are games and photoshop (i just cant get the hang of gimp) and yes i can install games w/wine, but its very laggy...

---

### Post by aysiu on 2006-12-22
I think the real question, then, is... what keeps you keep coming back to Ubuntu?

If Windows does everything you want it to do, you should probably use Windows.

---

### Post by zetsumei on 2006-12-22
what keeps me coming back is b/c i like ubuntu and some of the features...

for example, linux has better uptime than windows -_-, and IMO it boots faster than windows (if i could find a guide on tweaking windows so much that I could get it to boot in under 10 secs I would move to it again and stay with it...

but after this topic, I might go back to windows as I'm looking for guides on tweaking it so much that it runs more efficient...

---

### Post by bulldog on 2006-12-22
Didn't misunderstood after all.:(

---

### Post by WebJoel on 2006-12-22
I just downloaded GParted *ISO, -am considering partitioning a portion of my C:/ drive to make room for Ubuntu, to make for duel-boot system. What I'd *like to do* is install Ubuntu on my D:/ drive as an alternate start-up but would accept having Linux on same HDD as XP. -I just can't get the thought of the next, inevitable Windows crash-n-burn damaging Linux if on the *same disk-drive* (but other partition). My local pc shop is a big believer in mirroring the saveable data out and wiping the Master disk for re-install of everything on any 'damaged' HDD (actually, "damaged OS", but treats as if entire HDD needs to have everything re-installed). 
 I might try out GParted on my Slave drive to 'get the hang of it' first, before I start resizing my Master drive...
 -I guess I am just looking for a 'atta-boy!' for downloading "GParted" as another step in the right direction...

---

### Post by bulldog on 2006-12-22
If you have installed windows and make a separate partition for ubuntu,a windows crash will not involve ubuntu.
A hard disk crash would.

If you boot the gparted live cd you should see al your partions,if you have a free one with sufficient space you can install ubuntu there.
You will install a bootloader as  well,called GRUB,which it makes possible to choose which OS you want to boot.
Ubuntu is set as the default,but that is easy to change.

But as always,it's a good idea to backup your important data before you go messing with partitions and resizing your disk!!!
A little mistake is enough to wipe your data from the disk.

---

### Post by Greevous on 2006-12-23
> **zetsumei said:**
> 
but after this topic, I might go back to windows as I'm looking for guides on tweaking it so much that it runs more efficient...

Zetsumei,


If you haven't found a good resource yet, I'd recommend PCSTATS's [99 Performance tips for Windows]("http://www.pcstats.com/articleview.cfm?articleID=1590"),  [104 Great Tech Tips for Windows]("http://www.pcstats.com/articleview.cfm?articleID=1681"), and [101 Tips and Tweaks for Windows]("http://www.pcstats.com/articleview.cfm?articleID=1494"). 

All three are **excellent** guides for Windows.

---

### Post by William Pickett on 2006-12-25
Hello,
I have- according to File system/cdrom, downloaded and burned an iso image of gparted. Question is/are 1) how to change directory- cd /filesystem/cdrom/gpartedx.x.x etc does not do it, and 2) since I am a new to understanding linux user, would whoever responds to this help, spell out all the items, do not presume I 'get it' at all, thanks. (Walk me thru this- first you do this, which is done by doing a, then b, then c, etc and here is how a is done...);) 

William, who may have to write a new linux/ubuntu user book for my own use if no other reason, ;-)

---

### Post by 454redhawk on 2006-12-27
> **William Pickett said:**
> Hello,
I have- according to File system/cdrom, downloaded and burned an iso image of gparted. Question is/are 1) how to change directory- cd /filesystem/cdrom/gpartedx.x.x etc does not do it, and 2) since I am a new to understanding linux user, would whoever responds to this help, spell out all the items, do not presume I 'get it' at all, thanks. (Walk me thru this- first you do this, which is done by doing a, then b, then c, etc and here is how a is done...);) 

William, who may have to write a new linux/ubuntu user book for my own use if no other reason, ;-)

Not sure I understand your question.

If you downloaded and burned the Gparted .iso you need to reboot your computer with that cd in the drive. That will launch the Gparted live cd. (assuming you have boot to cdrom enabled)

---

