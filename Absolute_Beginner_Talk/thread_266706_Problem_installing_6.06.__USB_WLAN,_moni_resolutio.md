---
title: "Problem installing 6.06.  USB WLAN, moni resolution, sound, and drive mnting problems"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by darrellfjohnson on 2006-09-27
I tried using Ubuntu 6.06 the other day, and it was kind of a disaster.  When I booted the Live CD, I couldn't increase my resolution (it was stuck at 640x480), my wireless USB adapter wouldn't work (it froze when I tried to activate it, and I had to restart),I couldn't mount my hard drives that were formatted with NTFS (they were detected in the 'Computer' menu, but when I double clicked them an error message popped up.), and I had no sound from my Soundblaster X-Fi soundcard.  

Thinking that it was just that there were no drivers included with the Live CD, I went ahead and installed it.  Well once it did its thing and I restarted I couldn't boot.  It just said 'Error with Operating system' in the POST screens and wouldn't get past that.  I could boot the CD, and then select Boot from hard drive from there, but I still had the same problems.  I couldn't activate my USB wireless adapter, my resolution wouldn't increase any, I couldn't mount my NTFS formatted HDDs, and I still had no sound.  Is this just a problem with unsupported hardware? Are there some drivers that I need to download? My specs are:

3500+ Athlon 64
Abit AN8 32x motherboard
1.0GB PC3200 RAM
160GB Seagate SATA II HDD (Ubuntu was installed on this)
2x Maxtor 200GB IDE HDD (NTFS formatted HDDs)
nVidia 7900GT PCI Express videocard
Viewsonic G90fb
Soundblaster X-Fi
Zonet ZEW2500P USB wireless adapter

Thanks in advance for any help.

---

### Post by darrellfjohnson on 2006-09-27
bump to get it back on the first page

---

### Post by darrellfjohnson on 2006-09-27
Well, I looked in the Zonet manual and it says that it supports the 2.4.18-3 kernel of Linux, so I assume it is supported by Ubuntu.  But why does it lock up every time that I configure and activate it?  It makes no sense.

As for the resolution problem, I'm going to try to install the nVidia driver, hopefully that solves my problem.

---

### Post by darrellfjohnson on 2006-09-28
Sorry to keep bugging about this, but I fixed one problem, partly fixed one problem, and gained another one, which is worse than the one I fixed.

I managed to configure my wireless USB adapter by repeatedly going through some steps, then restarting until I did them all without the system freezing up on me.  So now my USB wireless adapter is configured.  It just doesn't work.  I can't ping, I can't traceroute, I can't go to any websites, nothing.  I've tried configuring it with a static IP, and DHCP and still nothing.

I also managed to get Ubuntu to boot.  For some reason I had to change the boot order of my hard drives so that my NTFS formatted backup drives are higher than my SATA 2 main drive where Ubuntu is actually installed.  I have no idea why, but now I can boot into Ubuntu.

But now I have a worse problem.  I tried dual booting, but I can't boot into Windows anymore.  Whenever I restart, the GRUB bootloader comes up with a couple of options.  Boot in Ubuntu, boot into Ubuntu (safe config, or something like that), Memtest86, and Windows XP Pro.

When I chose XP Pro, this shows up:

```
Booting 'Microsoft Windows XP Professional'
root (hd2,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
map(hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

and then it just stays there and does nothing.

I really need some help because at this point I'm extremely frusterated.  My Linux install is completely useless with Internet access or a higher resolution, and I can't boot into Windows where my stuff works.  Please help.

---

