---
title: "boot into OSX as default, choose Ubuntu with option"
date: 2016-01-16
forum: Apple Hardware Users
---

### Post by BobUgh on 2016-01-16
OK, I installed OSX 10.6 on the disk, then installed Ubuntu 14.04 on a 2010 macbook pro. By default it boots into grub, grub gives me several choices, the default is Ubuntu and that works fairly well. There are two OSX choices, 32 bit or 64 bit, either one gets into a panic. But no big deal. If I hold "option" key down, I can choose OSX (only 10.6 for now, no choice of Ubuntu) and it works great. So if I want Ubuntu I don't press option, if I want OSX I press option on boot up then select the OSX 10.6 partition.

I plan to install OSX 10.8 on yet another partition. I'm fairly sure that will overwrite grub? That may be OK with me, because what I really would like:
Default: boot into OSX 10.8
If I press "option", then give me a choice of OSXs or Ubuntu (or Grub)

Is what I would like possible? Somehow I have to make "option" recognize there is another OS. I can call it WINDOWS if that would help. Is there anything I should do now before installing 10.8?

---

### Post by este.el.paz on 2016-01-16
> **BobUgh said:**
> OK, I installed OSX 10.6 on the disk, then installed Ubuntu 14.04 on a 2010 macbook pro. By default it boots into grub, grub gives me several choices, the default is Ubuntu and that works fairly well. There are two OSX choices, 32 bit or 64 bit, either one gets into a panic. But no big deal. If I hold "option" key down, I can choose OSX (only 10.6 for now, no choice of Ubuntu) and it works great. So if I want Ubuntu I don't press option, if I want OSX I press option on boot up then select the OSX 10.6 partition.

I plan to install OSX 10.8 on yet another partition. I'm fairly sure that will overwrite grub? That may be OK with me, because what I really would like:
Default: boot into OSX 10.8
If I press "option", then give me a choice of OSXs or Ubuntu (or Grub)

Is what I would like possible? Somehow I have to make "option" recognize there is another OS. I can call it WINDOWS if that would help. Is there anything I should do now before installing 10.8?

BobU:

No worries Bob, yes, when you install 10.8 it will overwrite GRUB and it will be the default choice . . . ***probably*** . . . .  On my '09 MBPro I have a triple boot set up, 10.6 is first partition and is default partition . . . second partition I have 10.9 now . . . in that system I installed rEFInd . . . third partition I have Linux Mint 17.2/GRUB.

If I want OSX2 from cold boot, I hold the option key, which gives me OSX bootloader, I pick second disk, rEFInd opens and I could pick any of the options there 10.6, 10.9, or linux . . . .  In the OSX bootloader it shows the linux partition labeled as "Windows" . . . if I pick that one it goes to the GRUB window . . . .

Installing OSX after the linux install may be "difficult" . . . to get back into linux . . . if you can get to GRUB then maybe "recovery" might be able to "reinstall GRUB bootloader" . . . I haven't been so lucky.  If you can't boot linux then try to get SuperGRUB2 recovery boot iso and burn it to CD . . . that should boot linux or any system . . . .  In the past I have had to do a fresh install and provide a small 10 MB partition flagged "bios_grub" to get GRUB to install . . . .  Saw another post here saying that "rEFInd recommends no bootloader" . . . but on my MBPro w/o GRUB, even w/rEFInd, linux won't boot . . . .  Generally best to put linux in last . . . physically and temporally . . . .

On the "run in virtual" . . . probably best idea, then no worries about linux fan control for intel macs . . . .

e...

---

### Post by BobUgh on 2016-01-20
What I am still wondering about is why when I hold "option" down while powering on/booting, the Mac startup manager sees the OSX bootable volumes, - and if I have a bootable usb stick (e.g. live install ubuntu) the Mac startup manager also sees that - but it doesn't give me a choice of Ubuntu/grub even though that is what gets booted if I don't hold option down.

I think it has to do with how I did the Ubuntu install, but I'm not sure, hence why I am asking.

---

### Post by este.el.paz on 2016-01-20
@bobU:

It's hard to make sense remotely . . . main thing in linux world is, if it's working . . . it's working; no need to think about it . . . .  And then, the opposite, sometimes it isn't working . . . then there needs to be some thought expended.

e...

---

### Post by BobUgh on 2016-01-22
Well, it isn't working like I want, and mainly I want to understand it better. (1) I would like it to boot straight into OSX by default, it *usually* doesn't do that. (2) if I go into the Mac Startup Manager (press "option" when booting) I would like to see a choice that will get me Ubuntu, presently only OSX comes up.

