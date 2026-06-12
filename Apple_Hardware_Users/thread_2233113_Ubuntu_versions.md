---
title: "Ubuntu versions"
date: 2014-07-06
forum: Apple Hardware Users
---

### Post by carlito3 on 2014-07-06
Hi, 

I'm triple booting my Macbook pro 8,1 version 10.7.5 with windows 7 and Ubuntu.
i was just wondering whether i can install whatever version of ubuntu or i need the version of ubuntu that goes with my MBR model?

according to this [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) ?
[COLOR=#333333][FONT=Lucida Grande]
[/FONT][/COLOR]

---

### Post by carlito3 on 2014-07-06
Guys, can i install the last version 14.04 on my Macbook pro 8,1 or do i need the 11.04 version?

thanks for your advice

---

### Post by ian-weisser on 2014-07-06
Well, 11.04 is long past end-of-life, so I wouldn't recommend that.
14.04 is certainly the version I would recommend to try.

---

### Post by carlito3 on 2014-07-06
ok that's what i thought, i was just given the error "initramfs error could not find the file system" when trying to install 11.04 version
my iso file was probably corrupted or broken then..

---

### Post by shadesofoctober on 2014-07-10
Edit: I didn't actually specify, but yes, always use latest version (14.04 in this case) with Apple hardware if you can. Support has been getting much better in the last year or two.

Hi, sorry this is a few days old, but I have the exact same Macbook Pro and recent versions of Ubuntu are *much* more easy to work with in regards to compatibility than it used to be.

I highly recommend using Refind as your EFI bootloader for all 3 operating systems.

I installed Refind under OS X, then created 2 partitions for Ubuntu with the disk utility. 
Then I installed Ubuntu from USB.
You can select it for boot by holding ALT during bootup. Make sure to select EFI loader if it's a choice (I can't remember exactly what it shows up as, or if Refind detects the USB, which I think it does)
And yes this should work fine from CD. I have to use CD to install Fedora actually. Just make sure you're booting with EFI, NOT BIOS. Hybrid MBR's are just messy and antiquated, IMO.

Now boot into the live desktop and run 'ubiquity --no-bootloader' from terminal. Now that Linux has EFI boot-stubs, you don't need to go through Refind->Grub just to get into Ubuntu.

After install you won't have wireless. Either use ethernet cord or wifi dongle and install either 'linux-firmware-nonfree' or 'bcmwl-kernel-source'. I recommend bcmwl because (For me) the wl driver doesn't randomly disconnect like b43 driver would.
I also didn't like the verbose boot when using Refind. To show the Ubuntu plymouth bootsplash, this was all I could find that would work:
```
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
```

Sorry if that's overkill for an answer! There's just a LOT of conflicting methods floating around on how to fix various Macbook Pro issues under Linux, and I've been installing Ubuntu/Fedora since I got this Macbook new.. These methods have worked best for me.

---

