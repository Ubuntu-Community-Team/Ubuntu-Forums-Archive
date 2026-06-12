---
title: "Boot from external usb DVD Drive with REFIT?"
date: 2008-07-23
forum: Apple Hardware Users
---

### Post by felixdzerzhinsky on 2008-07-23
Can you Boot from external usb DVD Drive with REFIT?

---

### Post by cyberdork33 on 2008-07-23
you should be able to without refit even.

---

### Post by felixdzerzhinsky on 2008-07-24
> **cyberdork33 said:**
> you should be able to without refit even.

Well I wouldn't be asking here if it worked!

I did try to hit the "c" key during the boot. But it does not seem to see my external DVD drive.

When the piece of junk apple DVD-RW used to work REFIT would see the Linux cd's and they would show up in the REFIT menu.

After having a heart attack when I heard how much the Apple DVD-RW drive would be I bought an external drive.

---

### Post by cyberdork33 on 2008-07-24
> **felixdzerzhinsky said:**
> Well I wouldn't be asking here if it worked!
If you are having a problem, maybe you should try asking about the problem and describe the issue you are having instead of asking some generic boot question. The answer to your question is 'yes', the extended answer is, 'you don't even need refit'. You never said anything about having tried, what you tried, and what failed.

So, I assume that you have tried this now, and you do not see the Disc in the rEFIt menu?

---

### Post by felixdzerzhinsky on 2008-07-25
I should have been more clear. Yes I have tried "c" after the chimes and there is no cd image in the Refit boot menu.

---

### Post by Kobalt on 2008-07-25
Have you tried holding the "alt" key at boot? This is how you can select boot drives (including external USB) on a Mac usually...

---

### Post by cyberdork33 on 2008-07-25
> **Kobalt said:**
> Have you tried holding the "alt" key at boot? This is how you can select boot drives (including external USB) on a Mac usually...
Yes, I would also try that.

You should also verify that the disc is even bootable in another machine.

---

### Post by felixdzerzhinsky on 2008-08-03
I have now tied the above. It did not work. I am wondering if the answer may be in this post:

