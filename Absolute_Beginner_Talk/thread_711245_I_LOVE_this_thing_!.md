---
title: "I LOVE this thing !"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Rebelli0us on 2008-02-29
I love the "Live CD", Ubuntu 7.1 booted right up and was ready to use. It comes with everything you need to start working right away. There's nothing to installl, or is there?

I deleted Vista because it sucks and I reinstalled my old Windows 2000, which I will continue to use until I can transition to Linux. My decision is final, I've had it with Microsoftt and there is no going back.

I don't want something-for-nothing, I'm willing to pay a reasonable price for Linux software. But I will no longer allow an operating system to take over my computer and use my internet connection to install proprietary software without my knowledge or consent.

Ubuntu cheerfully installed on a bootable 4GB USB flash drive, and the memory stick will even attempt to boot in ANY computer you insert it! Wow, an operating system and all my work on a flash drive! And no 64-digit license # to type. Completely portable because there's no OS "license" tied to my hardware. I wish Ubuntu had a "clone" command to copy itself to flash drives so I could give one to all my friends for Xmas. Let's flood the world with free sticks, LinuX on stiX r0X.

Now the hard part. My DSL network/modem with NVIDIA drivers is automatically installed in Windows and is always on, but I couldn't install it in Ubuntu. I spent hours trying -- nothing. Then I tried installing the dialup modem, no luck. I downloaded several "packages" but none would install. Dell seems to be the only one offering Conexant drivers. 

I understand that Ubuntu doesn't have billions to spend on developing software, but we need more choices, so I'm going to stick with this. **Thank you Mr. Ubuntu.** I wrote Widows software for years, and I did well enough to retire at age 42. I want to give something back, so I'm willing to help -- just for the fun of it. I'm very qualified and it won't cost you anything.

---

### Post by jan quark on 2008-02-29
hi and welcome Rebelli0us

ubuntu needs such enthusiasts as you are
there are many ways you can contribute to make ubuntu better
just use your skills, tell us more and we direct you in the right direction


to install nvidia drivers you can either use the restircted driver manager (altough the drivers seemed to be old) or the application envy

to make your dls modem run read through this guide

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)

---

### Post by Duck2006 on 2008-02-29
Some reading for install and other stuff.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Rebelli0us on 2008-02-29
> **jan quark said:**
> hi and welcome Rebelli0us

ubuntu needs such enthusiasts as you are
there are many ways you can contribute to make ubuntu better
just use your skills, tell us more and we direct you in the right direction


to install nvidia drivers you can either use the restircted driver manager (altough the drivers seemed to be old) or the application envy

to make your dls modem run read through this guide

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)


Thanks jan quark, I tried the online help and the PPPoE link.  It wouldn't detect the hardware, it's a Netopia 2241N DSL gateway. I'll give it another try soon.

---

### Post by Rebelli0us on 2008-02-29
> **Duck2006 said:**
> Some reading for install and other stuff.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)


Thanks Duck2006, that link is for dual booting, I didn't do that. I just ran Ubuntu 7.10 from CD and installed to USB flash drive, took ~20 minutes. If you want the card to be bootable, select that option during installation. The only problem I found is Ubuntu and Grub use different disk naming convention -- hda, dev\ etc. that's confusing. So when you specify the boot disk in the final install dialog it's easy to do damage. If you don't want Ubuntu to mess with your Windows disk bootsector, you can temporarily disable your HD controller in BIOS, effectively hiding your HD during the install, then Ubuntu will by default make the flash drive bootable.

To boot Ubuntu, insert card in USB slot and in BIOS bootup select to boot from USB device. HP computers call it the "boot menu" (Esc). That way you don't even need to create a dual boot setup. The card will actually attempt to boot on both my machines . . . I'm using an A-data 4GB Class 6 SDHC and it boots and runs just fine.

---

### Post by forrestcupp on 2008-02-29
If you don't actually install Ubuntu to your hard drive, I don't think you're getting the full effect.  You have to have it installed to actually install any of the thousands of great apps that are available that aren't part of the default install.  I also don't know how video and networking drivers would work without having an actual installation.  I wonder if they would need to be reinstalled every time you boot.  

If you really like it, maybe you should venture out and try a dual boot setup to enjoy all of it's benefits.  Then when you are ready, you can always just get rid of Windows if you don't need it any more.

---

### Post by housam on 2008-02-29
> **Rebelli0us said:**
> 
I understand that Ubuntu doesn't have billions to spend on developing software, but we need more choices, so I'm going to stick with this. **Thank you Mr. Ubuntu.** I wrote Widows software for years, and I did well enough to retire at age 42. I want to give something back, so I'm willing to help -- just for the fun of it. I'm very qualified and it won't cost you anything.

You can go from here [[COLOR="Red"]_https://wiki.ubuntu.com/UbuntuDevelopment_[/COLOR]]("https://wiki.ubuntu.com/UbuntuDevelopment")
Or here [[COLOR="Red"]https://help.launchpad.net/BetaTesting[/COLOR]]("https://help.launchpad.net/BetaTesting")

---

