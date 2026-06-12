---
title: "Help getting started"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by macel82 on 2007-09-19
I wanna get started with Ubuntu on my PC.  But I wanna keep Windows as well.  I have an 80gb internal HDD already partitioned into C and D and a 300gb external Firewire HDD.  I don't wanna screw up my PC though and I'm wondering exactly what to do to make sure that doesn't happen.  I'm assuming that I just partition some of my HDD space for the Ubuntu installation and tell it I want to dual boot.  But is there anything else I should look out for?  Can I install it onto my external HDD?  Is NTFS a problem?  Let me know what kind of issues might come up.  Thanks.

---

### Post by splintercellguy on 2007-09-19
Reading to NTFS is possible out of the box, for r/w, you have to install the ntfs-config package and run the NTFS Configuration Utility. Other than that, just be careful, don't select Use entire disk, and good luck. Yes, you can install on an external, though where GRUB would be installed is an interesting question.

---

### Post by atria on 2007-09-19
NTFS is not a problem anymore since with the ntfs-3g driver you will be able to write to the NTFS partition.

Just don't delete your existing windows partition and you should be fine. Have fun.

---

### Post by Jeroen Vernooij on 2007-09-19
Hi,
I would recommend to install it on your internal disk, for more speed.

First thing: Backup the stuff that's really important to you: burn it to CD/DVD or put it on the Firewire-disk and leave the firewire-disk unconnected while you are installing ubuntu.

Then, When you're installing ubuntu (just download the regular 7.04 disk) you need to resize the Windows partition on your harddrive, to make space for a linux partition. So make sure your harddrive has at least 10gb free to make space.

After ubuntu is succesfully installed, reboot and you should get a menu in which you can choose to start windows or ubuntu.

Choose ubuntu to see if it works. 
When logged in: plug in firewire-disk. It should appear on your desktop.

Then: install nfts-config and run it. Now you can write on the firewire-disk.

Good luck,
Jeroen.

---

### Post by Jeroen Vernooij on 2007-09-19
Problem is when you want to install it on your external firewire-disk: You don't know for sure if your computer can boot from it. However, if it can, it's fun because your install is portable. You can then even install it on an usb-stick (>2gb).

---

### Post by macel82 on 2007-09-19
> **Jeroen Vernooij said:**
> Hi,
I would recommend to install it on your internal disk, for more speed.

First thing: Backup the stuff that's really important to you: burn it to CD/DVD or put it on the Firewire-disk and leave the firewire-disk unconnected while you are installing ubuntu.

Then, When you're installing ubuntu (just download the regular 7.04 disk) you need to resize the Windows partition on your harddrive, to make space for a linux partition. So make sure your harddrive has at least 10gb free to make space.

After ubuntu is succesfully installed, reboot and you should get a menu in which you can choose to start windows or ubuntu.

Choose ubuntu to see if it works. 
When logged in: plug in firewire-disk. It should appear on your desktop.

Then: install nfts-config and run it. Now you can write on the firewire-disk.

Good luck,
Jeroen.

So if all my important Windows system files and such are on the C partition, I can just put Ubuntu on the D partition?  I can just repartition D to have at least 10gb for Linux?  I just wanna play around with Linux for a while and see what's up.  The main goal is to not screw up my current system.

Like I said, D is just an existing partition of the one internal HDD I have.  Can I just break off 10 gb of it for Ubuntu or do I have to repartition the whole thing?  Is that gonna basically make a new drive like...E for example?  Should I defragment first?  

I know I have a lot of questions.  I promise I won't have as many in the future.  The getting started is just the hard part for right now.  Like I said I don't wanna mess up my system.  I have Yellow Dog on my PS3 and I've been playing around with it.  I'm just not sure about putting it on my Windows machine.

---

### Post by Jeroen Vernooij on 2007-09-19
Hi,
You also can't install ubuntu on your D: partition, even if it's on your internal harddrive.
Your new ubuntu installation wants a partition on it's own. That's why you have to decrease the size of your existing partitions (C: or D:) to make space for a new Ubuntu partition, which you can perform during installation. That's why you need to make sure you have at least ~10GB free on C: or D:

