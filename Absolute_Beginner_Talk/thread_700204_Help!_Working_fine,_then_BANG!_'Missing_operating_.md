---
title: "Help! Working fine, then BANG! 'Missing operating system'"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2008-02-18
Gutsy working fine for a few weeks - every few weeks it has a catastrophic break-down - then suddenly I can't anywhere with it - I start the computer, and I'm told 'Missing operating system', end of story.

I put in the alternative CD, to go into the rescue mode, but haven't a clue what to do.  Seems to be prompting me to install all over again, when presumably there an error with something like GRUB.

So, how do I get access back to operating system?

Thanks.

---

### Post by hyper_ch on 2008-02-18
download the SuperGrub disc and reinstall grub again. That should fix the problem.

---

### Post by getmeoutofhere on 2008-02-18
But surely there should be a way to reinstall grub from the alternate CD for gutsy (live cd doesn't seem to work for me)

---

### Post by candtalan on 2008-02-18
If it was a grub related error I think that grub would probably declare a grub error (number) or be mentioned at least. 

What is the machine - has it got only ubuntu on it? Has it got any other boot loader in addition to grub?

The BIOS initially uses its information to look at the booting hard drive MBR which  then points to grub information (I think....)

Your error suggests that the bios is sometimes not finding the correct hard drive (?). Is your hard drive set to be master? Worth checking all cables are snug and firmly in place maybe.

hth

---

### Post by candtalan on 2008-02-18
> **getmeoutofhere said:**
> But surely there should be a way to reinstall grub from the alternate CD for gutsy (live cd doesn't seem to work for me)
You will need to be actually running a basic OS so that files can be managed, so a live CD is one way of getting a working OS. I think the supergrub disc is a (small) live cd which may run even though your machine is too small (or slow) for normal ubuntu live cd.

The alternate cd only includes enough to manage the install process I guess, maybe not grub separately.

---

### Post by getmeoutofhere on 2008-02-18
The computer is a laptop, pretty new, though I see what you mean with the GRUB error - there was no message.  I'll see if I can get a livecd to work.

---

### Post by hyper_ch on 2008-02-18
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=grub&titlesearch=Titel](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=grub&titlesearch=Titel)

---

### Post by geo909 on 2008-02-18
> **getmeoutofhere said:**
> But surely there should be a way to reinstall grub from the alternate CD for gutsy (live cd doesn't seem to work for me)

Yes, indeed. For example:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
But it would be helpful if you answered candtalan's questions.

And if it's just a GRUB problem, SUPER GRUB DISK seems to do the job automagically

---

### Post by getmeoutofhere on 2008-02-18
Sorry, the computer is a Dell 6400 laptop.  It only has Ubuntu on it.

The supergrub disk didn't work - it ddin't behave as suggested, and I got an 'Error 15 file not found message.

As a further problem, although I can load a 7.10 livecd, I can't find any of my old Ubuntu files.  I also tried a Puppy Linux LiveCD, and I can't find my old file system.  In particularly home/myname/Desktop

Any idea how I might be able to find it?  Then I can back my stuff up before doing a clean install.

Thanks.

---

### Post by getmeoutofhere on 2008-02-18
Any ideas how to recover my filles?  Can't seem to access sda2, where I think they are, in the livecd.  Thanks.

---

### Post by justleen on 2008-02-18
so you booted both Ubuntu live cd and puppy, and you cant see your disk?

Sounds like your bios/system cant access the disk at all, considering what you've told us so far.. THe BIOS cant access the disk, the rescue and live CD's do boot, but cant access the disk..
you could try to mount the disk buh hand, from a liveCD ?


```
$  sudo mkdir /media/temp
$  sudo mount /dev/sda2 /media/temp
$  ls /media/temp
```

---

### Post by getmeoutofhere on 2008-02-18
Thanks, but that doesn't seem to work.  Any idea what to do in an emergency?  Got a deadline, my work is locked inside my computer.  I really though I could trust Ubuntu/mycomputer - though it seems that it might be the computer's fault, not Ubuntu's.  Surely there's got to be a way to get the stuff out?  I there anyone you can call up and pay by credit card?

---

### Post by Tatty on 2008-02-18
Are you sure its sda2?

For the sake of completeness do:

```
sudo fdisk -l
```

And see if you can spot your missing disk there...

If its not there then it probably is a hardware problem... have you checked all the cables to make sure the hard disk is plugged in properly?

I had a similar problem recently with a friends XP computer which couldnt seem to find the operating system, but it started working after i unplugged the hard drive and plugged it back in - something must have worked loose somewhere.

---

### Post by getmeoutofhere on 2008-02-18
It's a laptop, so cables are probably not the issue.  And that command doesn't work...

ubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found

---

### Post by Tatty on 2008-02-18
> **getmeoutofhere said:**
> It's a laptop, so cables are probably not the issue.  And that command doesn't work...

ubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found

Apologies, a typo from me there, there is supposed to be a space between the fdisk and the -l, (and thats l as in a lowercase L), so it should be:

```
sudo fdisk -l
```

Ill amend my above post too

---

### Post by getmeoutofhere on 2008-02-18
It seems to be there...

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       14331   115065562+   7  HPFS/NTFS
/dev/sda3           14332       14593     2104515    f  W95 Ext'd (LBA)
/dev/sda5           14332       14593     2104483+  dd  Unknown

So, that's a start.

---

### Post by justleen on 2008-02-18
is it a dual boot system by any chance? (then it would be sda2)

if so, can you still boot from windows, and access that partition? (see the partition in disk management)

edit: just saw your reply.. its NOT sda2, thats for sure.. thats your windows drive..
 its sda5:  But thats an unknow partition, so linux doens recognize it as a linux file system...you could try mounting it though, as ext3

---

### Post by getmeoutofhere on 2008-02-18
No, it's not dual boot.  Would installing Windows help me get to the files?  I though Linux files were unavailable via Windows.

---

### Post by zerhacke on 2008-02-18
> **getmeoutofhere said:**
> /dev/sda3 14332 14593 2104515 f W95 Ext'd (LBA)


> **justleen said:**
> its NOT sda2, thats for sure.. thats your windows drive..

This is not a windows partition.  This is the standard extended partition that Ubuntu creates to house the swap file.  sda2 does look like an NTFS windows partition though.

---

### Post by getmeoutofhere on 2008-02-18
Well, I talked to a few computer experts - who weren't Linux specialists - and the consensus seems that if I want access to my data I'm going to have to pull out the HD from my laptop and connect it to something else.  Does that sound reasonable?

---

### Post by getmeoutofhere on 2008-02-18
GParted says flags SDA2 with an yellow triangle with an exclamation mark.  It says it doesn't know what the filesystem is, and suggests that it might be corrupted.  Anyway I can repair it?

I tried -y fsck, etc, but that didn't work.

---

### Post by paydaydaddy on 2008-02-18
Just a stab in the dark here, but I had a similar problem a couple of weeks ago. It turned out that the bios on my motherboard had a setting in the advanced chip functions that allowed the choice of "priority boot device". It had somehow gotten changed so that it was seeking a removable disc. By selecting the proper boot device I fixed the problem. May not be your problem, but you might have a look. On mine, the option to select the priority boot device was buried fairly deep in the bios and was not related to the standard "select boot sequence (floopy, cdrom, hdd)". If all else fails, you can slave the hard drive to another machine to access the files. Depending on the machine that you connect to, it may require adapter cables. I feel your pain and hope you find a quick fix.

---

### Post by getmeoutofhere on 2008-02-18
Thanks paydaydaddy, I looked around my BIOS settings and couldn't find anything that equated to your suggestion.  Evidence from elsewhere suggests some form of corruption.  There are, it seems, programs for making mirrors, but I haven't got 100 GB+ of spare space anywhere.  And I only need a few M of data!

---

### Post by Irihapeti on 2008-02-18
This may or may not relate to you but might be worth a look. I just happened to see it yestereday.

[http://ubuntuforums.org/showthread.php?t=606345](http://ubuntuforums.org/showthread.php?t=606345)

The fact that your machine is a Dell is what caught my attention.

---

### Post by Lord DarkPat on 2008-02-18
it happened to me due to extensive formatting again and again.
I doubt it has anything to do with GRUB, but you could try.
I took out my hard drive once and once I put it back in, it had no data, and I still don't have any idea why or how it happend.
I think you should put it in an external case and check the files.

---

### Post by getmeoutofhere on 2008-02-20
Thanks everyone for all the help.

Irihapeti, I doubt that was the problem - the HD did seem corrupted. 

While I wasn't able to restore the OS, I was able to get the files back.

Fortunately I had enough free space on the HD to install Windows.  I was not able to use the SDA2 space - GParted would not allow me to shrink it, I think because it was corrupted.  Perhaps one should bear that in mind - if you use all the space available you could be in trouble.  Though I you have a SWAP file of at least 2 Gigs you can remove it and use the space to install Windows - though I don't think that would give you enough room for XP or Vista!  Some Linux distros would need much less space.  

Having installed Windows, I purchased for $45 a program for restoring Linux files, and I ran it on Windows.  I suppose I could have have installed a light version of Linux on the free space, and found a piece of software that ran on Linux rather than Windows.

The trial version of the software listed my missing files, and once I'd paid the money, and upgraded to the full version, I was able to move them onto an external hard drive.

I have no idea whether free recovery programs are available, but I was happy to pay the $45.  There are a number of linux recovery programs available.  The one I went for was at [http://www.recoverdatatools.com](http://www.recoverdatatools.com) . I'm not saying that it's better than any other one available, but it worked for me.

---

### Post by Irihapeti on 2008-02-20
Great to hear that you've rescued your files.

There are Linux recovery tools on the GParted liveCD, on the Parted Magic liveCD and on systemrescuecd. However, when you are up against a situation like the one you described, it's not the best time to be learning how to use them :)

I ran Vista Home Basic at one stage, and I noted that the system files took up about 8 GB. That didn't include the application programs. I think I got my Vista partition down to about 20 GB before I removed it. So you wouldn't get a modern version of Windows in 2 GB.

---

