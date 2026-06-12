---
title: "[SOLVED] Whoops."
date: 2008-12-16
forum: Apple Hardware Users
---

### Post by Cadeyrn on 2008-12-16
Stupid Mac and it's automatic-apply. Once on my Mac side, I accidentally clicked on Startup Disk when I was aiming for something else in preferences, and because I used my Windows side to launch the Live Ubuntu Preview, and installed Ubuntu over my Windows side, wiping it; instead of Boot Camp, Mac recognizes my Ubuntu partition, yet it's grayed out on Disk Utility and when I click Mount, literally nothing happens. And that specific partition is not an option under Startup Disk.

Of course I can still get into Ubuntu by holding down Alt, but I reeeeeeealy hate having to press Alt at the PERFECT time every time I start up. I was digging around through my Mac system files and Google, looking for a way to force my computer to automatically boot into sda4 (my Ubuntu partition), and ended up learning a lot about the famous BootX file. I have no idea how I'd acces or edit it, nor do I know if it would fix my problem.

But anyway, I need some help with this. How do I FORCE Mac to boot into a hidden partition???

---

### Post by cyberdork33 on 2008-12-16
> **Cadeyrn said:**
> Stupid Mac and it's automatic-apply. Once on my Mac side, I accidentally clicked on Startup Disk when I was aiming for something else in preferences, and because I used my Windows side to launch the Live Ubuntu Preview, and installed Ubuntu over my Windows side, wiping it; instead of Boot Camp, Mac recognizes my Ubuntu partition, yet it's grayed out on Disk Utility and when I click Mount, literally nothing happens. And that specific partition is not an option under Startup Disk.
sounds all normal to me.

There are no drivers for the linux filesystem for osx, thus it is greyed out and inaccessible from OSX. 

You should never use the Startup Disk utility to select Linux to boot anyway as there is no equivalent tool in Ubuntu to change it back to OSX later.

> **Cadeyrn said:**
> Of course I can still get into Ubuntu by holding down Alt, but I reeeeeeealy hate having to press Alt at the PERFECT time every time I start up. I was digging around through my Mac system files and Google, looking for a way to force my computer to automatically boot into sda4 (my Ubuntu partition), and ended up learning a lot about the famous BootX file. I have no idea how I'd acces or edit it, nor do I know if it would fix my problem.

But anyway, I need some help with this. How do I FORCE Mac to boot into a hidden partition???BootX is for PowerPC Macs. If you have an Intel Mac, what you want is rEFIt.

---

### Post by Cadeyrn on 2008-12-16
> **cyberdork33 said:**
> 
You should never use the Startup Disk utility to select Linux to boot anyway as there is no equivalent tool in Ubuntu to change it back to OSX later.

Well, I can always hold down ALT when the computer is starting up, click on my Mac partition, and use Startup Disk to set Mac to the default again.

> **cyberdork33 said:**
> BootX is for PowerPC Macs. If you have an Intel Mac, what you want is rEFIt.

Where is that? I'm looking around for it now, but it's hard to find.

EDIT: Hey! I was poking around my hidden files that can only been seen from Linux and I found an exact copy of Ubuntu's / directory (AKA file:///) under Mac's /private/tftpboot/private/tftpboot

EDIT2: I just checked out my system bin files (/sbin) and found a mount file for every file system Mac is compatible with. All I'd have to do is find one on the internet for ext3, right?

---

### Post by Cadeyrn on 2008-12-16
Alright, I found a way to mount ext3 systems on a Mac with no risk, no problem, but they're speaking in Mac/Linux console language. I used to be a total Windows person and am a complete newbie at Mac/Linux console stuff. Someone translate???