I said to backup your important files because you are going to install a new operation system, which always brings some risk to lose files or partitions (however don't be afraid: ubuntu is stable)

Ask as much as you want and need but you can also read and search: this is a good website for starters: [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by sailor2001 on 2007-09-19
It's always wise to defrag your windows prior to installing another os.....Installation is quite simple (resizing your windows). however, why don't you just use ubuntu as a live disk for a while to see how you like it and see if all your equipment works ok.....when you do install, ubuntu will set up a grub boot file that both it and windows can read to. Ubuntu will be default, but that can be changed quite easy.   Expect live disk to run slow.....normal

---

### Post by macel82 on 2007-09-21
How do I create a new partition on D: or my external drive without losing the data that's already on there?  I've searched around and that seems to be a problem for a lot of people.  From what I've read I'd have to just reformat an entire drive and that's not an option for me.

---

### Post by Sef on 2007-09-21
> How do I create a new partition on D: or my external drive without losing the data that's already on there? I've searched around and that seems to be a problem for a lot of people. From what I've read I'd have to just reformat an entire drive and that's not an option for me.

Read [Psychocat's Ubuntu.]("http://www.psychocats.net/ubuntu/index")

Read the [Illustrated Dual Boot.]("http://users.bigpond.net.au/hermanzone/")

**Back up ** your data.  Problems can always happen no matter how good you are.

---

### Post by macel82 on 2007-09-21
Ok I used Retrospect Express to duplicate all of the contents of D: onto my external Firewire drive.  So now there's a folder on my external with all of the contents of D: 

So now I need to boot the Ubuntu disc and do installation.  When I get to the partition part, can I reformat D: and break off 10 gb or so for Ubuntu?  Then once I do that, can I just go back into Windows and move all of the stuff back from my external onto the newly-partitioned and formatted D: ?   What about programs I have installed on D: ?   Is formatting and moving them all back gonna screw up the programs I have in there?  Or will everything run as normal once I put it back?  

I know these are a lot of questions, but this is the most important part for me because my Windows system now has like my whole life on it and I don't want to screw it up.  Once I get Ubuntu on there I'll be a lot more confident about learning Linux.  

Thanks

---

### Post by slira on 2007-09-21
Hi
I have those 2 solutions, on in my lap top and the other in my desktop.

Laptop, with a small hdd. I have:
1 partition for windows system and other windows software  (10gb)
1 partition for data (20 gb) both windows and linux
1 partition for ubuntu system (circa 8 gb) (including root and home)
1 partition for ubuntu swap (circa 768 Mb)

for this I resized the second partition (your D) making room for unallocated disk space before installing ubuntu (made a backup first!); when installing ubuntu use "free space" option or the "manual partition" option; in either cases be careful when deciding mounting points - by default you might be pointed to 1st partition, where your MSWindows is - that would destroy your Windows. See carefully if you are installing in the right partitions.

in this case, GRUB auto installs and during boot you are asked to chose the OS you want. (Notice that grub will rewrite first 400 bytes (or so) in your disk and change the MBR; so, if you give up ubuntu and destroy grub you will not be able to boot!!! without restoring your MBR); this is not a problem, you'll never give up ubuntu :)
(after all done you may want to edit /boot/grub/menu.lst from ubuntu, to change the grub menu; that's easy, but be careful not to change critical stuff........ in a shell the command will be 
[FONT="Courier New"]sudo gedit /boot/grub/menu.lst[/FONT])

=====================================

Desktop, in a 160 Gb external. I have:
1 partition for boot (100mB)
1 partition for root (6 gb)
1 partition for swap  (circa 2250 mb) (1,5 x your RAM)
1 (logical) partition for home, under root (rest of the disk) (as big as you want - that's for your data)

In this case, you install directly to the external hdd; use the "manual" option to create partitions. If you are afraid of making errors, you may disconnect the internal disk so you will be sure you will not mess with it. And grub will not be a problem (see below).

You must be sure that your BIOS allows booting from external drives... I decided to point my bios to the external drive in 1st place, then to CD, then to internal hdd; when the external is turned off, the pc boots with windows; when the external in turned on before turning on the pc, it boots from Ubuntu. Easy! This way dual booting is controlled by the switching on/off of the external drive and not by grub :lolflag: obviously, when I boot from the external hdd grub appears; (I edited it so I can decide to go to the internal drive from there, but that's not a need).

(final note: in another machine my son has a gentoo booting from a second internal hdd; if you want his solution I'll ask, ok? it's also usable in ubuntu)

Have fun! Ubuntu is a very good OS, I hope you enjoy.
best
slira


if you want more "step by step" just tell, ok?

---

### Post by slira on 2007-09-21
> **macel82 said:**
> Ok I used Retrospect Express to duplicate all of the contents of D: onto my external Firewire drive.  So now there's a folder on my external with all of the contents of D: 

So now I need to boot the Ubuntu disc and do installation.  When I get to the partition part, can I reformat D: and break off 10 gb or so for Ubuntu?  Then once I do that, can I just go back into Windows and move all of the stuff back from my external onto the newly-partitioned and formatted D: ?   What about programs I have installed on D: ?   Is formatting and moving them all back gonna screw up the programs I have in there?  Or will everything run as normal once I put it back?  

I know these are a lot of questions, but this is the most important part for me because my Windows system now has like my whole life on it and I don't want to screw it up.  Once I get Ubuntu on there I'll be a lot more confident about learning Linux.  

Thanks

before installing, defrag D a couple of times and resize it with a partition manager from inside windows; you can shrink D and make room for unallocated disk space; it's much better to install in free space than over an existing partition. (after all done, just recopy your data to D, if some data was lost)

---

### Post by macel82 on 2007-09-21
> **slira said:**
> before installing, defrag D a couple of times and resize it with a partition manager from inside windows; you can shrink D and make room for unallocated disk space; it's much better to install in free space than over an existing partition. (after all done, just recopy your data to D, if some data was lost)

What partition software can I use?  Anything free?

And when I reformat D: what format do I use?  NTFS for the old D: stuff and what for the new partition?

---

### Post by tenjin1 on 2007-09-21
When you resize your windows partition, you shouldn't lose any data, but backing up files as you were instructed to do on your external firewire drive is smart just in case. You are basically taking the left over space from your windows NTFS partiton and seperating it into its own 10gb (or whatever size you go with) partition. Then reformat that 10gb partition with Ext3 filesystem for Ubuntu.

Usually what I do on a fresh install of Ubuntu, with Windows already installed....boot into live cd and then choose install. You are then presented with a graphical partition manager. Where you can do your partitioning.

I'm not sure what you have on D partition, as I know your C partition must have your Window system files. But if you are wanting to install on D then all data will be lost when reformatting to Ext3...unless you are resizing D's unused space into a  seperate partition and using that for Ext3, you should be fine.

With that being said, below is good advice
> **slira said:**
> before installing, defrag D a couple of times and resize it with a partition manager from inside windows; you can shrink D and make room for unallocated disk space; it's much better to install in free space than over an existing partition. (after all done, just recopy your data to D, if some data was lost)

Not sure of any free Window Partitioning apps, someone elase may be able to recommend something. I know Acronis is good in windows but I don't think its free. You can always try the the way I suggested above, booting into ubuntu livecd and do your partitioning from there.

---

### Post by maniac_X on 2007-09-21
> **macel82 said:**
> What partition software can I use?  Anything free?

And when I reformat D: what format do I use?  NTFS for the old D: stuff and what for the new partition?

go get GParted and burn the iso to make a bootable CD. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
This partitioner is prob one of the easiest to use because it's mostly visually interactive, very much like the Windows program Partition Magic.

My suggestion would be to delete the D: partion, resize and defrag your C: partition, and then install Ubuntu with the choice to use largest 
space available(**not entire disk**). It will create a partition of ext3 and also a extended partition inside of which it will create the swap partition. 

Once finished, have fun playing around.

---

### Post by e_james on 2007-09-21
Watch out for GParted CD, the newer versions may not boot properly. There seems to be a bug in the grub setup. I tried gparted-livecd-0.3.4-8.iso and gparted-livecd-0.3.4-7.iso and finally gparted-livecd-0.3.4-2.iso. The last one worked for me.

---

### Post by slira on 2007-09-22
Hi

you may use many; 2 examples

Paragon Partition Manager Professional v8.5

or 

EASEUS Partition Manager (this one has a demo version for free)

these are very easy and "graphic" partition managers, from inside windows.

If I were you I would not change C:/ because that's where your Windows OS is, and you do not want to mess with it....

You have 3 choices:
- resize D and manually install Ubuntu using the unallocated space, defining manually the partitions (see my previous post)
or
- resize D and let Ubuntu installer freely use the unallocated space
or
- resize D, format the unallocated space an then install ubuntu there

From my experience, the first (or second) choices works better; it is easier to install without errors on a free unallocated disk space.

If you need any help, just post or e.mail me.
best
slira

EDIT:
Just a note: if you resize D, the "old" part will remain NTFS; the "new" partition will be ext3 (and a swap). Ubuntu will be able to read ntfs; and for windows there is an application that allows reading ext partitions; but leave that for later on, after your ubuntu is running. You will have to deal with fstab. When you get there, we will help, do no worry.

EDIT 2
> **maniac_X said:**
> go get GParted and burn the iso to make a bootable CD. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
This partitioner is prob one of the easiest to use because it's mostly visually interactive, very much like the Windows program Partition Magic.

My suggestion would be to delete the D: partion, resize and defrag your C: partition, and then install Ubuntu with the choice to use largest 
space available(**not entire disk**). It will create a partition of ext3 and also a extended partition inside of which it will create the swap partition. 

Once finished, have fun playing around.

Be very careful using a bootable partition manager; I once did that and destroyed windows in the process; it is much safer to use a partition manager from inside windows. Since you have a D partition DO NOT in any case mess (resize or so) with the C (windows) there is no point on doing that and it is really dangerous for your W OS.

---

