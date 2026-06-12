---
title: "Ubuntu 7.10 + Strange HD configuration"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2007-12-30
Hi there, let me start by saying that I am long time computer literate, but (very) short time Ubuntu literate, so complex command line explanations will confuse me no end!

Okay, so Iv used Ubuntu before, for a short time, on a borrowed laptop, and I was very impressed with it and Id like to try it for myself. However, I have a rather strange HD setup, and I'm completely unsure what is the best route to installation.

I have 2 HD's

HD 1
This is the main boot drive and contains the C: drive as well as drives D:, E: and F:, all of which are contained within an extended partition.

HD 2
This is a large data drive and it contains 2 partitions, G: and H

Questions:
Is it possible to install Ubuntu on F:, which is within the extended partition on HD 1?
Alternatively is it possible to install Ubuntu on G: or H:?
Depending on the answers for those two questions, what would I do about the boot manager and where would it go, and, more importantly since there is some important data on several drives, would the boot manager for the newly installed Ubuntu find and be able to access the current windows installation? (I dont want to find that Ubuntu boots fine but I suddenly have no boot access to my current windows installation!)

Sorry if thats a bit confusing, but I'm a little lost with this. Please feel free to interrogate me and force me to divulge any relevant information that Iv missed!

Thanks

Max

---

### Post by SOULRiDER on 2007-12-30
You can install ubuntu anywhere you want.
GRUB, the bootloader should go into the MBR of hte first drive (you can install it on any partition too if you want i believe). The installed will configure GRUB so that you can select which OS it is you want.

I hope thats what you wanted to know, but post again if its not and we'll try to help out.

---

### Post by phidia on 2007-12-30
It would be helpful to know the size of the partitions. If you are worried about installing and particularly booting (multi booting) then you might want to consider using the windows boot loader. A link for doing that is [here]("http://www.linuxsolved.com/linux-forums/linux-tutorials-how-tos/booting-linux-from-windows-boot-loader-how-to-dual-boot-a-t17.0.html") and there are many other how tos for doing that.
I like using that alternative install image of Ubuntu because it allows more options for installing and having said that the normal desktop version of Ubuntu should recognize your windows install and provide an entry in grub for booting windows. 
Which drive to install to will depend on how much space you want to devote to Ubuntu and how much space is available on the 2 drives you're considering.

---

### Post by MaxVK on 2007-12-30
Thanks for your quick responses!

Okay, firstly, I was looking to install Ubuntu onto either the F: drive, which is 18 Gig but exists inside the extended partition of HD 1, or on H: on HD 2, which is 80 Gig.

My concerns about booting are a newcomers paranoia that I'm sure you've seen before, where I'm worried that Ubuntu will trash my ability to boot into my existing windows installation, or, should I need to remove Ubuntu, that it will render the whole machine inoperable.

I like the idea of using the windows boot manager rather than GRUB, mainly because it keeps me within my comfort zone, although having briefly browsed the link I can see that a fair bit of time will need to be taken to familiarize myself with the whole procedure.

Assuming that I am able to install Ubuntu on ANY of my partitions, I would be inclined to choose F:, which is all but redundant now anyway, and I would try to go with using the windows boot manager, which will leave me feeling more comfortable with the whole thing.

Very many thanks for your help so far, and I would just like to ask if there are any avoidable pitfalls or other considerations to think about before I make a start.

Max

---

### Post by SOULRiDER on 2007-12-30
I recommend you use GRUB. When you install it it will detect your windows installation, but int he rare case that it doesnt you can still add it manually, which is actually a piece of cake, so dont worry about it.

---

### Post by jken146 on 2007-12-30
I second that suggestion.  The installer will automatically give you GRUB and add Windows to your boot options.  If you remove Ubuntu it's not that hard to put the Windows bootloader back (piece of cake if you have a Windows CD).

Welcome to Ubuntu, by the way!

---

### Post by MaxVK on 2007-12-31
Thanks guys. I'm aiming to get Ubuntu installed either today (New years eve! Ha!) or sometime before the weekend, so no doubt Ill be back and forth to these forums on a regular basis until I'm familiar with things. I think Ill follow your advice and use GRUB, since it seems to be the easiest way to go, but its good to know that you guys are here and prepared to help the helpless!

Have a good New Year celebration guys.

All the best

Max

---

### Post by pilli on 2007-12-31
I'd agree with the above two posts as well.  If, in the unlikely event that you wish to remove Ubuntu you can restore the windows bootloader with the windows CD.  Recovery consol>type fixmbr.

---

