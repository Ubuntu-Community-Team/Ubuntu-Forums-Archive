---
title: "i8042 error making it impossible to run ubuntu"
date: 2015-04-01
forum: Apple Hardware Users
---

### Post by ian82 on 2015-04-01
[COLOR=#333333][FONT=UbuntuRegular]I've searched high and low on the internet to find a solution. I am so new to Ubuntu that I haven't even been able to get it to install. I downloaded Ubuntu from the main page, burned it to a disk, have it pop up with rEFIt,and get three options: Book EFI\book\boot64x.efi, Boot EFI\boot\grubx64.efi, and Boot Legacy OS. These lead to options to try ubuntu, install, etc. When I click try ubuntu, it goes to a black screen with an error i8042: No controller found. I can't seem to find any solutions on any of the other threads that bring this up. Can someone help? I've read things about changing something to nomodeset, but I have no idea if that would help or how to get there. I would absolutely love to use Ubuntu, but this is getting a tad frustrating. Please help![/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]*I've also tried to load it via USB, with the same results.[/FONT][/COLOR]

---

### Post by este.el.paz on 2015-04-03
> **ian82 said:**
> [COLOR=#333333][FONT=UbuntuRegular]I've searched high and low on the internet to find a solution. I am so new to Ubuntu that I haven't even been able to get it to install. I downloaded Ubuntu from the main page, burned it to a disk, have it pop up with rEFIt,and get three options: Book EFI\book\boot64x.efi, Boot EFI\boot\grubx64.efi, and Boot Legacy OS. These lead to options to try ubuntu, install, etc. When I click try ubuntu, it goes to a black screen with an error i8042: No controller found. I can't seem to find any solutions on any of the other threads that bring this up. Can someone help? I've read things about changing something to nomodeset, but I have no idea if that would help or how to get there. I would absolutely love to use Ubuntu, but this is getting a tad frustrating. Please help![/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]*I've also tried to load it via USB, with the same results.[/FONT][/COLOR]

@ian:

There is a lot to learn to get an installed system set up, probably best if "dual-boot" next to OSX.  But, we need more information to offer real help; although I've posted here so many times answering the same questions it's clear that folks are not searching the forum first before posting, or searching Google for forum posts relating to their problem . . . .

The usual questions . . . what computer are you using?  Have you downloaded the "live desktop iso" or, some other option like "netboot"?  Which version of Ubuntu?  Did you check the "md5sum" number of the file before you burned it to a DVD?  And, lastly, if you are running a version of OSX that is later than 10.7 I believe, then you should install rEFInd . . . not rEFIt . . . .

I suggest that use the "live" or any iso that says "desktop" . . . check the md5sum to confirm that the file is not corrupted, and then after burning, put the DVD in the optical drive, reboot, when the screen goes black hold the "c" key down . . . that should boot the DVD or whatever is in the drive . . . directly . . . no rEFInd window should open.  And, then see what happens . . . you might need some boot parameters to get display working . . . or not.  First step is try to boot the "live" system . . . before trying an install.  Then before trying an install, thoroughly read at least "rodbooks" posts on dual-boot installs . . . only caveat being I suggest not using Boot Camp to partition your HD, just use Disk Utility . . . to set up some area as "free space" . . . it seems the linux installer can recognize that better . . . .

e...

---

### Post by bigknowz on 2015-04-16
> **ian82 said:**
> [COLOR=#333333][FONT=UbuntuRegular]I've searched high and low on the internet to find a solution. I am so new to Ubuntu that I haven't even been able to get it to install. I downloaded Ubuntu from the main page, burned it to a disk, have it pop up with rEFIt,and get three options: Book EFI\book\boot64x.efi, Boot EFI\boot\grubx64.efi, and Boot Legacy OS. These lead to options to try ubuntu, install, etc. When I click try ubuntu, it goes to a black screen with an error i8042: No controller found. I can't seem to find any solutions on any of the other threads that bring this up. Can someone help? I've read things about changing something to nomodeset, but I have no idea if that would help or how to get there. I would absolutely love to use Ubuntu, but this is getting a tad frustrating. Please help![/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]*I've also tried to load it via USB, with the same results.[/FONT][/COLOR]

Can you use a DVD to install?  I tried for days with USB and SD Cards, wouldn't get past the controller error.  From DVD it works as expected.

---

