---
title: "Use BIOS to choose Vista or Ubuntu?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by porcorosso on 2007-08-30
I had a laptop's modular bay hard drive (on which I had Ubuntu) die on me.

I did have GRUB on the internal drive, dual booting between Vista and Ubuntu. But I "fixed" the Vista drive so that it is now using the Windows boot loader again.

I spend a lot of time using a DVD writer in that modular bay location instead of the hard drive. This time I want to just install Ubuntu on that second drive and put GRUB on that drive, leaving the Windows boot loader alone on the first drive.

When Ubuntu was installed before it listed the Windows drive as /dev/sda0 and the Ubuntu drive as /dev/sda1.

I'll be installing Ubuntu 7.04 from a USB-connected DVD drive. How do I make sure that GRUB gets put on the SECOND drive, and not the first one -- so that I can just use the BIOS' F12 option to choose the hard drive I'm booting from?

If this were a desktop I'd just disconnect the first hard drive during the Ubuntu installation, but that's not so easy to do on a laptop.

---

### Post by Happy_Man on 2007-08-30
I believe that right before you click "install" in the LiveCD install utility, there is a button called "Advanced." Click that, and you should be able to configure what HDD GRUB is put on.

---

### Post by LaRoza on 2007-08-30
> **porcorosso said:**
> 
I'll be installing Ubuntu 7.04 from a USB-connected DVD drive. How do I make sure that GRUB gets put on the SECOND drive, and not the first one -- so that I can just use the BIOS' F12 option to choose the hard drive I'm booting from?

If this were a desktop I'd just disconnect the first hard drive during the Ubuntu installation, but that's not so easy to do on a laptop.

I would disconnect the drive, but I believe you can choose which drive to install grub. In case it doesn't work the first time, get the Super Grub Disk, so you can restore the MBR on the Windows hard disk.

---

### Post by porcorosso on 2007-08-30
Thank both of you for the suggestions.

**Happy_Man:** I should have mentioned that I saw the advanced options during a previous installation. The problem was that, when it came time to choose where to put GRUB, I was supposed to edit the choice. Instead of referring to the location as sda0 or sda1, it was using a notation something like this --

hd0(0,0)

-- If I remember correctly. I tried changing it to hd1(0,0), figuring that was the logical choice. But I got an error message when I tried to proceed from that point.

If you, or someone else, can give me a pointer here about this nomenclature or convention, I would appreciate it.

**LaRoza:** Thank you for suggesting Super GRUB as a possible means of fixing things if a accidentally wind up putting GRUB on the wrong disk. I had a moderately difficult time restoring the Vista boot loader without it when my Ubuntu drive died. I'll go looking for it right now.

------------------

If anyone can give me a bit more precise idea of how I might go about designating that modular bay drive as the recipient of the GRUB installation, I would appreciate it. I think that the error message I received before might have been issued because of the boot order sequence in the BIOS settings program. Is there some particular order I should use, like say --

1. external USB-connected DVD drive (for the Ubuntu LiveCD)
2. modular bay hard drive
3. internal hard drive

-- or should I just leave the setup with the internal drive to boot first, followed by the modular bay drive?

----------------

I just read up on Super GRUB. It appears to be a pretty useful tool, but I'm left with the question: Can it really restore the original Windows Vista boot loader if I accidentally wipe it out by installing GRUB on that first drive? (The Vista boot loader is quite a bit different from the one used in WinXP and Win2000.) Just wanted to be sure. What I've read so far indicates that it can get Windows booted if something goes wrong with GRUB on a dual boot system, but it said something about it having the equivalent of fdisk /mbr. That doesn't work for Vista.

---

### Post by sailor2001 on 2007-08-30
if I'm not mistaken...... once you are in windows you can 'FIXMBR'.........to restore your boot loader. someone who uses windows can help you out on that

---

### Post by porcorosso on 2007-08-30
Yeah, I'm a long-time Windows user. FIXMBR and FDISK are no longer part of the deal in Vista. The type of boot loader was totally changed around. The basic tool for dealing with the boot loader is now BCDEDIT. The loader is fixable after it has been replaced by GRUB, but it's a pain in the butt. I'd rather just get this right this time around.

I'm looking forward to getting Ubuntu running on this system again. I really like it, and find the man pages / yelp, not to mention Web sources like this forum, to be a hoot to use.

As I've said elsewhere, Ubuntu (along with all of the Open Source software available to run on it) is one of the best boxes of toys I've ever seen!

---