I did get brave enough to install Mountain Lion OSX *using* that machine - again, it had been booting into Grub then Ubuntu fine, Grub then OSX panicked, and I could boot into OSX by holding "option". . .   When I installed yet another OSX yesterday, I installed to a partition *on a usb drive*. I thought if I did that, it would leave my internal drive alone. When the machine booted for the Nth time during the install process, it worked fine. I shut it down, removed the usb drive, and rebooted.

I expected it to go into Grub as before, but it booted right into the old OSX, which it had never done before! So even though I didn't do anything to the Mac or the internal drive, somewhere in the install process some bits on the internal drive, or some bits in firmware memory got fiddled with. Half my problem solved?

It left me unable to boot into Ubuntu, now it wasn't going into Grub/Ubuntu by default, and it wasn't a choice from Mac Startup Manager. However, I eventually kind of fixed it: I connected up the usb drive again, from OSX System Preferences -> "Startup Disk", now here is the tricky part: I selected the usb as the default startup disk (even though that wasn't what I wanted) clicked on "Restart…" and as soon as it powered down, I quickly removed the usb drive.

On powering up, the Mac went looking for the usb, it wasn't there. After about 40 seconds, it went into Grub! Now that always happens.

It is probably good enough for now, this is more of a learning experience more than I urgently need a working multi boot Mac. Earlier I thought I had gone into "Startup Disk" and selected OSX as default, but now my memory is fuzzy. If I really wanted to, there's some code that examines a drive and reports on the boot up and partition info. I have used it on a Dell with legacy MBR, haven't tried it on a Mac with GPT.

Maybe I should start a new thread and try to simplify my original question: how do I install Ubuntu on a Mac, (either single or multi) and have it show up when the "Mac Startup Manager" is selected by holding "option/alt" key down while booting? However next week I will be too busy to work on this so this may get put on hold for a while.

---

### Post by este.el.paz on 2016-01-22
@Bob:

Well, maybe over the weekend some other people will post, up to you whether you feel like starting a new thread, might get new eyes on the topic . . . I haven't cracked open my MBPro in LM 17 yet, the other conversation about "can't shut down" and the kernel data is something I wanted to check . . . .  But, as I mentioned earlier in this thread, doing a triple-boot + recovery disk, I have rEFInd installed on second disk, so the default is 10.6 in first disk (no rEFInd) . . . .  But, booting with option key shows 4 disks . . . and I think that rEFInd has something to do with OSX "recognizing" linux, labeled as "windows" . . . and I can select that . . . takes me to GRUB window . . . OR, second disk with 10.9 selected takes me to rEFInd window . . . and I can select any of the options from there.

So, again, once you install or upgrade OSX that sort of "overwrites" GRUB and should make itself the default . . . and then OSX doesn't "recognize" linux as a viable system, so it doesn't show in the OSX option boot manager . . . you would also have to "re-bless" rEFInd to get that "hooked up" . . . but, it isn't necessary, using the option key should still show the linux option . . . .  But, also, doing an OSX install/upgrade after doing a linux install would also possibly mess with GRUB . . . .

So, only thing I think I haven't mentioned is, for my MBPro installs I have to set up a 10 MB partition labeled as "bios_grub" . . . if I don't, it says "successful" but system doesn't boot linux . . . and then, after the install, shut down after the install and cold boot . . . then all the rEFInd and GRUB stuff shows up and works . . . . So, doing an OSX install after that will mess with stuff . . . and so will using "start-up disk" . . . .  And, yes, I haven't had "success" trying to use the ubuntu/debian installer to install to an ext HD partition, even though GParted would show it and cut it up etc, during the install, parts were installed in the int HD and some in the ext HD . . . .  But, have fun . . . "learn stuff" as they say on NCIS NO . . . .

e.....

---

### Post by LostFarmer on 2016-01-22
Just started using a Macbook pro early 2011, what a pain but a challenge.  But have finally installed Mac OS, MS WIn 10 and Mint installed , in efi mode.    Some how when I made a partition with linux or MS Windows the comp firmware changed the hdd to a hybrid partitioning, had to then fix to only a EFI drive.  If your apple works more or less like my model, would add the Apple OS correctly to linux grub menu.  At this point of time , I am editing the grub.cfg file.  You could make Apple as the default OS to boot and make the time out to what ever you like.  

Pressing the 'Option' key at bootup only gives MacOS option. Without pressing the Option key it will boot the first boot OS listed in EFI firmware.  To see  under linux command 'efibootmgr -v'

[http://askubuntu.com/questions/179689/mac-os-x-wont-boot-from-grub-menu-in-ubuntu-precise-on-apple-mba5-2](http://askubuntu.com/questions/179689/mac-os-x-wont-boot-from-grub-menu-in-ubuntu-precise-on-apple-mba5-2)

---

