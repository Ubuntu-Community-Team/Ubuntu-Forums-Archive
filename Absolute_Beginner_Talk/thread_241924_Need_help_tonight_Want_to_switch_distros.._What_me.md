---
title: "Need help tonight: Want to switch distros.. What mess Have I got Myself into."
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-08-23
There are a few things I am hoping a couple other distros might fix..(Mandriva, mepis)

Laptop doesnt really sleep.. Fan still stays on and overheats potentially killing a 1000 dollar device.

Too long of a boot time.

I think I might have messed up my install and I want to start over...

BUT: I need to know how to do this because of the following..

I have a dual boot set up through the ubuntu install. I don't know how to reconfigure this so that ubuntu isnt listed any more and instead mandriva or mepis is..

What about my swap partition and my ubuntu partition.. How do I tell the new distro to use the old ubuntu partition as the new os partition and the old ubuntu swap partition as the new os swap partition..

Please some help guys, ubuntu is great but need better hardware support for my lappy.

Thanks.

---

### Post by bodhi.zazen on 2006-08-23
1. Research your laptop and identify which distro seems best.

2. Install depends a little on the distro BUT in general it should go without any problem.

The "new distro" will recognize and use swap just fine.

The "new distro" will ask where to install (root or /), just choose the ubuntu (root or /) partition.

No need to re-partition.

---

### Post by zxee on 2006-08-23
> I have a dual boot set up through the ubuntu install. I don't know how to reconfigure this so that ubuntu isnt listed any more and instead mandriva or mepis is..


If mepis or mandriva don't set up your grub _or_ for some reason you want to keep the grub you have you will need to edit /boot/grub/menu.lst. You can have those distros install grub to the boot partition, and then use rootnoverify (hdx,x) <you supply the actual drive and partition designation.
After rootnoverfiy insert below that chainloader +1 and you should be in business. You have to have a title too so it would all look like this in menu.lst:
> title mepis
       rootnoverify (hdx,x)
       chainloader +1

---

### Post by bodhi.zazen on 2006-08-23
Not so sure about that grub entry zxee. I thought chainloader was for Windows and BSD.

Should it not look something like this
```

title Mepis
rootnoverify (hdx,y)
kernel=/boot/vmlinuz-x.y.z root=/dev/hdxy ro
initrd=/boot/initrd-x.y.z
boot
```

Not sure of which partition is root or the kernel/initrd for Mepis.


At any rate, you boot menu will be updated when you install "new linux" if you install GRUB to the MBR.

---

### Post by zxee on 2006-08-23
> **bodhi.zazen said:**
> Not so sure about that grub entry zxee. I thought chainloader was for Windows and BSD.

Should it not look something like this
```

title Mepis
rootnoverify (hdx,y)
kernel=/boot/vmlinuz-x.y.z root=/dev/hdxy ro
initrd=/boot/initrd-x.y.z
boot
```

Not sure of which partition is root or the kernel/initrd for Mepis.


At any rate, you boot menu will be updated when you install "new linux" if you install GRUB to the MBR.

I multiboot 7 distros at present and I use chainloader for several of them with no problems. chainloader works fine with linux.

---

### Post by bodhi.zazen on 2006-08-23
Thanks for the info then. I will try it as it obviously is easier.

---

### Post by deadgobby on 2006-08-23
A distro that is good is Suse 10.0 You can either set KDE or Gnome while installing. You need at least 256mb of ram and a P4, I have Suse on a other box and found the hardware with out any problems. Suse is a 5 disk install and depending on ram and proccesor speed. It will take about an hour to install. It took about a day to DL the iso's from Piratebay.org. YOu still need to install the codecs on your own and the repos are set up differently. I love both Ubie and Suse. 
 Gobby

---

### Post by anaconda on 2006-08-23
Chainloader only works IF you have grub (or lilo) in the beginning of your linux partition.. 
Then chainloader just gives control to the bootloader you want to use...

SO basically you boot to GRUB from the beginning of the HD, and then chainload ANOTHER grub from the beginning of the partition you want to boot the OS...

And yes, it is simpple.

---

### Post by zxee on 2006-08-23
> **anaconda said:**
> Chainloader only works IF you have grub (or lilo) in the beginning of your linux partition.. 
Then chainloader just gives control to the bootloader you want to use...

SO basically you boot to GRUB from the beginning of the HD, and then chainload ANOTHER grub from the beginning of the partition you want to boot the OS...

And yes, it is simpple.

That's what I said in my orginal response.

> You can have those distros install grub to the boot partition, and then use rootnoverify (hdx,x) <you supply the actual drive and partition designation.

---

