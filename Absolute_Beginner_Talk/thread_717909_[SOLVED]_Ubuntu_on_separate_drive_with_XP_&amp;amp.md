---
title: "[SOLVED] Ubuntu on separate drive with XP &amp;amp; Vista on master"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Arch Parsons on 2008-03-07
Hello All! I just installed Vista along with XP and I am dual booting successfully. I was about to add Ubuntu 7.10 to the mix,and remembered that I have a small 20 gb hard drive in the case that isn't connected.  This drive is on the way out (crashed once), but it's working now and I thought it might do for trying out Ubuntu.  I'd like to have the system to provide a 3-way choice at startup.  If the Ubuntu drive crashes in the future, is that serious for the integrity of the other two OS's?  Any help or suggestions would be appreciated.

---

### Post by gpilkay on 2008-03-07
Upon install, Ubuntu WILL try to write Grub over the MBR (boot record) of the master drive.  This could cause some troubles.  However...

I have a similar setup with two IDE drives.  What I did to make sure my windows install didn't get botched was hook up the new Ubuntu drive as Master, with the Windows drive as Slave, with the switches set appropriately.  This way, Ubuntu got the full Master disk to itself and installed Grub there, while registering the Windows drives as boot options.  The windows bootloader was unaffected.

This way, if Ubuntu does explode, you just switch a cable and dip switch, and you're back to how you were with no troubles.

This was a Ubutu/XP system, though.  Not too familiar with the XP/Vista dual boot, but I'm sure others are!

---

### Post by juky on 2008-03-07
Maybe this will help (I am planning to do it soon):

```
http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu
```

A question:

Have two physically separated HDDs, with two partitions each. On first disk, first partition is XP system installed. Another partition on that disk is blank. On second disk, first partition is data storage partition, second partition is also blank. What do you suggest? 

Thanks
juky

---

### Post by Arch Parsons on 2008-03-07
What about if I temporariy disconnect the master disk and reset the jumper on the  slave to master until the installation is finished?

---

### Post by Arch Parsons on 2008-03-07
Or, on  a second though, is is risky to create a third partition on the master drive?

---

### Post by forestpixie on 2008-03-07
> What about if I temporariy disconnect the master disk and reset the jumper on the slave to master until the installation is finished? I think that if you do that when you then reconnect you'll boot the master with no choice of booting the slave. gpilkay has the best suggestion imo for this as it stands
I personally would install, let grub install to the mbr and if you haven't got the xp install disc to do the fixmbr, get a copy of supergrub - there is an option on that to fixmbr.


> Have two physically separated HDDs, with two partitions each... What do you suggest?
depending on size - install / and swap to first disc second partition, install /home on second drive second partition

---

### Post by forestpixie on 2008-03-07
> Or, on a second though, is is risky to create a third partition on the master drive?

not any riskier than any other partitioning expedition :)
make an extended and put all buntu partitions insside as logical drives

---

### Post by Arch Parsons on 2008-03-07
Thanks for your comments. To provide a little detail, my master drive is a Sata 320 gb drive.  I have it partitioned so that approx. 200 gb of unallocated space was divided into half with half to go to use with the existing XP and the rest for Vista plus its applications.  I used Magic Partition 8.0 to shrink the first  partition.  Can I use the same software to shrink the "Vista" partition to make space for the Ubuntu or do I have to let Ubuntu do that? Will Ubuntu still overwrite the MBR when it's installed?

---

### Post by Arch Parsons on 2008-03-07
How many partitions will I need?  What sizes do you suggest?

---

### Post by forestpixie on 2008-03-07
if you need to shrink the vista partition let vista do it - there have been reports of problems, don't know if it's changed

as far as space goes - what do you want to do with it, I have 8Gb for my / which is half empty, you'll probably want swap which depends on your RAM, you could have /home seperate or as part of the install 

I'm a bit unsure what you're saying about the unallocated space - but I woiuld guess if you can get 20Gb it should do for the moment

and yes installing buntu will overwrite the mbr

To give a bit more idea of what partitions you have if you boot the livecd - go to apps >accessories and open terminal - paste this command in and then post the output

```
sudo fdisk -l
```

if you decide toi type it - the l is a lowere case  L not a 1

---

### Post by gpilkay on 2008-03-07
Found the site I was looking for:

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2)

Not the best in the world but it gives some good details.

