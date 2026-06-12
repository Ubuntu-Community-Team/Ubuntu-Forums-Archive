---
title: "latest MBP 9,1 (non-Retina) won't boot 12.04 CD or USB"
date: 2012-06-20
forum: Apple Hardware Users
---

### Post by skierpage on 2012-06-20
I've run Kubuntu dual-boot on a desktop PC for years. I have a new 15-inch MacBook Pro: model 9,1 (not the Retina), and want to run 12.04 on it.  I followed the [LifeHacker guide]("http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required") and installed rEFIt (latest version 0.14 is 2.5 years old..?) and resized to add Windows and Linux root/home/swap partitions.

I haven't installed Windows yet. I went straight to booting a Kubuntu 12.04 .iso, and into a brick wall :(. I've put first the amd64 and then amd64+Mac desktop CD .iso on USB flash drive with usb-creator, I've burned the amd64+Mac to CD, I've booted with one or the other or  both CD and USB inserted, and whether I boot from rEFIt or holding down the option key, or holding down the 'c' key for CD-ROM boot, I always wind up at a dark gray screen showing  "Boot error" or just a flashing cursor. I never see a Linux-like splash screen or grub menu.

There is no page yet for the 9,1 in the [MacTel Wiki Support Matrix]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages") , but I've followed the closest model ([8,2 on Oneiric]("https://help.ubuntu.com/community/MacBookPro8-2/Oneiric")). Note I haven't even got to messing around with MBRs and GPTs; this computer just doesn't seem to like the (K)ubuntu boot media.

There are a zillion things I could try: a different USB flash drive, burn the regular amd64 (no "+Mac") .iso to CD, learn EFI commands, learn rEFIt commands, try an alternate (no graphics?) .iso, try a Fedora 17 .iso (developer did [insane amount of work]("http://mjg59.dreamwidth.org/11285.html") for Mac booting) ... But mainly I'm hoping for "I got a 9,1 model to work", "I've heard of problems with latest MBP hardware/firmware" or "Here's how to diagnose *early* CD/USB boot failures."

This model 9,1 has Apple firmware 1.10,  EFI 1.10, Intel HD Graphics 4000 + NVIDIA GeForce GT 650M to 1,440-by-900 display, 500 GB spinning drive, Core i7.

