---
title: "EFI boot bricks Macbook Pro 5,4"
date: 2011-04-29
forum: Apple Hardware Users
---

### Post by Hatsune Miku on 2011-04-29
Alright this is a general reminder to all mac users. Today i multi-booted Mac OS X 10.6.7 with Ubuntu natty 64bit. I booted using the EFI boot loader built into the Mac and use the EFI boot on the live CD. After installing the system and rebooted it **_bricked the firmware to the point of black screen of death!_** I've already sent it to the apple store where it will be repaired under warranty. This is a reminder that the EFI boot on any Macintosh is still experimental, please be cautious!

It wouldn't even do the POST chime, BIOS/EFI beeps, or blink the LED. It just sat there with a dim LED.

Miku :popcorn:

---

### Post by metatechbe on 2011-04-30
> **Hatsune Miku said:**
> I booted using the EFI boot loader built into the Mac and use the EFI boot on the live CD. After installing the system and rebooted it **_bricked the firmware to the point of black screen of death!_** 

Hi Miku,
Just a naive question : how did you define the partitions during the installation ?  Are you sure the EFI partition was not overwritten ?
metatech

---

### Post by nandaiyo on 2011-04-30
Sorry to hear. Would rEFIt have provided a better solution?

---

### Post by srs5694 on 2011-04-30
There was a thread a week or two ago in which somebody was attempting to install the 11.04 beta on a UEFI-based PC. It transpired that the installer was probably reformatting the EFI System Partition (ESP) as FAT-16, thus wiping out any previous boot loaders installed there. Assuming that bug wasn't fixed in the final release version, and assuming that the Mac's BIOS either requires certain files in the ESP or can't understand FAT-16, it could be that wiping the ESP in this way explains the problem. I'd say this merits further investigation. (My own Intel-based Mac is a 32-bit Mac Mini, and the 32-bit Ubuntu 11.04 installer includes no EFI support, so I can't test this hypothesis in the most direct and obvious way, but I might test the individual components of the hypothesis in other ways, if I find the time. No guarantees on that last caveat, though....)

---

### Post by Hatsune Miku on 2011-05-01
> **metatechbe said:**
> Hi Miku,
Just a naive question : how did you define the partitions during the installation ?  Are you sure the EFI partition was not overwritten ?
metatech

The EFI Partition has nothing to do with it. I've installed Mac OS X - Windows with no EFI partition and it booted fine. The EFI is the firmware for the Mac, its like the BIOS for a PC.

> **nandaiyo said:**
> Sorry to hear. Would rEFIt have provided a better solution?

Yes it would! Install using the PC Method&#8230; will come up as "Windows" on the Mac OS X Boot loader

> **srs5694 said:**
> There was a thread a week or two ago in which somebody was attempting to install the 11.04 beta on a UEFI-based PC. It transpired that the installer was probably reformatting the EFI System Partition (ESP) as FAT-16, thus wiping out any previous boot loaders installed there. Assuming that bug wasn't fixed in the final release version, and assuming that the Mac's BIOS either requires certain files in the ESP or can't understand FAT-16, it could be that wiping the ESP in this way explains the problem. I'd say this merits further investigation. (My own Intel-based Mac is a 32-bit Mac Mini, and the 32-bit Ubuntu 11.04 installer includes no EFI support, so I can't test this hypothesis in the most direct and obvious way, but I might test the individual components of the hypothesis in other ways, if I find the time. No guarantees on that last caveat, though....)

Refer to the post to Metatech; The EFI's on Macintoshes us EFI 1.10 the Standard Intel defined and not the UEFI standard. I also think apple added their own bits of code from OpenFirmware as well. What im guessing is the Kernel made a call to ACPI to halt the CPU, to get to ACPI it needs to go through the EFI. So in theory im thinking it made a odd call and just over wrote something in the EFI system (You can access the firmware's FS through rEFIt), because it wouldn't even run POST. So it will be need to be looked at by someone in the development team.

And sorry it took so long to respond&#8230; so many pointless project to do :p!

---

### Post by srs5694 on 2011-05-01
I've seen cases where unexpected hard disk contents cause a BIOS-based computer to fail to boot past its BIOS disk-detection code. Thus, it wouldn't surprise me if Apple's EFI implementation might do something similar if it was missing something critical on the EFI System Partition, or if that partition use a variant filesystem that it didn't like, even if the computer boots fine from a CD-ROM when the disk is completely blank. That is, of course, sheer speculation on my part, but given the known issue in the beta of how the Ubuntu installer treats the EFI System Partition, it's at least plausible.

---

### Post by Hatsune Miku on 2011-05-01
> **srs5694 said:**
> I've seen cases where unexpected hard disk contents cause a BIOS-based computer to fail to boot past its BIOS disk-detection code. Thus, it wouldn't surprise me if Apple's EFI implementation might do something similar if it was missing something critical on the EFI System Partition, or if that partition use a variant filesystem that it didn't like, even if the computer boots fine from a CD-ROM when the disk is completely blank. That is, of course, sheer speculation on my part, but given the known issue in the beta of how the Ubuntu installer treats the EFI System Partition, it's at least plausible.

Well i had a EFI boot partition at the time though. And yet it still bricked.... bricked really hard, and i just my mac back today and they had to replace the "Logic" board (Why they dnt call it a Mother board ill never understand -_-)

---

### Post by srs5694 on 2011-05-01
My suggestion wasn't that the installer *deleted* the EFI System Partition, but that it *damaged* it.

That said, if the shop said it had to replace the motherboard, that tends to suggest that my hypothesis was incorrect. (OTOH, they may have been incompetent or just billed you for unnecessary work....)

---

### Post by Hatsune Miku on 2011-05-02
> **srs5694 said:**
> My suggestion wasn't that the installer *deleted* the EFI System Partition, but that it *damaged* it.

That said, if the shop said it had to replace the motherboard, that tends to suggest that my hypothesis was incorrect. (OTOH, they may have been incompetent or just billed you for unnecessary work....)

I have apple care so it was free. Once the logic board was replaced it booted just fine, on the same hdd/partition map that the last install was (The one what bricked my computer). So that just gives more evidence it was the boot code/efi (Please dnt think im being a douche, i'm just trying to figure out if it was the boot code/efi or not :))

---

### Post by srs5694 on 2011-05-02
You're probably right. If so, that's very disturbing, since it means that something in the GRUB code or Linux kernel did something to damage the firmware or even the hardware. I'd file a bug report; although you probably don't want to check to see if it's repeatable, it's so serious that the developers should know about it.

The one possibility for my initial hypothesis is that the techs misdiagnosed the problem, replaced the motherboard, and as a routine measure, re-wrote the EFI System Partition (ESP). In this scenario, the motherboard replacement accomplished nothing, but the routine clean-up of the ESP did the job. Note that this would mean that the ESP would look the same to you after you got the machine back as it did before the problem occurred, so the only chance of discovering the misdiagnosis would be if they sent the board somewhere for further testing and that testing turned up no problems. Even if this were to happen, you probably wouldn't hear anything about it.

---

### Post by Hatsune Miku on 2011-05-03
> **srs5694 said:**
> You're probably right. If so, that's very disturbing, since it means that something in the GRUB code or Linux kernel did something to damage the firmware or even the hardware. I'd file a bug report; although you probably don't want to check to see if it's repeatable, it's so serious that the developers should know about it.

The one possibility for my initial hypothesis is that the techs misdiagnosed the problem, replaced the motherboard, and as a routine measure, re-wrote the EFI System Partition (ESP). In this scenario, the motherboard replacement accomplished nothing, but the routine clean-up of the ESP did the job. Note that this would mean that the ESP would look the same to you after you got the machine back as it did before the problem occurred, so the only chance of discovering the misdiagnosis would be if they sent the board somewhere for further testing and that testing turned up no problems. Even if this were to happen, you probably wouldn't hear anything about it.

Macintosh EFI firmware doesn't use the ESP partition at all. It looks for HFS+ partitions and looks for a BOOTX.EFI, Which would need to mean it had to have been the firmware. Also on the sheet they gave me on what they did to fix it, it was a mother board replacement. Nothing else was done to is.

---

### Post by Jujstme on 2011-05-03
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089](https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089)

As you can see, you are not the only one who had problems with EFI.

---

### Post by srs5694 on 2011-05-03
> **Jujstme said:**
> [https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089](https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089)

As you can see, you are not the only one who had problems with EFI.

I ran across that link, too, and was going to post it -- you beat me to it! ;)

