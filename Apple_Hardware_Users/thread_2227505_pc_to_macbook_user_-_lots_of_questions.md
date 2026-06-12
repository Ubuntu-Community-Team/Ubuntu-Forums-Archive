---
title: "pc to macbook user - lots of questions"
date: 2014-06-02
forum: Apple Hardware Users
---

### Post by dhawk3122 on 2014-06-02
I haven't used Ubuntu or linux in a while, since switching to Mac years ago actually. I always used Ubuntu though dating back to the original 04.10 release. After switching to Macs I never installed linux again due to the lack of support and complex install methods. My gf wanted to play around with linux so I booted it up on my custom built HTPC. She quite liked Ubuntu and asked if we could easily install it on her 2013 MBA--and I have the 2012 MBA. Since I haven't used linux in a long time I thought I'd start here. After looking around I have more questions than I started with though so I'm hoping people will bare with me and help me out. 

1) Can Ubuntu 14.04 be installed from the USB livecd on an MBA?
2) Do Macs still require software like rEFInd to boot Ubuntu? Or can will it boot straight into Grub the same as a PC does?
3) Any chance of installing linux via bootcamp?
4) If my gf decides to delete Ubuntu is it easy to remove Grub for the stock OSX EFI bootloader?
5) Is the multitouch/gesture trackpad on the MBA actually usable in Ubuntu? It's abysmal in Windows. The trackpad is one of the best features of the MBA. It'd be a shame to lose that. 
6) If Windows is installed via bootcamp, will Grub seemlessly handle the triple booting? Or would one have to select OSX then hold down the alt key then select Windows via the bootcamp loader thingy?

I'm guessing nearly all of these questions are more general to linux on a MBA rather than just Ubuntu. Sorry for all the newb questions. Linux has progressed quite a bit since I last used it, esp around EFI/UEFI.

---

### Post by zircon_34 on 2014-06-03
> 
[COLOR=#000000]1) Can Ubuntu 14.04 be installed from the USB livecd on an MBA?
[/COLOR]
[COLOR=#000000]Yes it can, no problem!
[/COLOR]> [COLOR=#000000]
2) Do Macs still require software like rEFInd to boot Ubuntu? Or can will it boot straight into Grub the same as a PC does?
[/COLOR]
Some people say not but I don't see why not using rEFInd and I don't see why using Grub should be better. I like rEFind because it lets you choose easily the OS to boot and its fast, I also managed to install a dual boot on Mac without GRUB at all. But generally if you install refind, you will click on linux and the grub will start and boot into linux. It makes life easier for first install, especially if you are a newbie like me... then you can either remove it or remove Grub, but thats more tricky.

And for people finding the rEFind ugly, you can easily customize the background image, the icons, to get something very stylish!

> 
[COLOR=#000000]3) Any chance of installing linux via bootcamp?
[/COLOR]
no only windows...
> [COLOR=#000000]
4) If my gf decides to delete Ubuntu is it easy to remove Grub for the stock OSX EFI bootloader?
[/COLOR]
Yes, you just delete the EFI folder from reFind.
> 
[COLOR=#000000]5) Is the multitouch/gesture trackpad on the MBA actually usable in Ubuntu? It's abysmal in Windows. The trackpad is one of the best features of the MBA. It'd be a shame to lose that. 
[/COLOR]
I did not try all, but scrolling with two fingers and magnifying goes flawlessly with Xubuntu at least.
> 
[COLOR=#000000]6) If Windows is installed via bootcamp, will Grub seemlessly handle the triple booting? Or would one have to select OSX then hold down the alt key then select Windows via the bootcamp loader thingy?[/COLOR]

Don't know this one....

---

### Post by este.el.paz on 2014-06-03
> **zircon_34 said:**
> [COLOR=#000000]
[/COLOR]
no only windows...

I did not try all, but scrolling with two fingers and magnifying goes flawlessly with Xubuntu at least.

Don't know this one....

@D & Z:

Wanted to add some comment, but the "reply with quote" feature doesn't show the OP questions.  I've done a fair amount of installs of linux on MBP . . . there is/was a rodbooks wiki on installing linux on mac where he recommends using Bootcamp to preserve some features, like the camera, etc.  So, for my first install of dual boot system I went that way; however, after Mavericks came out I wanted to have triple boot system, but BC had locked the disk, it was no longer possible to alter the disk partitions.  This was before I had (recently) more or less found out about the "mactel ppa" stuff (still don't know all the features of that ppa) which apparently is to provide more features that the mac provides . . . but, the LM system wasn't providing all the features, and, more irritatingly, the touchpad features were pretty basic and there is/was some bug that would cause the cursor to jump around and in the process highlight data and then erase it.  Solution: disable tap to click--i.e., the touchpad features in OSX don't seem to be well supported . . . .

So, in terms of dual boot; if you think you won't ever want to change the disk, then you can install linux by way of BC, but, really you don't need it, you can partition the disk in Disk Utility in OSX . . . either leaving OSX intact (but needs to go in first) and then "installing next to" or using the linux install GParted Disk Utility to set up your linux partitions and then running the install . . . .  Seems like rEFInd might not need GRUB, but it doesn't take much space; I put mine after the OSX partition so that if I boot w/o holding the option key the computer will boot to OSX normally; some people seem to want GRUB in front.  rEFInd goes into the OSX system . . . you can read about that on the rodbooks wiki.

Thirdly, right, you'll have to figure out what's happening depending upon what you have installed . . . for my now triple boot, booting "normally" with no keys takes me to my 10.6.8 partition; if I hold the option key it goes to the OSX bootloader and I have 4 disks to select, 2 for OSX, 1 that says Windows but is actually Xubuntu 14, and 1 that is Recovery for OSX . . . .  If I select OSX disk 2, that is where rEFInd is loaded and then we get the options from it and I could select any system; if I select Windows I go to the GRUB window . . . .  Perhaps it's redundant, but, in the past if there was no GRUB linux would not boot . . . again, it doesn't take much space.

e.e.p.

---

### Post by zircon_34 on 2014-06-03
Agree with e.e.p. disable the tap to click feature, which is annoying, then the trackpad worked nicely for me...:) (I don't use this feature anyways...)

---

