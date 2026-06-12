---
title: "Triple Boot Macbook lost in action - lilo problem"
date: 2007-12-12
forum: Apple Intel Users
---

### Post by 2bord on 2007-12-12
Right,

so I tried installing Win XP, Ubuntu Mint, that's 7.10 methinks, and OS 10.5 on my Macbook.
Well, OS X was already on there, which is why I continued with Windows; worked like a charm.

Then I went on to Ubuntu and since I had read that if I'd instal the Grub the mbr would get messed up, I didn't. I then went for the [triple boot success]("http://ubuntuforums.org/showthread.php?t=187465") and followed the instructions on how to instal lilo, but ended up with 'lilo command not found' when I entered 'lilo -v -r /mnt' in terminal.

Well, now I'm stuck with Linux on the partition but without a proper bootloader.
Could anybody point me in the right direction on how to instal this with the live cd?

What is more, the gpt got kinda messed up in the procedure, I can't access my NTFS in OS X and now looks like this:

[INDENT]
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    193208655  Mac OS X HFS+
 3      193208656    212739906  Basic Data
 4      212739907    234441078  MS Reserved

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    193208655  af  Mac OS X HFS+
 3      193208656    212739906  83  Linux
 4 *    212739907    234441078  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 193208656:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 212739907:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 4, type MS Reserved
 Listed in MBR as partition 4, type 07  NTFS/HPFS, active[/INDENT]


Would it mess up the mbr or gpt if I'd remove the msftres flag with gparted???

Thanks in advance

edit: rEFIt is installed on hfs+

---

### Post by 2bord on 2007-12-12
Just found this [Booting/]("http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/")

Would it be possible to remove all the lilo stuff that I did when I followed the link in my first post and instal grub from the live cd, w/o installing the whole thing again??

bye

---

### Post by cyberdork33 on 2007-12-12
> **2bord said:**
> Just found this [Booting/]("http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/")

Would it be possible to remove all the lilo stuff that I did when I followed the link in my first post and instal grub from the live cd, w/o installing the whole thing again??

bye

I think so. do:
```
sudo apt-get install grub
``` to make sure you have grub on your system first, then follow the instructions in the link you last posted. You should be ok.

you can remove lilo too, if you want:
```
sudo apt-get remove lilo
```

---

### Post by 2bord on 2007-12-13
Well, I opted for the clean install since it takes only about 10min with mint. 
At the end of the install I moved grub to the liux partition in this case sda3 and did a reboot.

The only thing I got back was Grub loading stage2...

no error message, no choose your kernel stuff, just the curser blinking...
I checked the menu.lst but it seems to be ok. tried starting w/o any extras but didin't work either.

no idea what to do...anybody??

---

### Post by cyberdork33 on 2007-12-13
my guess is that somehow grub is getting confused by the two installations of linux. I don't know why... Probably just another Mac-unique issue.

Here is some information that might be helpful. Doesn't look like multiple versions of linux, but it is good info that may help in some aspect still... 
[http://forum.onmac.net/showthread.php?t=2793](http://forum.onmac.net/showthread.php?t=2793)


I can try an play around with something like this at home sometime. Sounds like this is going to be a trial and error type thing any way we play it.

---

### Post by 2bord on 2007-12-13
but I installed grub just one time and replaced the linux installation!
so grub ought to know where to find ubuntu.

I mean my partition table is still the same as above.

thanks anyway! I'll take a look at your link.

---

### Post by cyberdork33 on 2007-12-13
stage2 is where the menu to choose a kernel comes up, so if grub is unable to load that then you will never get the menu. 

i don't understand it if you only have one linux installation so far. What filesystem format are you using? ext3? Maybe it is an issue with Mint?

---

### Post by 2bord on 2007-12-13
I have OS X on my sda2 HFS+ , Mint on sda3 ext3 and WIn XP on sda4 NTFS.

 the filesystem is ext3, I'm using Mint (Darnya/Main) based on Gutsy (Gnome).

I thought that mint is basically ubuntu with another design, so it shouldn't be a mint issue, IF I'm not mistaken.

---

### Post by cyberdork33 on 2007-12-13
> **2bord said:**
> I have OS X on my sda2 HFS+ , Mint on sda3 ext3 and WIn XP on sda4 NTFS.

 the filesystem is ext3, I'm using Mint (Darnya/Main) based on Gutsy (Gnome).

I thought that mint is basically ubuntu with another design, so it shouldn't be a mint issue, IF I'm not mistaken.yes, understood, but I was thinking that maybe they have modified something, or used a newer/older version of grub for some reason. I have no idea. Anyway, it is not seeing the grub stage2 file which is on the partition with your OS (or just not loading it) for some reason, that is where the issue lies.

---

### Post by 2bord on 2007-12-13
hmm.. but the last time i checked stage2 was right beneath stage1 in /boot/grub among a couple of other stuff...

I'll just do another install since my knowledge of linux is just not sufficient enough to play around with grub, apart from reading text files like menu.lst?!
at least if you don't know what to do!

thanks

---

### Post by cyberdork33 on 2007-12-13
that is correct... but it can use stage1 because that is what gets installed (copied) to the MBR or the boot portion of the partition you specified. Normally, I would say that your menu.lst is wrong, and that is the issue, but what I saw looked good.

---

### Post by cyberdork33 on 2007-12-13
I found this:
[http://linuxmint.com/forum/viewtopic.php?f=46&t=7437](http://linuxmint.com/forum/viewtopic.php?f=46&t=7437)

I would post your issue there. It seems that there is something wrong with linux mint and grub on the Mac as others are getting the same issue. What you COULD try to do is install Ubuntu again, and copy the stage files over to your mint install, and maybe get a working system again.

---

### Post by 2bord on 2007-12-14
you were right! ubuntu installed and ran like a charm! seems to be a problem of mint when it installs the grub at another place but the mbr! I'll file some sort of complaint!

so if I'm right I'll use 

rm ----------------------
cp -------------------

right?

thanks a bunch

---

### Post by cyberdork33 on 2007-12-14
no don't do that... wow that would be bad, I would edit my post so as not to get others to do that... you almost never rm -rf anything. that is dangerous.

someone has a way to install a normal version of grub in mint here:
[http://linuxmint.com/forum/viewtopic.php?f=49&t=7522](http://linuxmint.com/forum/viewtopic.php?f=49&t=7522)

---

### Post by 2bord on 2007-12-14
that's strange coz I acctually did that and it worked fine at least in ubuntu when I restarted!

what should I use instead? or should I just try overwriting the stage2 file!
Or should I try the article way? I mean it SHOULD work the way I meant to do it, installing Mint now that I have the /boot on my external hd and replacing the mint one!

---

### Post by cyberdork33 on 2007-12-14
> **2bord said:**
> that's strange coz I acctually did that and it worked fine at least in ubuntu when I restarted!

what should I use instead? or should I just try overwriting the stage2 file!
Or should I try the article way? I mean it SHOULD work the way I meant to do it, installing Mint now that I have the /boot on my external hd and replacing the mint one!

well if you removed your /boot directory, that means you removed the kernels, the grub files and everything...

I would use the method in the article I linked to, although just copying the grub files from Ubuntu should work... (but you do not want to copy all the kernels and everything too, they can stay on your Ubuntu partition.

---

### Post by 2bord on 2007-12-14
will do as recommended! 

thanks a lot!

---

