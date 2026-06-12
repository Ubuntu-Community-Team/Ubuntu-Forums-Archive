---
title: "Can't boot into desktop"
date: 2014-03-19
forum: Any Other OS
---

### Post by Shadius on 2014-03-19
Hey everybody,

I'm unable to boot into Linux Mint after some updates. I'm a noob with Linux Mint so please help!

---

### Post by Bashing-om on 2014-03-19
Shadius; H i!

Just as a guess, a proprietary graphics driver broke in the updates ?
Try and see if you can boot up with the "system" graphics driver using the "nomodeset" boot parameter.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by Shadius on 2014-03-19
Okay, I'm trying to boot from my Ubuntu Live USB but it's just staying on the Ubuntu loading screen.

---

### Post by Bashing-om on 2014-03-19
Shadius; Welp,

Could be a lot of things.
Check the easier things 1st.
Are you certain boot options in bios are correct to boot the liveUSB ?
Is the liveUSB known good ? , Can you boot that liveUSB in a different machine ?

In your install what results when you attempt to boot up in "recovery mode" from the grub boot menu ?

We got to boot something linux from some where to even have a means to find out where/what the problem is.

[INDENT]even after all these years, it still comes
[INDENT][INDENT][INDENT]back to a Command Line Interface[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Shadius on 2014-03-19
> **Bashing-om said:**
> Shadius; Welp,

Could be a lot of things.
Check the easier things 1st.
Are you certain boot options in bios are correct to boot the liveUSB ?
Is the liveUSB known good ? , Can you boot that liveUSB in a different machine ?

In your install what results when you attempt to boot up in "recovery mode" from the grub boot menu ?

We got to boot something linux from some where to even have a means to find out where/what the problem is.

[INDENT]even after all these years, it still comes
[INDENT][INDENT][INDENT]back to a Command Line Interface[/INDENT][/INDENT][/INDENT][/INDENT]

Okay, the BIOS is set to boot from USB. LiveUSB works, tested it on my Windows computer. Recovery Mode doesn't even show up. I get a bunch of code on the screen. I was going to do a clean reinstall because I have nothing of importance on the machine. I'm thinking of using DBAN to wipe the drive and then trying to do a clean install.

---

### Post by slooksterpsv on 2014-03-19
What graphics do you have in the computer? Do you know its specifics like AMD Radeon HD 7520G or what not?

---

### Post by Bashing-om on 2014-03-19
Shadius; Hey,

Not able to boot the live USB is not a good indication.

Consider, if you can not boot the liveUSB, then there is also no means to (RE-)install !

If you can not boot the known good liveUSB and bios is set up correctly to boot that USB, that leaves only 2 possibilities; and you still can not boot.
1. Hardware problems
2. bios is messed up. Might be worth considering resetting bios to defaults (??).

As a maybe, on this particular machine, are you dual booting with Windows ?

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by Shadius on 2014-03-19
No, I'm not dual booting. I managed to get to some screen (don't recall the name of it) by holding down Shift. I set it to "nomodeset" and "acpi=off". I'm checking the disc for errors and it says "errors found in 1 files! pool/main/u/ubuiquity-slideshow-ubuntu-oem-config-slideshow-ubuntu_58.2_all.deb:"

I have no idea what this means!

---

### Post by Shadius on 2014-03-19
> **slooksterpsv said:**
> What graphics do you have in the computer? Do you know its specifics like AMD Radeon HD 7520G or what not?

I do not know what kind of graphics the laptop has. Is there a way I can find out using the LiveUSB?

---

### Post by slooksterpsv on 2014-03-19
Run the following:
lspci | grep VGA

```

shawn@shawn-Satellite-C75D-A:~$ lspci  | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8400]

```

---

### Post by Shadius on 2014-03-19
> **slooksterpsv said:**
> Run the following:
lspci | grep VGA

```

shawn@shawn-Satellite-C75D-A:~$ lspci  | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8400]

```

How do I run this when I'm stuck at the loading screen? How can I get to a Terminal to run it?

---

### Post by slooksterpsv on 2014-03-19
Press CTRL+ALT+F2 - it should take you to a terminal like interface. If you know the make/model of the computer that would help too.

---

### Post by Shadius on 2014-03-20
> **slooksterpsv said:**
> Press CTRL+ALT+F2 - it should take you to a terminal like interface. If you know the make/model of the computer that would help too.

The make and model is Hp Compaq nc4200

---

### Post by Shadius on 2014-03-20
So I pressed **Ctrl Alt F2** and this is what I get...

[ATTACH=CONFIG]251305[/ATTACH]

---

### Post by slooksterpsv on 2014-03-20
PERFECT! It looks like we can determine the issue with this.

How did you make the bootable medium? CD or USB?
What program(s) did you use to create it? If CD did you use infrarecorder, or if it's usb did you use unetbootin? (Those kinds of apps)
After you downloaded the ISO did you do an md5 checksum on it to make sure it matched? Do you know how to do this?
Does this always happen or did it just start?

I'd recommend trying to do a test on your memory, I'm wondering if RAM could be an issue.

---

### Post by Shadius on 2014-03-20
> **slooksterpsv said:**
> PERFECT! It looks like we can determine the issue with this.

How did you make the bootable medium? CD or USB?
What program(s) did you use to create it? If CD did you use infrarecorder, or if it's usb did you use unetbootin? (Those kinds of apps)
After you downloaded the ISO did you do an md5 checksum on it to make sure it matched? Do you know how to do this?
Does this always happen or did it just start?

I'd recommend trying to do a test on your memory, I'm wondering if RAM could be an issue.

I'm using a USB. The system doesn't have a CD-ROM drive. I used the Startup Disk Creator on my main Ubuntu computer to create the LiveUSB. I just did an MD5 checksum and everything checks out. This is just happening now.

---

### Post by slooksterpsv on 2014-03-20
[https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors)

We need to go through those steps. I'd try to make the bootable usb with unetbootin. I haven't tried the one in Ubuntu.

---

### Post by Bashing-om on 2014-03-20
Shadius; slooksterpsv; Morning !

Agreed we must have a known good liveUSB. To that end we must be able to boot to the boot options screen and run "check disk for defects".

Boot the liveUSB, at the purple splash screen depress the right shift key -> language screen, escape key to accept the default ->
Boot option screen, select "check disk for defects" option, let it run and advise us of the results.

Now this, if it continues with a known good liveUSB we can also attend to
> 
"errors found in 1 files! pool/main/u/ubuiquity-slideshow-ubuntu-oem-config-slideshow-ubuntu_58.2_all.deb:"


Off the top of my head I do not recall how to remove it (slideshow) .. if it continues to be a problem will do the research and find out the procedure to remove it !

With a liveMedium, we can look at everything
[INDENT][INDENT][INDENT]and -> fix most things
[/INDENT][/INDENT][/INDENT]

---

### Post by Shadius on 2014-03-21
Slooksterpsv & Bashing-om,

I verified that the USB is good by running it on other machines. Looking at the Squashfs Errors page that Slooksterpsv provided, I ran a memtest86+ and it resulted with a few thousands errors. So with that, I'm guessing the SODIMM needs to be replaced. I will try to replace the SODIMM on Monday and try again. Thanks again for all your help, really appreciate it. I will update when I can.

---

