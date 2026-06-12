---
title: "ubuntu-xp dual boot problems"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by mklehner on 2008-02-27
Okay, so my computer wouldn't start up the other day ago, it just went to a blank screen. I called Dell to ask what was up, and the guy told me it was a glitch in Vista (did the diagnostics tests) and to get all of the stuff I needed off of my harddrive backed up so that they could restore to original settings. I didn't want Vista anymore, so I went and bought a student copy of XP for $30. Me thinking it was Vista's fault didn't want to pay a bunch of money to get stuff backed up by a technician, so I loaded Ubuntu onto my computer to pull the stuff off. That was successful. Ubuntu worked. Now, I'm trying to get XP onto my computer, dual boot OR XP alone (I need XP for a software I have to use for an engineering class). I've tried both routes. Both ways I get an error message from XP saying that my computer doesn't have hard disks in my computer. I called Dell to ask them about it, and the people said that it was a problem with Linux and not the harddrive. They told me that Linux isn't allowing XP to boot because it is on the harddrive and something about how that is what it does. Is this true, or are they being idiots and my harddrive has gone bad? Do you think it was Vista's fault or just the harddrive? Thankssss!!

---

### Post by Het Irv on 2008-02-27
XP is not recognizing your partition.  The best way to fix this is to use Gparted to resize your Ubuntu partition.  You can install Gparted thru Synaptic or you can find it on the live CD.  XP should then recognize the free space.

---

### Post by djbsteart1 on 2008-02-27
if you want to dual boot, boot ubuntu on live cd and format all disks. then install xp, then ubuntu. grub will then chainload both os,s and you have a dual boot system. 
when you wipe the hardisks, put then into fat, or a partition like that so windows wont cripple itself reading them.

---

### Post by Duck2006 on 2008-02-27
If you have ubuntu on the disk and want to install XP this may help.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by Arthur Archnix on 2008-02-27
The way I'd tackle this problem is to do this:

1) Get your data backed up off that computer. DVDs, CDs, whatever.
2) Burn a [gparted live cd]("http://gparted-livecd.tuxfamily.org/download.php")
3) Reboot into gparted and use it to delete every partition you see. Apply the changes. You've now got a fresh disc.
4) Still using gparted, create the partitions you want. I'd recommend the following:
     --1--10GB primary partition (ntfs)
Make the remaining space an extended partition, then create:
     --2--1GB linux swap partition
     --3--7GB ext3 partition
     --4--remaining space (ntfs)

So, you'd install XP to the first partition, obviously. And use it as you like, as much as you like. You put all your data into the largest ntfs partition, which Window will see straight away. Then, you install ubuntu into the 7GB ext3 partition. You'll be able to access all your data on the ntfs partition, and grub will let you choose which one to boot.

Whatever you decide to do, what with the problems you've been having you should just give up on the current setup as a bad job, wipe it out with gparted and start over.

---

### Post by mklehner on 2008-02-27
Thank you all so much! I'll have to get started on researching and testing this all and I'll write back if there are any problems.

---

### Post by djbsteart1 on 2008-02-28
if only all computing issues could be settled with a towel........

---

### Post by Het Irv on 2008-02-28
> **djbsteart1 said:**
> if only all computing issues could be settled with a towel........
+1
Some can...all you have to do it put a towel over the computer and, ta da, Windows Fixed.

---

### Post by djbsteart1 on 2008-02-28
if by windows you mean the m$ variety, surely a black towel........ maybe a brown colered box for the computer as well?

---

### Post by Het Irv on 2008-02-28
Yes.. That would do nicely.

---

