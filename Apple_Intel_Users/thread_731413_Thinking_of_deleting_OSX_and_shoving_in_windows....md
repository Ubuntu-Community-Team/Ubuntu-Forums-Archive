---
title: "Thinking of deleting OSX and shoving in windows..."
date: 2008-03-21
forum: Apple Intel Users
---

### Post by ThatGuyThere on 2008-03-21
I have a few questions about deleting my Mac OS X partition and going all out windows/linux combo, as some stuff just doesn't work in linux. I have a few questions about it before I start:

Will rEFIt still work? I figure not, since it's on OS X. How will I be able to boot up then? 

Will Ubuntu loose any functionality? After all, i am planning on deleting the original operating  system...

EDIT: Another one... Would it be possible to just boot windows from a usb-harddrive? That would make it a lot easier, and i wouldn't have all of these questions :P

---

### Post by ThatGuyThere on 2008-03-21
bump

---

### Post by cyberdork33 on 2008-03-21
> **ThatGuyThere said:**
> I have a few questions about deleting my Mac OS X partition and going all out windows/linux combo, as some stuff just doesn't work in linux. I have a few questions about it before I start:

Will rEFIt still work? I figure not, since it's on OS X. How will I be able to boot up then? 

Will Ubuntu loose any functionality? After all, i am planning on deleting the original operating  system...

EDIT: Another one... Would it be possible to just boot windows from a usb-harddrive? That would make it a lot easier, and i wouldn't have all of these questions :P
Why in the world did you buy a mac if you don't want to use OSX? You could have gotten a much more Ubuntu-compatible machine...

rEFIt will still work, but I would suggest not deleting OSX entirely because that is the ony way to install firmware updates. If rEFIT gets messed up it will quit working and there will be no way to fix it too (not yet anyway).

Ubuntu doesn't care if you have OSX or not.

Windows can be made to install to a USB hard drive, but it doesn't work without some tweaking.

---

### Post by blznazn on 2008-03-21
If you get rid of OS X rEFIt won't work because it's installed on the OS X partition.  You can install Ubuntu with out OS X, but then I don't think you can install windows.  Mac's use EFI to manage partitions and things, but Windows still uses the BIOS and MBR.  The Windows Longhorn Beta supports EFI, but isn't used in the Vista final release.  I think though you'll have to install it using LILO instead of GRUB.

---

### Post by onshiv on 2008-03-21
...

---

### Post by blznazn on 2008-03-21
The thing about Macs are they seem really nice at first.  After awhile OS X isn't really the nicest thing ever.  OS X is very far behind with java, it doesn't use the hardware to the fullest (no 3d acceleration), it's not too good for development, it's very limitting, and just the hardwares sort of the only thing going for it, but then it's also locked down tight.

---

### Post by Stu09 on 2008-03-22
> **blznazn said:**
> The thing about Macs are they seem really nice at first.  After awhile OS X isn't really the nicest thing ever.  OS X is very far behind with java, it doesn't use the hardware to the fullest (no 3d acceleration), it's not too good for development, it's very limitting, and just the hardwares sort of the only thing going for it, but then it's also locked down tight.

Lol you could've bought something much more windows/ubuntu compatible for much less money if that's what you wanted.

---

### Post by robzon on 2008-03-22
I bought a MacBook not for OS X but for the hardware, the design and the overall look and feel of the _hardware_. Other notebooks were just plain ugly. MacBook is slick and ergonomic. And I'd rather pay Apple Tax than Microsoft Tax. Hardware compatibility is not the only thing to be considered when buying a notebook (though iit's probably #1 thing).

I know a lot of Linux users who bought MacBooks for the same reasons I did and there's nothing wrong with it. It's just a damn good piece of hardware. Getting everything to work well on Ubuntu took me a few hours, but now I'm VERY satisfied with it. So please stop telling people they shouldn't buy a MacBook for Linux if they want to.

---

### Post by blznazn on 2008-03-22
> **Stu09 said:**
> Lol you could've bought something much more windows/ubuntu compatible for much less money if that's what you wanted.

That's true lol, but like I never planned on originally putting Windows on it, and it is compatible with linux.  But like when I first got it, I didn't know about the EFI and all the problems it caused.

---

### Post by cyberdork33 on 2008-03-22
> **blznazn said:**
> If you get rid of OS X rEFIt won't work because it's installed on the OS X partition.
You can install it into the EFI partition as it really should be anyway.
> **blznazn said:**
> You can install Ubuntu with out OS X, but then I don't think you can install windows.  Mac's use EFI to manage partitions and things, but Windows still uses the BIOS and MBR.uninstalling OSX does not remove EFI or the MBR/BIOS emulation. It is part of the firmware. You can dual-boot windows and ubuntu if that is what you want.  
> **blznazn said:**
> The Windows Longhorn Beta supports EFI, but isn't used in the Vista final release.  I think though you'll have to install it using LILO instead of GRUB.Why is that? Grub will work fine.

> **Stu09 said:**
> Lol you could've bought something much more windows/ubuntu compatible for much less money if that's what you wanted.Exactly

> **robzon said:**
> I bought a MacBook not for OS X but for the hardware, the design and the overall look and feel of the _hardware_. Other notebooks were just plain ugly. MacBook is slick and ergonomic. And I'd rather pay Apple Tax than Microsoft Tax. Hardware compatibility is not the only thing to be considered when buying a notebook (though iit's probably #1 thing).and you deal with the limitations of that hardware choice. Functionality is more important than looks though if you ask me. Apple Tax / MS Tax, it makes no difference, you are supporting tha same thing on both sides of the fence.

> **robzon said:**
> please stop telling people they shouldn't buy a MacBook for Linux if they want to.I will not. For you it might be ok, but for the average user it is not a good choice and I am sticking by that. I am not saying there is anything wrong with putting other operating systems on your Mac, I just think it is pointless to buy a Mac (limited, locked-down, oddities, etc) to do what what you could pretty much do with a much larger variety of hardware, and do so much easier.

---

### Post by blznazn on 2008-03-22
Sorry about that then, just from other sources I looked at for getting linux on a mac brings up all those issues, when I look at them again they're back from 2006 I think :-\.

---

### Post by tvtech on 2008-03-22
I have a friend that has a macbook pro, and runs ubuntu and windows on it in dual boot with the Grub EFI loader.  works like a charm.  he also kept osx.  he was clever enough to buy a big enough hard drive for the matter
more to the point he kept his original osx installation on the hard drive that came with the machine and just installed a new hard drive.  he does use osx but was disenchanted with the newest update, although from what I hear it's getting better.  also you can enable x11 under osx and run with some tweeking 90% of the linux programs out there. this has to be done to run open office thanks to mac creating aqua for a window manager. 

check out this link for Grub-EFI related issues [http://packages.ubuntu.com/gutsy/admin/grub-efi]("http://packages.ubuntu.com/gutsy/admin/grub-efi")

---

### Post by cyberdork33 on 2008-03-23
It is interesting that he got Grub-EFI working... Most people are having issues with attempting that. Does 3D-acceleration work?

---

