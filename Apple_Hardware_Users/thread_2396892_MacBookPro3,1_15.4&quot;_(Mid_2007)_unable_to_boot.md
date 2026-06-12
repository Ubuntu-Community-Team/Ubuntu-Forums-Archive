---
title: "MacBookPro3,1 15.4&quot; (Mid 2007): unable to boot from a live USB"
date: 2018-07-22
forum: Apple Hardware Users
---

### Post by allamistakeo19 on 2018-07-22
Hi, 

Has anyone ever managed to boot from a live USB on a MacBookPro3,1 15.4" (Mid 2007)? 

I've just spent my week-end trying various things, but never got very far. I'm new at this though, so I was hoping the community would point me out to things I haven't tried yet. 

What I have tried: 


[LIST]
[*]I've been trying with Ubuntu 18.04 Desktop AMD64, but I'm open to other versions and flavors. I just want a version that will remain supported for a few more years. In contrast, Mac OS X El Capitan (the last macOS version supported by this MBP) will reach end-of-life support this Fall &#8212; hence the motivation to migrate to Linux.
[*]The first thing I did is install rEFIind, following the instructions [here]("https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733"). This seems to be working, even though I realized later that this probably wasn't even needed to boot from USB (the Mac boot loader is sufficient).
[*]I then went on to create a bootable USB using UNetbootin, following the instructions in the previous link. That didn't work, in that the USB would not show up in any boot loader (neither rEFInd nor when starting the Mac while holding the ALT key). I think I have identified that this was due to the fact that the instructions mentioned using the GUID Partition Map, while I should have used MBR.
[*]Once I had an MBR live USB created using UNetbootin, I got all the way to GRUB 2, but when selecting the first option (to boot from the live USB), all I got was a black screen. Following the previous instructions, I tried with the "nomodeset" and "nvidia.modeset=0" options, but that didn't help.
[*]When I try to check the disk, I still get a black screen, and after a while I get the following errors: "Couldn't get size: 0x800...0e" and "MODSIGN: Couldn't get UEFI db list". A search on the web suggests that this may be an unrelated, non-fatal error.
[*]I then tried various other ways to produce the live USB. For instance, I tried without UNetbootin, using [dd]("https://askubuntu.com/questions/86/how-do-i-create-an-ubuntu-live-usb-using-a-mac") instead. I also tried Etcher.
[*]At some point I got an error message "error: file `/boot/' not found". A search on the web brought up a [thread]("https://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/") about ISO-2-USB EFI-Booter for Mac, so I gave it a try as well. It took several long minutes to complete the "Loading RAMdisk" step, and then it got stuck for hours at the "Fasten your seat belts" step.
[*]I've also tried to burn a DVD instead of USB, but my "Super Drive" is not being very "super" anymore, i.e. I can't get it to burn anything other than my time.
[/LIST]

Suggestions on what to try next would be very welcome. Thanks a lot in advance!

---

### Post by yancek on 2018-07-22
Given your inability to boot the usb on your Mac, the first thing I would suggest doing would be to try to boot on another non-mac if you have one to see if it boots thus eliminating that as the problem.
Is your Mac EFI compatible?  I'm not sure an 11 year old computer would be.  I'm not familiar with or at least never used rEFind but my understanding is that it is used to boot EFI systems installed rather than a usb.  You should have some method of selecting the usb to boot.

Maybe reading the Ubuntu documentation on UEFI install/boot at the link below will help, at least check through the General Principles section.  You need to know whether your Mac is EFI or not as you need to install Ubuntu the same.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by howefield on 2018-07-22
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by allamistakeo19 on 2018-07-22
Thanks for your very fast response! 

Here is what I found:
[LIST]
[*]The live USB boots on a PC.
[*]The live USB also boots on a slightly more recent MacBook Pro (15-inch, 2.53GHz, Mid 2009). During startup, the aforementioned error messages "Couldn't get size: 0x800...0e" and "MODSIGN: Couldn't get UEFI db list" also flashed for a half a second, but Ubuntu successfully launched anyway, which confirms that these error messages are unrelated and non-fatal.
[*]The MBP has a 64-bit architecture and supports EFI64, as reported by "32- or 64-bit Kernel Startup Mode Selector.app".
[*]However, according to the app and to [this link]("https://everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-15-santa-rosa-specs.html"), by default it boots Mac OS X in 32-bit mode. Not sure whether this is relevant. I used the Startup Mode Selector app to set it to boot in 64-bit mode instead, but this did not change anything.
[/LIST]