[http://www.mac-forums.com/forums/showthread.php?p=404282](http://www.mac-forums.com/forums/showthread.php?p=404282)

**From the post: **
> Holding down various buttons during booting got me nothing but a the little question-mark-o-doom. But, I did manage to boot from the USB cd. I had to override the built-in firmware device alias for 'cd' and point it to the USB device:

Hold down CTRL+OPTION+O+F, hit power button, get a firmware prompt.
0> devalias cd /pci@f2000000/usb@19/disk@1
0> boot cd,\\:tbxi

Sadly, I haven't yet figured out how to permanently change the cd alias - whenver the system reboots, it comes back as the original alias pointing to the device that doesn't work. 

What's more - none of the Apple CDs want to boot from the USB drive. But, I've got Debian Linux up and running for the moment.

I'm a bit unsure of how to list my DVD drives under OSX. I suspect that REFIT may be looking at my old DVD drive and just needs to be pointed to the new external drive.

---

### Post by hajk on 2008-08-06
> **cyberdork33 said:**
> you should be able to without refit even.
Your answer surprises me! The OP is talking about an *external* drive, not the onboard drive. Now, you must know that booting from an external drive will only work if that drive is "blessed". An external USB or FW drive with another version of Mac OS X on it will boot from an external drive (as the Mac OS X reinstall DVD does). A "legacy OS" (like Windows or, indeed, GNU/Linux) will not, unless that drive was somehow blessed; it needs a GUID partition table and an EFI first partition, and must have gone through the blessing procedure... the problem is well-known to people wishing to boot GNU/Linux on a MacIntel machine from a USB-key. 

Correct me if I'm wrong about this, please.

---

### Post by cyberdork33 on 2008-08-06
> **hajk said:**
> Your answer surprises me! The OP is talking about an *external* drive, not the onboard drive. Now, you must know that booting from an external drive will only work if that drive is "blessed". An external USB or FW drive with another version of Mac OS X on it will boot from an external drive (as the Mac OS X reinstall DVD does). A "legacy OS" (like Windows or, indeed, GNU/Linux) will not, unless that drive was somehow blessed; it needs a GUID partition table and an EFI first partition, and must have gone through the blessing procedure... the problem is well-known to people wishing to boot GNU/Linux on a MacIntel machine from a USB-key. 
From my experience, Booting from external CD/DVDROM drives works... It is booting from an "installation" that does not work. I admit that I could be wrong though, and if I am, I apologize.

Also, are you saying that you CAN boot an installed system from USB if you bless the drive?

---

### Post by hajk on 2008-08-06
Well, no need to apologize, I know you're as interested as I am in finding out how booting a MacIntel machine from an external device can be done. 

I know for a fact that Mac OS X can be booted from an external device: I had my old MacBook single-booting GNU/Linux from the internal HD without rEFIt or Option-key: there was the familiar grey startup screen with a filefolder icon. Meanwhile, Mac OS X was cloned to an external FW drive, and it would automatically boot (with the familiar grey screen and Apple logo) when the drive was plugged in (again not touching any Option-key).

Now, people have been trying to boot GNU/Linux from an external device (like USB key), but this will not work when it is installed with an MBR partition table - EFI just plain doesn't see it, regardless of using rEFIt, holding down the Option-key or the C-key. I've read recently, though, that installing GNU/Linux on a blessed external device might do the trick - there would have to be synchronized GUID and MBR partition tables on the device...

I'm planning to test this as follows with that external FW drive: install Mac OS X Tiger on it and then also Ubuntu Hardy, just the same way it's done on the internal HD. If that external Hardy can be booted, then the Tiger partition could be removed and Hardy should still boot, right? Stay tuned...

Edit: don't even need to install that Tiger, just partition the external HD with diskutil...

---

### Post by cyberdork33 on 2008-08-07
> **hajk said:**
> I know for a fact that Mac OS X can be booted from an external device
Agree 100%. and to take it further, I think any system that can be executed from EFI directly can be external... i.e. refit, elilo, grub2

> **hajk said:**
> Now, people have been trying to boot GNU/Linux from an external device (like USB key), but this will not work when it is installed with an MBR partition table - EFI just plain doesn't see it, regardless of using rEFIt, holding down the Option-key or the C-key. I've read recently, though, that installing GNU/Linux on a blessed external device might do the trick - there would have to be synchronized GUID and MBR partition tables on the device... I think it sees it, it just fails to boot. and I don't know that the GPT matters either... Macs are fully capable os using MBR disks (even the main internal disk). The blessing might be different though. I can't remember anyone trying that.

> **hajk said:**
> I'm planning to test this as follows with that external FW drive: install Mac OS X Tiger on it and then also Ubuntu Hardy, just the same way it's done on the internal HD. If that external Hardy can be booted, then the Tiger partition could be removed and Hardy should still boot, right? Stay tuned...

Edit: don't even need to install that Tiger, just partition the external HD with diskutil...Sounds good. We might should take this to a new thread... Reference infromation is here ([http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)) I know it is really long, but that is basically a storehouse for info. Since we can't post to it anymore, I's suggest a new thread with your results and a link to this old thread for reference. Also note that user 'billbear' has messed with blessing a little bit, but I think only with blessing specific executables.

---

### Post by pxwpxw on 2008-08-07
The guid partitioning and efi are indeed the answer to usb stick booting (and I suspect other external enclosures ).  

Just  installed grub2-efi on a 2 GB usb stick, guid partitioniong, hfsplus 200MB partition.

It boots, and runs, and so can boot linux on the usb stick (will check that).

I have been playing with grub-efi and have it loading linux 2.6.26 custom kernel, agp=off
video=efifb, on MacBook c2d, and unable to get it booting from external or usb stick on other partitioning schemes,  this is very encouraging as grub2-efi works very well, here on the MacBook internal drive, booting linux, macosx and legacy grub all from grub2 menu  with a few rough edges. Also grub-efi has the added advantage being able to live on the Macosx partition where its grub.cfg is editable in Macosx, and it can load kernels from the same Macosx partition - to boot any external linux that the kernels can handle. And it is faster to load.
```

ads-computer:~ admax$ sudo gpt -r show /dev/disk1
    start     size  index  contents
        0        1         PMBR
        1        1         Pri GPT header
        2       32         Pri GPT table
       34        6         
       40   419712      1  GPT part - 48465300-0000-11AA-AA11-00306543ECAC
   419752  3019824      2  GPT part - 48465300-0000-11AA-AA11-00306543ECAC
  3439576   524295         
  3963871       32         Sec GPT table
  3963903        1         Sec GPT header

ads-computer:~ admax$ date 
Thu Aug  7 23:26:19 EST 2008
ads-computer:~ admax$ sudo su
ads-computer:/Users/admax root# cd
ads-computer:~ root# bless --info /Volumes/usb\ 1/efi/ 
finderinfo[0]:     26 => Blessed System Folder is /Volumes/usb 1/efi
finderinfo[1]:     74 => Blessed System File is /Volumes/usb 1/efi/grub/grub.efi
finderinfo[2]:      0 => Open-folder linked list empty
finderinfo[3]:      0 => No OS 9 + X blessed 9 folder
finderinfo[4]:      0 => Unused field unset
finderinfo[5]:     26 => OS X blessed folder is /Volumes/usb 1/efi
64-bit VSDB volume id:  0x3445D3DD33CB570B

```

And for rEFIt.efi, it boots for me also off hfsplus on an MBR external or an Apple external, but then its stuck because it has to
hand over to grub lilo or other bios/mbr  bootloader.


I find that grub1 on the internal hd can not see the guid/mbr usb stick, even after gptsync makes its  MBR partiton info. And refit can see the usb stick but cant load linux kernel, so when refit passes the boot to legacy grub, that gets nowhere. It can run grub.efi on the usb stick and it will load linux, but in that case may as well just boot grub2-efi initially (done that).

---

### Post by felixdzerzhinsky on 2008-08-12
> **hajk said:**
> Your answer surprises me! The OP is talking about an *external* drive, not the onboard drive. Now, you must know that booting from an external drive will only work if that drive is "blessed". An external USB or FW drive with another version of Mac OS X on it will boot from an external drive (as the Mac OS X reinstall DVD does). A "legacy OS" (like Windows or, indeed, GNU/Linux) will not, unless that drive was somehow blessed; it needs a GUID partition table and an EFI first partition, and must have gone through the blessing procedure... the problem is well-known to people wishing to boot GNU/Linux on a MacIntel machine from a USB-key. 

Correct me if I'm wrong about this, please.

Thanks for the tip with the Mac OSX Install DVD and holding down the Alt key. I did notice that my Linux partition is strangely named Windows [The Horror!] and I had to hold the alt key for about 10 to 15 seconds before the OSX DVD appears. 

At least I will be able to recover the empty space where OpenSolaris used to live using the OSX DVD.

---

### Post by cyberdork33 on 2008-08-12
Just to add to this thread. I just tried (again) to install Ubuntu to an external drive. It still did not work. I tried blessing the partition as well, and it did not work (in fact that really confused refit... I wouldn't recommend it.)

---

### Post by pxwpxw on 2008-08-13
**pxwpxw** said above -

> 
I find that grub1 on the internal hd can not see the guid/mbr usb stick, even after gptsync makes its MBR partiton info. And refit can see the usb stick but cant load linux kernel, so when refit passes the boot to legacy grub, that gets nowhere.



I now find that grub.efi will boot from a hfsplus (Macos extended) partition (and load linux kernel from ext2/3 or hfsplus) on guid, mbr, and apple partitioning. 

Tried so far on a 2GB usb stick and 300GB external firewire enclosure. This required simply preloading all the efi modules when using grub-mkimage to creating grub.efi (making it 328KB). 

It needs preloaded modules (file systems etc) to find itself, the modules and grub.cfg, else dropping back to rescue mode (not much use). The grub.efi image I tried initially (92KB) had only gpt and hfsplus modules preloaded. 
 
Still using the 2.6.26 kernel, and the MacBook c2d, will try 2.6.24  again with some re-configure, it has some EFI support, but don't expect success, 2.6.25 is reported usable from EFI boot.

I have been unable to get the ubuntu 804 grub-efi package to work, I am using the savannah gnu grub2 source current as at 2008-07-27. This has compiler options to generate grub for efi, pcbios (mbr), and ppc (replacement for yaboot?).

Savannah CVS Surfing - project grub - Index of /trunk/grub2 
[http://svn.savannah.gnu.org/viewvc/trunk/grub2/?root=grub](http://svn.savannah.gnu.org/viewvc/trunk/grub2/?root=grub)

Thanks to **Nosferax** for motivation and links.
[http://ubuntuforums.org/showthread.php?t=869324](http://ubuntuforums.org/showthread.php?t=869324)
 
How to test GRUB 2 on EFI
[http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)

How to test GRUB 2 on Macbook
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

**Attachment may work for a test**.

This is an i386 version, AKA grub.efi, with modules preloaded.

It should run standalone on macintel efi hardware. You can play with the grub> command line to see the file system and partition map capability.
It gives a 1280x800 resolution boot screen on my McBook. 

$ gunzip grub-svnx.efi.gz

insert grub-svnx.efi in the root of any macos extended partition and run it with rEFIt or bless it and run it direct.

It should give the familiar grub command prompt
grub>

help is good.

ls -l 
ls -l /
lists partitions (types) or files

set root=hd0,1
is partition 1 on first hd. (not hd0,0 like grub1)

search is handy

linux, initrd, boot
used for manual boot (successfully if the kernel supports efi).

Attachment superseded by later version in package at
[[COLOR="RoyalBlue"]grub2 EFI boot loader internal/external booting[/COLOR]]("http://ubuntuforums.org/showthread.php?t=995704")

---

### Post by hajk on 2008-08-13
> **cyberdork33 said:**
> Just to add to this thread. I just tried (again) to install Ubuntu to an external drive. It still did not work. I tried blessing the partition as well, and it did not work (in fact that really confused refit... I wouldn't recommend it.)I've been off the air for a few days after messing around with Hardy installed to an external FW drive... and hosing my Linux installation on the internal HD in the process while doing something stupid in sheer desperation to get Hardy to boot from the external HD. It wouldn't.

Then (for a change) tried to install Debian testing (Lenny) to the internal HD, and then something interesting happened: the installer recognized GPT and, without asking, installed Grub 2 (the package is called grub-pc in the Debian repositories). Except, now (after resynching the GUID and MBR partition tables) it wouldn't boot, despite the claim that Grub 2 is GPT aware. So, back to Hardy which installed old Grub, and all was well...

I'm letting this rest for a while...

---

### Post by cyberdork33 on 2008-08-13
> **pxwpxw said:**
> I now find that grub.efi will boot from a hfsplus (Macos extended) partition (and load linux kernel from ext2/3 or hfsplus) on guid, mbr, and apple partitioning.Just a Note, this will only be true on a Mac since Apple added a hfs driver to EFI for their machines... (Makes sense doesn't it?)

> **pxwpxw said:**
> Still using the 2.6.26 kernel, and the MacBook c2d, will try 2.6.24  again with some re-configure, it has some EFI support, but don't expect success, 2.6.25 is reported usable from EFI boot.Yay

> **pxwpxw said:**
> I have been unable to get the ubuntu 804 grub-efi package to work, I am using the savannah gnu grub2 source current as at 2008-07-27. This has compiler options to generate grub for efi, pcbios (mbr), and ppc (replacement for yaboot?).

Savannah CVS Surfing - project grub - Index of /trunk/grub2 
[http://svn.savannah.gnu.org/viewvc/trunk/grub2/?root=grub](http://svn.savannah.gnu.org/viewvc/trunk/grub2/?root=grub)

Thanks to **Nosferax** for motivation and links.
[http://ubuntuforums.org/showthread.php?t=869324](http://ubuntuforums.org/showthread.php?t=869324)
 
How to test GRUB 2 on EFI
[http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)

How to test GRUB 2 on Macbook
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

**Attachment may work for a test**.

This is an i386 version, AKA grub.efi, with modules preloaded.

It should run standalone on macintel efi hardware. You can play with the grub> command line to see the file system and partition map capability.
It gives a 1280x800 resolution boot screen on my McBook. 

$ gunzip grub-svnx.efi.gz

insert grub-svnx.efi in the root of any macos extended partition and run it with rEFIt or bless it and run it direct.

It should give the familiar grub command prompt
grub>

help is good.

ls -l 
ls -l /
lists partitions (types) or files

set root=hd0,1
is partition 1 on first hd. (not hd0,0 like grub1)

search is handy

linux, initrd, boot
used for manual boot (successfully if the kernel supports efi).

[COLOR=Red]The usual dire warnings apply.[/COLOR]
This might go well in a "Native EFI Booting Information" thread. and hopefully a discussion could ensue. I will link it in the FAQ as well.

---

### Post by pxwpxw on 2008-08-15
Working on it

grub.efi boots kernel 2.6.26-5-generic.

---