[http://forum.insanelymac.com/index.php?showtopic=34227](http://forum.insanelymac.com/index.php?showtopic=34227)

---

### Post by Cadeyrn on 2008-12-16
BUMP.

I'm impatient.

---

### Post by cyberdork33 on 2008-12-17
> **Cadeyrn said:**
> Where is that? I'm looking around for it now, but it's hard to find.
Well, when I google "refit" the first result is a link to the page for the software, so I don't know how you could have missed it.

> **Cadeyrn said:**
> Alright, I found a way to mount ext3 systems on a Mac with no risk, no problem, but they're speaking in Mac/Linux console language. I used to be a total Windows person and am a complete newbie at Mac/Linux console stuff. Someone translate???

[http://forum.insanelymac.com/index.php?showtopic=34227](http://forum.insanelymac.com/index.php?showtopic=34227)
Ignore that. Basically they are using a very old, out-of-date driver that was being worked on at one time. it is not very reliable if you can even get it to work at all. You can download it and try it if you like:
[http://sourceforge.net/project/showfiles.php?group_id=64713](http://sourceforge.net/project/showfiles.php?group_id=64713)

I'd start with the 1.3 version as it has been reported by many that the 1.4 version doesn't work at all anymore. It should add an icon to system preferences that you can use to mount your Linux partition (if it works).

---

### Post by Cadeyrn on 2008-12-17
Oh. Damn.

Well, a bigger problem now is suddenly my two external hard drives are suddenly hfs+. My Linux partition can't edit what's in them, and one of them is read as a 700 GB partition with many copies of the original drive, each being the size of the original drive. I can't format them, so I tried unmounting, and that didn't help. I think, though, since my Mac side can access them, I'm gonna try formatting them to what Mac calls "MS-DOS File Type" or something like that. Though I have no idea if that means FAT16 or FAT32.

---

### Post by cyberdork33 on 2008-12-17
> **Cadeyrn said:**
> Oh. Damn.

Well, a bigger problem now is suddenly my two external hard drives are suddenly hfs+. My Linux partition can't edit what's in them, and one of them is read as a 700 GB partition with many copies of the original drive, each being the size of the original drive. I can't format them, so I tried unmounting, and that didn't help. I think, though, since my Mac side can access them, I'm gonna try formatting them to what Mac calls "MS-DOS File Type" or something like that. Though I have no idea if that means FAT16 or FAT32.
should be fat32.

NTFS is another option

---

### Post by Cadeyrn on 2008-12-17
Yeah, NTFS is more powerful, but it's inferior to ext3, plus only Windows can use it without special drivers that must be found manually.

Come to think of it, each operating system has its own powerful file type that's incompatible with any other system without drivers. Windows has NTFS, Linux has EXT, and Mac has HFS. I know HFS+<NTFS<EXT3, but why can't we all get along and use somethine universal that's more powerful than FAT32, which, by the way, sucks when used in Vista?

---

### Post by Chrisj303 on 2008-12-17
I tripleboot OS X/Ubuntu/Windows on my Macbook Pro.

I have used the ext2 filesystem for my Ubuntu partition - this way, the extfsmanager drivers work perfectly on OS X.

---

### Post by cyberdork33 on 2008-12-19
> **Cadeyrn said:**
> Yeah, NTFS is more powerful, but it's inferior to ext3, plus only Windows can use it without special drivers that must be found manually.Understood, but ntfs-3g is installed by default in Ubuntu, and it is not that hard to find for OSX... plus it is a much better filesystem then FAT32.

> **Cadeyrn said:**
> Come to think of it, each operating system has its own powerful file type that's incompatible with any other system without drivers. Windows has NTFS, Linux has EXT, and Mac has HFS. I know HFS+<NTFS<EXT3, but why can't we all get along and use somethine universal that's more powerful than FAT32, which, by the way, sucks when used in Vista?HFS+ is actually not a bad filesystem, it is just getting aged.
There were some big updates to FUSE recently and I think that Unix File Systems (UFS, but not the Apple variety) will now work in Ubuntu and OSX. You could probably get ZFS running in Ubuntu if you really HAD to.

> **Chrisj303 said:**
> I tripleboot OS X/Ubuntu/Windows on my Macbook Pro.

I have used the ext2 filesystem for my Ubuntu partition - this way, the extfsmanager drivers work perfectly on OS X.yes, but then you lose journaling which makes it about as good as fat32.

---

### Post by Cadeyrn on 2008-12-19
Whoops again--double post.

---

### Post by Cadeyrn on 2008-12-19
Ugh, well I'll see if my dad, who's a computer nerd who totally knows his stuff but uses Mac anyway (WTF???) can help with my problem when I see him in a few days.

Oh wait, I think he uses Mac because he gets paid bank to take pictures and/or write books about using new Apple products and software.

---

### Post by Chrisj303 on 2008-12-20
> **cyberdork33 said:**
> 

yes, but then you lose journaling which makes it about as good as fat32.

I don't use Ubuntu for anything other than dicking about with CompizFusion and internet browsing, filesystem limitations really don't bother me as it isn't my primary (or even secondary) OS.

Being able to write to it from OS X does come in handy though..

---

### Post by Cadeyrn on 2008-12-22
Well, it looks like if and when there's a solution, I won't find it here.

Marking it solved.

---

### Post by cyberdork33 on 2008-12-24
> **Cadeyrn said:**
> Well, it looks like if and when there's a solution, I won't find it here.

Marking it solved.
IDK why you say that, I would say that if and when there is a solution, I would expect it to pop up pretty quick on the forums here.

---