Also, have you considered Wubi?  [http://wubi.sourceforge.net/](http://wubi.sourceforge.net/)
They have a section right here in the forums, in the third-party projects.  It's a bit buggy from what I hear but it lets you try Ubuntu with no partitioning at all.

Myself, I use a VM on my Dell, which has maxed out its partitions.  Ubuntu didn't like to install to it so VirtualBox runs Ubuntu right within XP and it works great.  cntrl-F gives me a full virtual-linux laptop with no XP visible at all.

Just a few possibilities!  Good luck and let us know what you find that works!

---

### Post by Arch Parsons on 2008-03-07
In trying to do this I clicked on the executable file on the Ubuntu CD and it unex;ectly quickly installed without asking any questions.  I rebooted, expecting the worst, but when it booted it had XP, Viata, and Ubuntu all listed.  I opened Vista and when I got in there it opened up a chart showing the drives with an MBR and anoher file written to the slave drive.  Where do I go from here?  I have done no partitoning as yet.  I was going to mention that my two main partitions on the master drive are listed as C and E when I am in XP but as C and D when in Vista.  C is XP when I am in XP, but C is Vista when I am in Vista.  Also the slave drive comes up as G in XP but as E in Vista.

---

### Post by Arch Parsons on 2008-03-07
When I went back into XP it said Ubuntu was already installed and diid I want to uninstall it.  I clicked uninstall and the process seemed to complete normally.  Will wait til tomorrow to continue thiis. Hopefully my mind will be clearer then.

---

### Post by gpilkay on 2008-03-07
Is this 7.10 or 8.04?  8.04 is expected to ship with Wubi as a feature, that would fit with what you're describing.  The previous release has no from-Windows installation.

What Wubi does is use a big file on the hard drive AS its hard drive, similar to a VM, so you don't have to partition anything.

If you have Ubuntu or Wubi under your Windows add/remove programs, it has been installed through that means.  I'd take a look at the Wubi forum, though, as it has its own quirks.  Still a great way to get started, though, as if you're like me, partitioning stinks.

---

### Post by Arch Parsons on 2008-03-07
I have Ubuntu 7.10.  The other software is completely foreign to me.  I'll have a look at your link. Thanks

---

### Post by Arch Parsons on 2008-03-08
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x07510751 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       23738   190675453+   7  HPFS/NTFS 
/dev/sda2           23739       38914   121893888    7  HPFS/NTFS 

Disk /dev/sdb: 20.0 GB, 20020396032 bytes 
255 heads, 63 sectors/track, 2434 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x135e135e 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        2433    19543041    7  HPFS/NTFS 
ubuntu@ubuntu:~$

---

### Post by Arch Parsons on 2008-03-09
Thanks for the various comments up to now. I'm still waiting for Forestpixie to comment on the Ubuntu screen output above  (perhaps tomorrow).  I'm on the verge of going ahead with the install.  Like most people I'm mostly concerned with not damaging my exisitng (dual boot) setup.  I'm pretty vague on this partitioning stuff and how it's done  within the Ubuntu install and whether or not I will get to a point in the partitioning process where I won't know what to enter to get the desired result. I have never had the need to use the Vista partitioning software.  The advantage of using my  master drive is that it's a relatively new disk  and dependable.  My only reason for waniting to use my second drive (IDE now slave) is that it's there.  I have had lots of trouble with this disk coming and going in the past, so it's probably better to use if for something non-vital (whatver that might be) or to simply toss it out, although it seems to be  usable at the moment. I have done all kinds of tests on this disk without being able to ascertain what the problem has been in the past.

---

### Post by Arch Parsons on 2008-03-10
This morning I started by opening Partition Magic inside XP and it said there was an error in the partition and did I want to fix it. I said yes and it answered that the error was fixed.  When I looked at the partitions, though, it listed the whole drive as one partition with the word BAD in place of NTFS.  This did not affect the dual booting, though, and everything looked the same insider MY Computer.  then I went into Vista and sucessfully used Shrink to divide that partition. I ended up with roughly two halves.  Now I have 55 mb of unallocated space for Ubuntu.  I was not able to shrink the unallocated space, though, so I don't know how to creae the swap parition..... Should I shrink the Vista parition a second time to create the swap space?

---

### Post by Arch Parsons on 2008-03-10
I'm a little impatient so I keep replying to myself.  I found a pretty good guide on manual partitioning on this site:  [http://digitalgraphy.wordpress.com/tag/manual-partition/]("http://digitalgraphy.wordpress.com/tag/manual-partition/")
The best part was that the manual partitioning screen was enlargeable to full-screen size  by clicking on it a couple of times. I'm approaching the point at which I expect to start the install.  It would be nice to have some more 1 on 1 human assistance, though.  I did another sudo fdisk -l output and got this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07510751

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23738   190675453+   7  HPFS/NTFS
/dev/sda2           23739       31640    63467201    7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x135e135e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2433    19543041    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

Which parts of this am I going to see when I get to the manual insall screen.  

The only difference I see since creating the two partitions within the Vista section is in the line 
/dev/sda2           23739       31640    63467201    7  HPFS/NTFS

The End point is 31640 whereas the other day the End point was
38914.

I was expecting to see the new partition on a separate line.  

This is vital because I have to know which partition is the unallocated space.

I could add that I tried using GeParted 0.3 and had all kinds of difficulties, especially video problems, and I couldn't see any grab handle to resize a partition.  That's why I had to scrounge a copy of Partition Magic 8.0 which worked like a charm.  

I'm still vague about what to expect and what to enter in the manual paritioning screen. Can you see the new 55 gb partition in  the screen output above?  Many thanks in advance for any further assistance.

---

### Post by Arch Parsons on 2008-03-10
OK I started the installation...

The earlier posted link states:

Create three partitions out of thefree space you can see.

One will be swap (set it to 512mb-this is more than enough)

The other one is a small ext3 partition (put it 50Megs) and mount it to /boot (Very important to do that!!)

Then the rest will be all the free space available; use ext3 as file-system and mount it to ‘/’


I thought I was clear on everything.  I did see the unallocated space no problem, which I selected to partition.

My doubts are with the partitioning windows.

Each asks if I want a primary or logical partition.  I'm not sure of the correct answer to this.

Each asks Location - beginning or end.  I'm not sure of the answer to this either.

Each asks Mountng point.  Again I'm not 100% sure what to enter in each case.

I cancelled until I could research these topics further....

---

### Post by forestpixie on 2008-03-10
ok - hi and that is a serious amount of writing 

from what I can see you've not created any partitions as yet - 
1st-
> 
/dev/sda1 * 1 23738 190675453+ 7 HPFS/NTFS
/dev/sda2 23739 38914 121893888 7 HPFS/NTFS

/dev/sdb1 * 1 2433 19543041 7 HPFS/NTFS 

2nd
> /dev/sda1 * 1 23738 190675453+ 7 HPFS/NTFS
/dev/sda2 23739 31640 63467201 7 HPFS/NTFS

/dev/sdb1 * 1 2433 19543041 7 HPFS/NTFS

but you do now appear to have missing space on sda - which I hope is where you were expecting it 

firstly unless you've some pressing need to do so I wouldn't bother putting /boot seperate, if you don't give it enough space and you get kernel updates and don't keep on top of it - you won't be able to boot

you'll still need 3 partitions if you want to have a /home seperate

In the unallocated space make an extended partition  - then inside that make 3 logical partitions - 1 each for / , /home and swap

How much space have you got? Is this it, although I assume you meant 55Gb? > Now I have 55 mb of unallocated space for Ubuntu.

I'd do 10Gb for your root, 1Gb for swap and the remainder for /home

If you're using the manual partitioner in the installer - make the 10Gb, format to ext3 and give it a mountpoint of / , then do the home - make it 45Gb and give it mountpoint /home , finally use the remaining space for swap - format it as swap and you won't need to do mountpoint.

---

### Post by Arch Parsons on 2008-03-10
With a lot of trial and error I got to the point where it wanted to format the three partitions that I had created.  I noticed that when I clicked the advanced button it indicated position of boot loader hd(0).  What does this mean?  What will this do with my present boot loader for XP and Vista? Thanks in advance for any comments.

---

### Post by Arch Parsons on 2008-03-10
Mission Accomplished.  I now have a functioning triple boot system!  Thanks to Forestpixie and the others!  Thanks to the thousands who made this awesome piece of free software possible.  The only thing left to do is to edit the bootloader.  It's a bit of a tree now wherby I have to go into the Vista option and then XP and Vista both come up.  It's now 9:30 p.m. here and the old eyes are a bit weary.  That's a job for tomorrow.  Meantime, I'll have a deeper look at Ubuntu!

---