What's next? The [COLOR=#000000]Ubuntu documentation on UEFI install/boot you are mentioning seems to be heavily PC-oriented and installation-oriented, while I'm on a Mac, and for the moment I'm not even trying to install Ubuntu yet. 

Thanks again in advance [/COLOR]

---

### Post by allamistakeo19 on 2018-07-23
[Here]("https://everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-15-santa-rosa-specs.html") are the detailed specs of the MBP.

---

### Post by allamistakeo19 on 2018-09-02
Ping 
Anyone?...

---

### Post by francoisdelabre on 2018-10-08
I have installed Ubuntu 16.04.5 on a Macbook 2,1 late 2006.
It's not the same hardware (my Macbook does not have 64 bit EFI or nvidia), but not that far in date.

I discovered that my Macbook couldn't boot from USB (not even a Mac OSX Install USB key), only from DVD.
With refind installed, it should be able to boot from USB, but I couldn't get it to boot even with refind.
I ended up installing Ubuntu in 32 bits from DVD, which succeeded.

So if you find a DVD burner somewhere, give it a try.
Otherwise, perhaps you should first check that your MacBook Pro is able to boot from a Mac OSX Install USB key.

From your first post, it seems you were able to reach the Grub 2 menu.
nomodeset option should disable the graphics card driver, but it does not seem to be enough for you.
Did you remove the quiet and splash options to see the boot logs ? Where does the boot stop/hang?
Did you try the 'recovery mode' from Grub 2 ?
Have you tried the same thing with Ubuntu 16.04.5 instead of 18.04?

---

### Post by francoisdelabre on 2018-10-08
In addition, I find this thread really excellent, with plenty of nice troubleshoot help and clear explanations.
[https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535)

Here is a excerpt :
> 
Basically, we want to make sure that the Grub menu boots, then verify that the kernel is booting, then that the XServer Session starts and displays. 


**Troubleshooting Flow Chart **
This is to break this down into steps: 
_Step 1. Do you have a Grub Menu? _
- Yes: Go to step 2... 
- No: While booting, Press shift key (don't hold down) multiple times to see if the Grub menu will come up. 
- - If yes on Menu, go to step 2 
- - If no, use a LiveCD to chroot >> Change /etc/default/grub/ (line) GRUB_HIDDEN_TIMEOUT=00. and rerun "update-grub" Or you can do that chroot'ed from a LiveCD... instructions second half of post #3. 
(Note- that will display a warning on boot- saying that timeout cannot be set to '0'... but it will display the menu, then and have no apparent challenges with that) 
- - - If yes on Grub Menu go to Step 2 
- - - If No, go to my fix on "Forcing Grub To Show Menu"... Link in Post #2 
- - - - If yes on menu, go to Step 2 
- - - - If No, reinstall grub and Start Step 1 from Beginning... Because it seems that Grub is not booting. 


_Step 2 "Does the Linux Kernel Boot?" At Grub Menu, go into edit mode and boot into a text console (see instructions below) _
- Yes. Go to Step 3 
- No. Messages will be verbose on what is loading, what are warnings and what are error messages. Shortcut keys will start to work as the kernel modules load. If if stops at an error, you will be able to use the shortcut navigation cuts to review the errors. Depending on the error, if it is a kernel error, you may be able to reinstall or renew the kernel image. If it is a device module, at least you have somewhere to go to reload that device module or driver.,,, Goal is to get a "booting kernel." 


_Step 3. From the Grub Menu, try to boot in Rescue mode/low graphics. _
- If Yes, look for additional drivers and install recommended driver. 
- If No, goto Step 4 to verify that linux kernel will boot. 




So step 1 is OK for you.
For step 2, have you tried to edit the grub entry and boot in text mode (i.e. replace the "quiet splash" options in the linux line with "nosplash --verbose text") ?

---