Thanks and regards (and a big shout-out to "Smurphy" helping folks out on #kubuntu last night).

---

### Post by BoDlulu on 2012-06-20
I wish I had seen your post before.

I *just* purchased a MacBook Pro, and I am trying to install Ubuntu, to no avail :(

What am I gonna do, use MacOS?!

Please follow up if you find a solution.

---

### Post by BoDlulu on 2012-06-20
Well, you know what?  This method worked for me:
[http://tillmail.de/wordpress/436](http://tillmail.de/wordpress/436)

Good luck!

---

### Post by lael on 2012-06-20
My MacBookPro6,1 wouldn't boot either.  I've got that method and also using the amd64+mac iso to boot.

---

### Post by inphektion on 2012-06-21
honestly there are always little issues on these new macs.  Ubuntu can't catch up.  None their fault, propriety stuff needs reverse engineering, etc...
But it seems like a constant fight trying to get ubuntu to run on this hardware and even once it *works* it doesn't work as well as the native mac, using both video cards, efi boot, wifi drivers, etc.

My point is that instead of fighting it I don't see a reason not to leave macosx native, with these latest gen of intels, up to 16GB of ram, etc. I can run ubuntu full screen mode in a vm and not ever know i didn't boot it native.  This is what i'm going to do, this way i don't fight with getting ubuntu working half a$$ over the next year on the latest mac osx hardware.

---

### Post by theMentor on 2012-06-21
Hi guys,

So I have had no issue running Ubuntu 12.04 on my MacBook Pro (Non-Retina) 9,1

Can I ask what you've tried so far?

I simply booted the image of USB after splitting my harddrive down the middle using DiskUtility in OSX.

Once installed in added the macintel repo and bob-your-uncle, wifi, USB and all that...

---

### Post by alexmurray on 2012-06-22
Try booting the livecd / usb with the [kernel boot parameter]("https://wiki.ubuntu.com/Kernel/KernelBootParameters"):

```
nouveau.noaccel=1
```

Or if that doesn't work try:

```
nomodeset
```

as a kernel parameter as well

---

### Post by BoDlulu on 2012-06-22
> **theMentor said:**
> 
So I have had no issue running Ubuntu 12.04 on my MacBook Pro (Non-Retina) 9,1

I simply booted the image of USB after splitting my harddrive down the middle using DiskUtility in OSX.

FYI mine is a **9,2** - not a 9,1.  Maybe that is why it wasn't as easy as with yours.


1/ I had to use the method mentioned above to boot from the usb key (the [http://tillmail.de/wordpress/436](http://tillmail.de/wordpress/436) one)

2/ Once the installation was done, linux would crash during boot.  I had to add the **noapic** kernel argument (found it by googling the error message while starting in safe mode)

3/ Wifi didn't work, I had to manually add the 'b43' (broadcom) drivers

Now it works well but I still have two minor problems:

- The keyboard backlight doesn't work
- Wifi sometimes doesn't work after suspend/resume

---

### Post by philcolbourn on 2012-06-23
> **theMentor said:**
> Hi guys,

So I have had no issue running Ubuntu 12.04 on my MacBook Pro (Non-Retina) 9,1

Can I ask what you've tried so far?

I simply booted the image of USB after splitting my harddrive down the middle using DiskUtility in OSX.

Once installed in added the macintel repo and bob-your-uncle, wifi, USB and all that...

What iso image did you use? There are many to choose from: i386-dvd, alt amd64 ,...

I tried a non dvd one for x64 (i think...) and it did not work.

---

### Post by philcolbourn on 2012-06-26
> **BoDlulu said:**
> FYI mine is a **9,2** - not a 9,1.  Maybe that is why it wasn't as easy as with yours.


1/ I had to use the method mentioned above to boot from the usb key (the [http://tillmail.de/wordpress/436](http://tillmail.de/wordpress/436) one)

2/ Once the installation was done, linux would crash during boot.  I had to add the **noapic** kernel argument (found it by googling the error message while starting in safe mode)

3/ Wifi didn't work, I had to manually add the 'b43' (broadcom) drivers

Now it works well but I still have two minor problems:

- The keyboard backlight doesn't work
- Wifi sometimes doesn't work after suspend/resume

Is your fan working? Did applesmc module load?

---

### Post by gancub on 2012-06-26
Hi guys,

have you been able to install properly linux/ubuntu in the new macbook pro? I am very interested to know if there is any progress and to know if everything works properly, nvdia, wifi, trackpad... I would like to buy a 15" non retina I think it is the 9,1.

I saw that you are using a non-standard grub.Isn't it possible to use a standard grub2-efi?

Thanks a lot

---

### Post by maclion on 2012-06-26
Also unable to boot a CD (Kubuntu 12, Fedora 17, OpenSuse 12 -- all amd64 versions)

Parted Magic (June 2012 version) boots OK

Linux Bible (2011 edition) DVD boots OK

---

### Post by philcolbourn on 2012-07-01
A thought.

If the live CD graphical installer works, what kernel options does it use?

---

### Post by philcolbourn on 2012-07-01
> **philcolbourn said:**
> A thought.

If the live CD graphical installer works, what kernel options does it use?

Ok, I have Linux Mint 13 working. Ubuntu would be better as it seems to have better refind/EFI support.

Mint's 'compatibility mode' works and allows installation.

To boot into Mint, I have to use Apple's boot manager by holding 'option' while powering-on.

See details [here]("http://philatwarrimoo.blogspot.com.au/2012/06/unubtu-1204-on-macbook-pro-91-non.html").

---

### Post by maclion on 2012-07-01
I have not looked into the the kernel options of the Linux Bible DVD. (would be in the grub.cfg or menu.lst file?)
On my MBP 9,1 the Ubuntu 12.04 install CD would not work. I was able to install LinuxMint 13 (maya)

Now working on wi-fi firmware install...


[LIST]
[*]No */boot/grub/menu.lst*. It has been replaced by **/boot/grub/grub.cfg**.
[*]There is no "/find boot/grub/stage1" at the grub prompt. Stage 1.5 has been eliminated.
[*]The main Grub 2 configuration file, normally located in the **/boot/grub** folder, is **grub.cfg**. It is the product of various scripts and should not normally be edited directly.
[*]**grub.cfg** is overwritten by certain Grub 2 package updates, whenever a kernel is added or removed, or when the user runs update-grub.
[*]The menu list of available Linux kernels is automatically generated by running **update-grub**.
[*]The user can create a custom file in which the user can place his own menu entries. This file will *not* be overwritten. By default, a custom file named **40_custom** is available for use in the */etc/grub.d* folder.
[/LIST]

---

### Post by maclion on 2012-07-01
GRUB_DEFAULT=0 
#GRUB_HIDDEN_TIMEOUT=0 
GRUB_HIDDEN_TIMEOUT_QUIET=true 
GRUB_TIMEOUT=10 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nointremap"** GRUB_CMDLINE_LINUX=""

(using the 40_custom command)the above allows me to boot LinuxMint (nointremap)

---

### Post by clipcarl on 2012-07-03
Have you tried the tips / patches I posted for the 10,1 MBP here:

[http://forums.opensuse.org/english/get-technical-help-here/laptop/476258-howto-2012-retina-display-macbook-pro-opensuse-linux.html]("http://forums.opensuse.org/english/get-technical-help-here/laptop/476258-howto-2012-retina-display-macbook-pro-opensuse-linux.html")

Since the 9,1 came out at the same time as the 10,1 and they share much of the same hardware they may be very similar with the exception of course that the 9,1 doesn't have the retina display. I was able to get most things working in openSUSE Linux with notable exceptions being the screen backlight and Intel graphics (NVIDIA works fine).

Carl

---

### Post by glennr on 2012-08-20
I have my 9,1 mostly working (for my purposes), but I can't get the Nvidia graphics to work. Also does anyone have an external monitor working?

What do I need to do to get these things going?

I have tried amd64 kernels 3.2.28 and 3.5.2 and nvidia-current from the precise repos and from the ubuntu-x-swat ppa, but no luck with those. Also I'm using BIOS boot (because I also have Windows installed).

Would the graphics work if I installed a 32 bit version?

---

### Post by crack2mann on 2013-03-23
> **glennr said:**
> I have my 9,1 mostly working (for my purposes), but I can't get the Nvidia graphics to work. Also does anyone have an external monitor working?

What do I need to do to get these things going?

I have tried amd64 kernels 3.2.28 and 3.5.2 and nvidia-current from the precise repos and from the ubuntu-x-swat ppa, but no luck with those. Also I'm using BIOS boot (because I also have Windows installed).

Would the graphics work if I installed a 32 bit version?

How did you get it to install? I'm also on a 9,1 and can't get it right.

---

### Post by Vinodh Moodley on 2013-03-24
I have an early 2011 MacBook Pro 13" and installed Ubuntu 13.04 (last weeks build) Mac specific edition. I booted directly from the disk and installed as per normal. Everything works great. Even the keys for keyboard backlight work.

---

