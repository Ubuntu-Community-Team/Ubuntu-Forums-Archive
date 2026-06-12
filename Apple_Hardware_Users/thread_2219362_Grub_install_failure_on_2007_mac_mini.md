---
title: "Grub install failure on 2007 mac mini"
date: 2014-04-23
forum: Apple Hardware Users
---

### Post by adamgdavis on 2014-04-23
I have installed Ubuntu 14.04 desktop on my 2007 mac mini but the installer throws a fatal error at the end, indicating that grub cannot be installed.

The mac mini has been upgraded with a 60GB SSD and a 1TB HD where the Optical drive used to live. I am running the installer/LiveDVD from a USB DVD drive, booted from rEFInd.

I am trying to set up the mini to dual boot my existing OS X partition (half of the SSD) and Ubuntu (the remaining half of the SSD).

Paste of the boot info script is here: [http://paste.ubuntu.com/7318152/](http://paste.ubuntu.com/7318152/)

Having tried to wrap my head around Hybrid MBR as compared to GPT, I think I want to stick with the latter. If I understand correctly, I should be able to put grub on a GPT partition but it will need to have a bios_grub flag (as per [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)).

Can anyone confirm the GPT/BIOS option is a sane one and offer any suggestions how I may get this working?

---

### Post by este.el.paz on 2014-04-23
> **adamgdavis said:**
> https://help.ubuntu.com/community/Grub2/Installing[/URL]).

Can anyone confirm the GPT/BIOS option is a sane one and offer any suggestions how I may get this working?

Yes . . . you shouldn't have to do a hybrid MBR . . . but, if you have the space you want for Ubuntu set as "free space" you might let the installer run the show and it should set up the GRUB partition . . . automatically.  But, if you set the partitions, then it's only about 10MB and indeed you flag it bios_grub--but I just did the 14.04 install last night and the choice in the drop down menu was not "bios_grub" as it used to be but was something else, but then in the GParted table it showed "bios_grub" in the line for the partition . . . and then you also need the home folder set as EXT4 and flagged as "/" . . . .  But there should be a place for GRUB for to go . . . if you do it "the other way" . . . and if you choose "install next to other system" should be OK and it should set it up automatically . . . .  After install, the advice is to shut down, rather than restart . . . and when you re-boot holding the option key down, the rEFInd splash should work and show your optional system . . . and then it will go to the GRUB window . . . etc.

e.e.p.

---

### Post by adamgdavis on 2014-04-24
Thank you for the reply. I did choose to let the Ubuntu installer partition free space for me with the 'Install Ubuntu Alongside Mac OS X' option and this resulted in the grub install failure I mention.

The installer did create a /boot partition (/dev/sdb3 as per the boot info script paste above). The boot info script shows an unknown boot loader on that partition. I have browsed the /boot partition within a LiveCD session and it clearly has some grub files, a vmlinuz file, etc. I am not clear whether it is a proper grub installation or whether the installer placed many of the requisite files for grub but missed some critical ones.

Should I try to work with what is already in the /boot partition and see if I can get this to function as a boot loader that rEFInd will recognize, or re-allocate all but the Mac partitions and start the installer again?

---

### Post by este.el.paz on 2014-04-24
> **adamgdavis said:**
> Thank you for the reply. I did choose to let the Ubuntu installer partition free space for me with the 'Install Ubuntu Alongside Mac OS X' option and this resulted in the grub install failure I mention.

The installer did create a /boot partition (/dev/sdb3 as per the boot info script paste above). The boot info script shows an unknown boot loader on that partition. I have browsed the /boot partition within a LiveCD session and it clearly has some grub files, a vmlinuz file, etc. I am not clear whether it is a proper grub installation or whether the installer placed many of the requisite files for grub but missed some critical ones.

Should I try to work with what is already in the /boot partition and see if I can get this to function as a boot loader that rEFInd will recognize, or re-allocate all but the Mac partitions and start the installer again?

@adamg:

OK, well, it does seem like sometimes the installer messes up, seemed to happen more in LM than in 'buntu.  But, first question, did you check the md5sum number for your .iso?  If it doesn't match the .iso may be corrupted and you should get another one . . . .  I'm not a technical computer guy, but I did have this GRUB issue in several LM installa and I'm questioning whether the "/dev/sdb3" is correct . . . thinking that it should be "sdaX" . . . X being the partition number . . . but, could be that's OK????  Anyway, if the md5sum number is correct then I'd try to run the install "the other way" and manually set up the partitions in GParted . . . using the 10 or so MB for "bios_grub" and it seems like the installer is using the amount of RAM for the swap, rather than the old advice for 1.5 - 2x the RAM.  Personally in my observation I haven't used much if any of swap, but then I'm just checking emails and posting stuff on forums.

Point being, it's probably less of a brain teaser to start fresh rather than try to figure where it went wrong . . . unless you are stuck in Mobile and have nothing to do . . . .  Other option, which I tried and it's good to have for emergencies, is get a copy of SuperGrub2 burn to CD and see if you can boot the install, possibly since you have a boot partition there it may be able to repair GRUB and get you back in Biz . . . .  Otherwise the installs go relatively fast, it's just easier to nuke and pave . . . .

e.e.p.

---