That link describes a problem with a MacBook Pro 5,5 rather than the 5,4 model that Hatsune Miku uses. It could well be the same issue, though. If so, following [this procedure](http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/) to reflash the firmware would have fixed the problem; replacing the motherboard was overkill. (Of course, since you didn't pay for it, you probably don't care, Hatsune; I'm posting this link in case somebody else has this problem in the future. Note that I've not had this problem myself or used that procedure, though.)

---

### Post by Hatsune Miku on 2011-05-04
> **srs5694 said:**
> I ran across that link, too, and was going to post it -- you beat me to it! ;)

That link describes a problem with a MacBook Pro 5,5 rather than the 5,4 model that Hatsune Miku uses. It could well be the same issue, though. If so, following [this procedure](http://pubmem.wordpress.com/2011/04/09/flash-efi-firmware-update-manually-on-a-macbook-51/) to reflash the firmware would have fixed the problem; replacing the motherboard was overkill. (Of course, since you didn't pay for it, you probably don't care, Hatsune; I'm posting this link in case somebody else has this problem in the future. Note that I've not had this problem myself or used that procedure, though.)

Tbh im so glad they gave me a new motherboard :D! increases my computers life another 2 years :D!

---

### Post by Hatsune Miku on 2011-05-05
If a Mod Could please Sticky this!!

---

### Post by shew82 on 2011-05-06
I've now ended up completely restoring my MBP 5,5 (in efforts to get it up and running again before I was able to find the re-install firmware advice)... 

My question to anyone who may know is this: If I try re-installing Natty (and it again bricks my EFI), will simply re-re-installing the firmware file bring everything to life, leaving my Mac data intact? Alternatively, is there a way to install Natty without bricking the EFI in the first place?

---

### Post by Hatsune Miku on 2011-05-07
> **shew82 said:**
> I've now ended up completely restoring my MBP 5,5 (in efforts to get it up and running again before I was able to find the re-install firmware advice)... 

My question to anyone who may know is this: If I try re-installing Natty (and it again bricks my EFI), will simply re-re-installing the firmware file bring everything to life, leaving my Mac data intact? Alternatively, is there a way to install Natty without bricking the EFI in the first place?

Did you install using the EFI option or the "Windows" option?

---

### Post by lateralchaos on 2011-05-11
I have also had this exact same problem with this model. I already had Ubuntu working on the Mac, but because of some problems with OS X and Windoze (lame, I know), I decided to do a complete rebuild. When doing so, I failed to specify the grub installation partition... 

I ended up with a bricked Mac, but I was able to actually get it to boot:

With the Mac fully powered down, hold down the power button, until the power indicator light blinks. From here it is a little tricky, since I haven't quite figured out exactly what gets it to boot. When the power indicator starts blinking, immediately release the power button. Sometimes just this did the trick. If this does not work, when light starts blinking (after going through process again), immediately release and press the power button again, before the blinking stops. Also, sometimes it would work when I do that and then press the power button again right after the indicator became solid again. 

Since I was able to boot into OSX, I wiped the bootcamp partition, restoring to default. I did not have the OSX disc so a reinstall was not an option. I dug around and could not find any firmware restoration utilities whatsoever. I could find firmware restores and upgrades for other close models, but not this one. I was able to take it to the Apple store Saturday and they had a new logic board in it the next day.

I am very satisfied with Apple that Ubuntu did not void the warranty, and the quick turnaround, but why not have firmware restoration for every Mac?

I hope this helps others in at least getting it to boot, and if only Apple provided the firmware restoration utility they/we wouldn't have to pay 500$ a pop for new logic boards...

I hope that this EFI "feature" (or at least the default setting) is savagely murdered and removed from Ubuntu forever.

---

### Post by lateralchaos on 2011-05-11
> **shew82 said:**
> I've now ended up completely restoring my MBP 5,5 (in efforts to get it up and running again before I was able to find the re-install firmware advice)... 

My question to anyone who may know is this: If I try re-installing Natty (and it again bricks my EFI), will simply re-re-installing the firmware file bring everything to life, leaving my Mac data intact? Alternatively, is there a way to install Natty without bricking the EFI in the first place?


To install Natty without bricking EFI,do everything as guides say, but BEFORE clicking Install , change the grub bootloader install from the hard drive, to the Ubuntu partition itself. You will need to have pre-formatted the ext4 (or whatever) partition for it to allow grub to install on it. This way rEFIt can see the bootloader on the partition and EFI is not hosed. 

If somehow you screw up, since you have the firmware restoration (unfortunately for me 5,4 doesn't have one), you should be able to restore it. If it is bricked, you will need to hold the power button down as described in my above post.

---

### Post by Hatsune Miku on 2011-05-12
> **lateralchaos said:**
> To install Natty without bricking EFI,do everything as guides say, but BEFORE clicking Install , change the grub bootloader install from the hard drive, to the Ubuntu partition itself. You will need to have pre-formatted the ext4 (or whatever) partition for it to allow grub to install on it. This way rEFIt can see the bootloader on the partition and EFI is not hosed. 

If somehow you screw up, since you have the firmware restoration (unfortunately for me 5,4 doesn't have one), you should be able to restore it. If it is bricked, you will need to hold the power button down as described in my above post.

Thats odd.... it told the installer to install GRUB on the ubuntu partition.... I do not think this was the original problem.

---

### Post by lambengolmor on 2011-05-17
I was just going to install... Lucky me I've seen this post... Is there some place where is described a safe&tested install procedure? Or, does the good old rEFIt install still works fine?
Thanks very much for the advice!

BTW, I guess it should affect all EFI macbooks, not just MBP5,4 right?

---

### Post by Hatsune Miku on 2011-06-01
> **lambengolmor said:**
> I was just going to install... Lucky me I've seen this post... Is there some place where is described a safe&tested install procedure? Or, does the good old rEFIt install still works fine?
Thanks very much for the advice!

BTW, I guess it should affect all EFI macbooks, not just MBP5,4 right?

  It seems to mostly be effecting the 5,X models.

---

### Post by metatechbe on 2011-06-02
> **Hatsune Miku said:**
> It seems to mostly be effecting the 5,X models.

Yes, most probably MacBook(Pro) 6,x, 7,x and 8,x do not suffer from the problem because the vanilla kernel freezes during boot in EFI mode on those machines, so the installation process does not go so far as to call the efibootmgr command which corrupts the firmware.

Regards,

metatech

---

### Post by lambengolmor on 2011-06-03
What about older models? Are they expected to behave like the 5 series or like the newer?
Thanks a lot for the info anyway :)

---

### Post by Miles Away on 2011-06-25
Yesterday I was lucky to install Natty on MacBook 4,1 (MB402A) in single-OS setup without any problems. I've used 11.04-amd64-alternate image. During install I've chosen guided partition setup, wiped HFS partition, but left EFI 200Mb partition. I was surprised when system booted quickly after install, as I was expecting a 30-seconds timeout, so it seems to me that EFI Boot worked well :)
So, I believe at least one of older models doesn't have such problem, but, obviously, this should be confirmed.

---

### Post by andreigherghe on 2011-07-04
Hello,
I have the EXACT same problem on a MacBook Air 2,1
It boots, the screen is black, the sleep indicator flashes rapidly, and then a loooud beep.
I hardly booted into OS X, and i can type from it now. I mounted the EFI partition using "sudo mount -t msdos /dev/disk0s1 /Volumes" And in /EFI, there are two folders. At first was only 1 folder (APPLE), but now there are APPLE and ubuntu...
I'm desperate, what should i do? On the installer, at boot loader, i selected the partition itself, not the HDD.
Thanks, hoping for an answer...

EDIT: I want to reflash. As i said, i have a MacBook Air 2,1 ; and i found the following firmware: MBA21_0075_03B_LOCKED.scap However, my firmware is MBA21.0075.B05 (Newer...) Should i flash it?
Thanks #2!

EDIT #2: YEEES! It works! I flashed a new firmware and it works!!

EDIT #3: Also, i can still use ubuntu :D

---

### Post by zaebo on 2011-07-18
> **Hatsune Miku said:**
> It seems to mostly be effecting the 5,X models.


Hello,

I've got an iMac10,1, and have the same problem.
I tried several solutions, but nothing worked for me.

The method to flash the EFI firmware sounds very promising, but
unfortunately my iMac Version is the only one without an 
EFI firmware update.

There seems to be a Firmware.scap located on the MacOS Installer DVD
and in a folder on the mac. This seems to be the only way to
flash a different firmware.
So, this could be although a way to brick my iMac for good.

Does anyone of you have an idea if this could work out? 
Using the Firmware.scap from either the DVD of from the folder
/usr/standalone/i386?

I'm also discussing this on a mac forum, but none of us has
a clue. I thought that I could maybe here have luck..

---