### Post by Happy_Man on 2007-08-30
Try using this site to figure out how to get GRUB to install how you want it to. [http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

---

### Post by porcorosso on 2007-08-30
Thank you, Happy_Man. That's an outstanding page. I'm saving that one for reference.

I think I've got this figured out -- from a "static" standpoint. The problem is that it has been pointed out to me (elsewhere) that some BIOSes do this differently from others.

I'm hoping to be able to hit the F12 key at boot time and choose between Vista and Ubuntu. Here's the problem. Apparently some BIOSes actually switch the boot order on the fly at this point. If that's the case, and if I've installed GRUB on hd(1,0), is the system looking at the modular drive as hd(1,0) or as hd(0,0)?

I guess the only way to find out is to install to hd(1,0) with the boot order set to normal (DVD-internal hdd-modular hdd) and try it out to see.

Above all else I just don't want to kill that Vista boot loader again.

---

### Post by oomingmak on 2007-08-30
> **porcorosso said:**
> I'm hoping to be able to hit the F12 key at boot time and choose between Vista and Ubuntu. Here's the problem. Apparently some BIOSes actually switch the boot order on the fly at this point. If that's the case, and if I've installed GRUB on hd(1,0), is the system looking at the modular drive as hd(1,0) or as hd(0,0)?

I guess the only way to find out is to install to hd(1,0) with the boot order set to normal (DVD-internal hdd-modular hdd) and try it out to see.

Above all else I just don't want to kill that Vista boot loader again.
I've been stung by this crappy Ubuntu implementation of grub before.

In fact my very first experience with Ubuntu (or any Linux at all come to that) was to have my Windows MBR trashed. This was despite the fact that I had gone out and purchased a second hard disk specifically for the purposes of putting Ubuntu on, so that **nothing** would touch my precious Windows data on my main hard disk. This was back in the days of Dapper (when there was no options for grub at all) and so Ubuntu would quite happily write to a totally different drive (other than the one that you'd told it to install to) and would overwrite your MBR without so much as a warning or prompt. 

In my particular case, not only did Ubuntu's install write to my Windows drive without my consent, but it also totally destroyed its ability to boot, so that I was left with nothing working at all. I was apoplectic with rage, because at the time I had no idea how to fix it, and I didn't know whether all of my Windows data had been permanently lost due to Ubuntu's reckless behaviour.

[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG]  **[COLOR=DarkOrange][http://ubuntuforums.org/showthread.php?p=1937710&post1937710](http://ubuntuforums.org/showthread.php?p=1937710&post1937710)[/COLOR]**

These days in Feisty there is the option (hidden under the vaguely-named 'Advanced' button) to chose where grub should be installed, but although this is better than having no option at all, it's still a half-ar$ed implementation. 

As you rightly point out Porcorosso, there is no consistency between drive naming between the disk partitioner and grub installer, but worse still it doesn't cater for BIOS based boot device switching, so it's useless when using F12 / F8 to change boot drives.

When you switch boot devices in BIOS, the boot device becomes Hd0,0 but if you set grub to install to Hd0,0 during install then it will wipe your MBR. If you set it to install to anything other than Hd0,0 then it won't work because the drive will be the first drive (i.e. Hd0,0) when you switch boot devices in the BIOS!  ](*,)

What I do now (because I have 3 disks, but only 2 of which are bootable) is to set the grub placement to anywhere **other **than zero (so that I know my Windows drive is safe). Then after install is complete I reboot (at which point it inevitably breaks because it can't load) but I just hit e to edit the boot menu and change the setting to hd0,0. This allows you to start Ubuntu. Once Ubuntu has loaded, I go and edit menu.lst to make the Hd0,0 setting change permanent. So from then on it boots fine without any intervention required. 

It's a clunky procedure that really should not be required, but it's the only thing that works until Ubuntu fix their grub install process.
  
Not long after I first started trying out Ubuntu I posted on here that I had tried out Foresight Linux. Disk Druid (the partitioner that comes with Foresight) does a way better job of grub installation than Ubuntu. Not only does Disk Druid use *consistent* drive naming throughout the entire Foresight install process, but it also doesn't restrict you to cryptic 4 character names that leave you guessing which drive it's referring to. You can see the full drive make and model, as well as the device name, so it's easy to tell which drive is which. 

When it comes to installing grub in Disk Druid, you can specify the drive order that is **going** to be used (rather than being forced to use the *current* drive order). Only then do you specify where grub should be installed. So even though your Linux HD is currently Hd1,0 during the install process, you can just move it up the boot list so that it becomes the first drive (hd0,0) and then you can select to have grub installed there as Hd0,0 (but without ever touching your Windows drive).

This means that when you switch boot devices in BIOS (and your second drive suddenly becomes the first drive) it still boots just fine, because grub was written to the drive with the expectation that it would be the first device.

[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG]  [COLOR=DarkOrange]**[http://ubuntuforums.org/showthread.php?p=2558032#post2558032](http://ubuntuforums.org/showthread.php?p=2558032#post2558032)**[/COLOR]

I have no idea why grub installation is so appallingly implemented in Ubuntu.

---

### Post by porcorosso on 2007-08-30
Thank you for that information, oomingmak.

That's pretty much what I think I'll be facing with this system. I've made a note of the process you outlined, and I'll probably give it a shot tomorrow -- or maybe over the weekend.

Very much appreciated. And I hope the Ubuntu distro folks are watching for a way to improve this particular behavior. There really are good reasons for not overwriting the other operating system's boot loader on a dual/multi boot system. That consideration shouldn't make it so hard to come up with a multi-boot system.

It's supposed to be about choices.

---

### Post by gn2 on 2007-08-30
I had dreadful experiences with GRUB  when I first started using Ubuntu, but discovered that my BIOS would give a "Boot device selection menu" at boot time.
.
If you have this option available by pressing F8 or whatever key, physically remove the Vista hard drive, and install Ubuntu to the other hard drive. Then put the Vista drive back.
.
Now set the BIOS boot order to have the desired default OS first in the list.
Then you will only have to use F8 (or whatever key) to boot the second OS.
.
After you have Ubuntu installed this way you will have to configure access to the Vista drive if you want to use files on it in Ubuntu.
.
The Hermanzone is absolutely essential reading and I too highly recommend it. (Link in sig)
.

---

### Post by porcorosso on 2007-08-30
Thanks, gn2.

I plant to give it a shot tomorrow. I'll post back to let you folks know how it goes.

It will be interesting to see if this model will boot with the primary drive moved. I guess it should do so, but it just seems weird to do it that way. I don't know why, really. I wouldn't worry about it all if I were doing the same thing with a desktop unit, now would I?

:)

---

### Post by porcorosso on 2007-08-31
It was really easy to just handle this in the manner to which **oomingmak** referred.

It really would be better if the installer made allowances for this sort of thing. There are lots of advantages to dual booting this way. If you have OS1 on one drive and OS2 on another drive, and the boot loader for OS2 resides on the OS1 drive, and the OS1 drive goes toes up -- what then? Yeah, it can be fixed. But people who have multiple drives and who can devote one drive (or more) per OS are better off doing it this way. Then, no matter what they do with the boot configuration or other parameters of one OS won't have any effect on the other OS(es). Just makes sense.

Thanks, **oomingmak** for the confirmation that this was a solvable, if slightly arcane, problem. And thanks to everyone else who participated for trying to provide guidance to a stubborn old guy who just couldn't see why he should have to physically disconnect a drive to keep and installer from messing with it!

:lolflag:

In case anyone is thinking of doing the same thing, **oomingmak** and I weren't really very precise or complete about the process. The point is that ALL of the references to linux boot options in the /boot/grub/menu.lst file have to be changed to (hd0,0). And I simply commented out the references to other operating systems and Vista/Longhorn because I didn't want the chainloader to be attempting to access that other drive if I got dumb and chose it from the GRUB menu. I can start Windows without any help from GRUB, thank you. And I can start Ubuntu without relying on a GRUB installation sitting on a Windows drive. Just the way I like it.

BTW, though, each time that GRUB gets edited automatically now, the values get set back to (hd1,0). I don't know enough about the OS yet to know what I would have to change to get the system to use (hd0,0) in the future, like for kernel updates, for instance. Somebody know?

---

### Post by oomingmak on 2007-08-31
> **porcorosso said:**
> It was really easy to just handle this in the manner to which **oomingmak** referred.
I'm glad that you managed to get it working the way you like it. I only gave a broad overview of what I do to get round the issue, so it's good to know that you figured out the necessary details.



> **porcorosso said:**
> It really would be better if the installer made allowances for this sort of thing.
No kidding! 

I'm surprised that Ubuntu lets this poor state of affairs continue, especially as the installer is one area in which they have full control (unlike many other problems  in Ubuntu that require upstream fixes). Other distros seem to manage to have a sane grub installer, so I don't see why Ubuntu can't sort its mess out.



> **porcorosso said:**
> There are lots of advantages to dual booting this way. If you have OS1 on one drive and OS2 on another drive, and the boot loader for OS2 resides on the OS1 drive, and the OS1 drive goes toes up -- what then? Yeah, it can be fixed. But people who have multiple drives and who can devote one drive (or more) per OS are better off doing it this way. Then, no matter what they do with the boot configuration or other parameters of one OS won't have any effect on the other OS(es). Just makes sense.
I agree entirely with you. I know that my BIOS isn't going anywhere, so it will always be there to allow me to switch drives (regardless of what software may try to do to my boot sectors). It also means that if I can restore disk images at will, without having to worry about how other OS's or partitions might be affected.
 


> **porcorosso said:**
>  Thanks, **oomingmak** for the confirmation that this was a solvable, if slightly arcane, problem.
You're welcome. :)

Thanks for coming back to let people know that it worked for you.

---

### Post by porcorosso on 2007-09-07
Just to answer my own question at the end of my previous post in this thread --

> BTW, though, each time that GRUB gets edited automatically now, the values get set back to (hd1,0). I don't know enough about the OS yet to know what I would have to change to get the system to use (hd0,0) in the future, like for kernel updates, for instance. Somebody know?

There is a reference about groot in the menu.lst file. I was ignoring that reference to hd --

```
# groot=(hd1,0)
```

-- because, after all, there was a "#" at the front of the line. It hadn't occurred to me that, although the line was "commented out", it could still be used as a reference! I changed it to --

```
# groot=(hd,0,0)
```

-- then deliberately invoked a function to cause grub to be updated. This time it all happened without me needing to edit menu.lst again. Nice.

---

