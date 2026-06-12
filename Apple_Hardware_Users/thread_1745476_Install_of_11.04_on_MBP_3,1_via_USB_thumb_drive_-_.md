---
title: "Install of 11.04 on MBP 3,1 via USB thumb drive - drive not recognized during boot"
date: 2011-05-01
forum: Apple Hardware Users
---

### Post by arifba on 2011-05-01
Hi all,

Macbook Pro 3,1 (late 2007, core2duo). Trying to install 11.04 (dual boot with OS X).

My CD drive is busted, can't use it to install from. So I'm trying to use a USB thumb drive. Followed the instructions here exactly:
[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

However, rEFIt can not see my USB thumb drive during boot, therefore can't install. Tried using the dd utility to copy the Ubuntu ISO to a spare partition on my internal hard drive. Now, rEFIt sees that drive but attempting to boot into it gives me a 'Missing Operating System' message. So I'm back at trying to get the system to boot from the pendrive.

Anyone have an idea of what I should do?

Thanks.

---

### Post by Peter09 on 2011-05-01
Not sure how you do it on a MAC but you need to make sure that the USB drive is higher up the order of boot devices than your Hard Drive. This is normally done by using a function key to get into the Bios during the boot phase.

It can be F4, F12 or esc for for example.

---

### Post by arifba on 2011-05-01
> **Peter09 said:**
> Not sure how you do it on a MAC but you need to make sure that the USB drive is higher up the order of boot devices than your Hard Drive. This is normally done by using a function key to get into the Bios during the boot phase.

It can be F4, F12 or esc for for example.

Thanks for the reply Peter09 however I don't think that's it. Mac's check all connected drives to see if they are bootable and if one hits the correct key during boot (alt/option), a menu comes up asking you which drive you want to boot from. However, when I do this with the Ubuntu ISO on my pen drive, the pen drive does not come up as one of the options.

---

### Post by Peter09 on 2011-05-01
How are you building your thumb drive, you cannot just copy the iso to it, just like you cannot copy the iso to a partition to get a bootable image. You need an application to convert the iso to a bootable image on the thumb drive.

I do not know what that would be for a MAC.

---

### Post by Peter09 on 2011-05-01
Read

[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

---

### Post by arifba on 2011-05-01
> **Peter09 said:**
> Read

[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

Again, thanks, but as I referenced in the original post, that link is exactly how I went about it. I even tried the alternate method that the page talks about for Macbook Air folks, and that partition was seen by the boot loader but when selecting that partition I got the ''Missing Operating System' message.

---

### Post by Hatsune Miku on 2011-05-01
> **arifba said:**
> Again, thanks, but as I referenced in the original post, that link is exactly how I went about it. I even tried the alternate method that the page talks about for Macbook Air folks, and that partition was seen by the boot loader but when selecting that partition I got the ''Missing Operating System' message.

**_EVERYONE STOP, I GOT THIS! xD!_**

Make a bootable with [unetbootin.]("http://unetbootin.sourceforge.net/") Then install rEFIt on the machine you want to boot ubuntu from. Next make the bootable Flash drive with the unetbootin utility. Once done reboot (With the Flash drive in the computer while its rebooting!). Once rEFIt is booting select tux (yay Tux :3!) Then boot into the installer.

---

### Post by arifba on 2011-05-01
> **Hatsune Miku said:**
> **_EVERYONE STOP, I GOT THIS! xD!_**

Make a bootable with [unetbootin.]("http://unetbootin.sourceforge.net/") Then install rEFIt on the machine you want to boot ubuntu from. Next make the bootable Flash drive with the unetbootin utility. Once done reboot (With the Flash drive in the computer while its rebooting!). Once rEFIt is booting select tux (yay Tux :3!) Then boot into the installer.

Thanks for the reply Hatsune - I did not try to use unetbootin b/c its docs say 'that the resulting USB drives are bootable only on PCs (not on Macs)'.

Am I missing something here? Heading off to bed but will check the thread and reply if need be as soon as I get up.

Thanks.

---

### Post by Hatsune Miku on 2011-05-01
> **arifba said:**
> Thanks for the reply Hatsune - I did not try to use unetbootin b/c its docs say 'that the resulting USB drives are bootable only on PCs (not on Macs)'.

Am I missing something here? Heading off to bed but will check the thread and reply if need be as soon as I get up.

Thanks.

More or less because the Mac OS X bootloader will not see it. But rEFIt will :D!

---

### Post by robvas on 2011-05-01
> **Hatsune Miku said:**
> More or less because the Mac OS X bootloader will not see it. But rEFIt will :D!

Correct, I just wasted half my morning on this. It's not an 'official OS' so it won't see it!

---

### Post by Hatsune Miku on 2011-05-01
> **robvas said:**
> Correct, I just wasted half my morning on this. It's not an 'official OS' so it won't see it!

So it did work yes? :p

---

### Post by arifba on 2011-05-02
> **Hatsune Miku said:**
> So it did work yes? :p

Unfortunately, no, not yet for me. Your advice has moved me forward in that now when I boot rEFIt does see my usb stick with the ubuntu image on it. It actually shows 2 different bootable options for the stick, one with tux and one labelled Boot EFI\boot\bootx64.efi (attached a screenshot of this option as it's a bit of a weird one). 

Selecting tux sends me to the rEFIt Booting Legacy OS screen where I get a bunch of errors (such as 'Error: Not Found returned from legacy loader') and it says the firmware refused to boot from the selected volume. I have attached a screenshot of these errors

Selecting the EFI\boot\bootx64.efi option seems more promising as it sends me to a menu asking me 3 options one them being 'Install Ubuntu'. Selecting that sends me to a black screen which doesn't change and the fans spin up on my laptop and stay that way (I left it for at least 10 mins). Have to power down and reboot to get anywhere from there.

Thanks for the help but still stuck unfortunately.

---

### Post by Hatsune Miku on 2011-05-02
> **arifba said:**
> Unfortunately, no, not yet for me. Your advice has moved me forward in that now when I boot rEFIt does see my usb stick with the ubuntu image on it. It actually shows 2 different bootable options for the stick, one with tux and one labelled Boot EFI\boot\bootx64.efi (attached a screenshot of this option as it's a bit of a weird one). 

Selecting tux sends me to the rEFIt Booting Legacy OS screen where I get a bunch of errors (such as 'Error: Not Found returned from legacy loader') and it says the firmware refused to boot from the selected volume. I have attached a screenshot of these errors

Selecting the EFI\boot\bootx64.efi option seems more promising as it sends me to a menu asking me 3 options one them being 'Install Ubuntu'. Selecting that sends me to a black screen which doesn't change and the fans spin up on my laptop and stay that way (I left it for at least 10 mins). Have to power down and reboot to get anywhere from there.

Thanks for the help but still stuck unfortunately.

Well from my experiences i got it to work, but after that one time it just wouldn't... I hate how the BIOS emulator is so anal D:

---

### Post by arifba on 2011-05-17
> **Hatsune Miku said:**
> Well from my experiences i got it to work, but after that one time it just wouldn't... I hate how the BIOS emulator is so anal D:

Well, thanks for your help Hatsune. If anyone else has any other suggestions I'd love to hear them.

Unbelievable that I can not run Ubuntu on this MBP (other than a VM I guess).

---

