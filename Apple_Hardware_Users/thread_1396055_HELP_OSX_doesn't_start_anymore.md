---
title: "HELP: OSX doesn't start anymore"
date: 2010-02-01
forum: Apple Hardware Users
---

### Post by Romu on 2010-02-01
Hi all,
I made a mistake and need some help.

I tried to install Ubuntu on a USB HDD on my Macbok Pro 5.3. Everything seemed to be fine, but while rebooting the computer, OSX doesn't start anymore.

So, I would say I erased the boot sector of the internal HDD or something similar but I'm not an expert.

My internal HDD seems to be fine:
One 200 MB FAT32 partiton partition labeled EFI and with the boot flag,
One HFS+ partition for the system.

I tried to boot with the Snow Leopard DVD and run the Disk Utility to make a "repair". The repair was fine, but the Mac still doesn't boot anymore.

Anyone to help me? (Forget Ubuntu, it's only OSX related, I'll try again Ubuntu only when I'll be able to boot OSX again).

Thanks.

---

### Post by jml on 2010-02-01
Does your Mac boot with the USB HDD plugged in?  If it does, that means that the boot sector was moved to the USB drive.  While there may be a way to fix this.  I would suggest that if you can, get the files that you need off the Mac.  Do a clean install of OSX then restore your files. Then have another go at installing Linux. Good luck.

Joe

---

### Post by Romu on 2010-02-02
Thanks JML,
I remembered that I didn't click the "Advanced" button to install the Grub on the USB HDD. So, I guess Grub was installed on the internal Mac HDD.

I would imagine there is a way to restore the OSX boot sector without doing a clean install. :(

---

### Post by linuxopjemac on 2010-02-02
try to remove the boot code in the MBR, so you at least boot osx (from liveCD)
```

sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```

---

### Post by Romu on 2010-02-02
Thanks linuxopjemac,
But could you please describe a bit more your proposal?

Because, I can boot a bootable CD/DVD, I can boot the Ubuntu CD or the Snow Leopard DVD, no problem at all. Following some advices on other forum, I tried to re-install Snow Leopard, re-installing it's not a big deal and OSX keeps the data already stored on the HDD.

But this doesn't fix my problem, if I don't reformat the HDD, re-installing OSX doesn't change the boot sector. My Mac still doesn't boot :frown:

So to run your command, I guess I should boot with the Ubuntu CD, right? What this will do on the HDD and what result should I expect?

Anyway, thanks for you help.

---

### Post by linuxopjemac on 2010-02-03
you have to do it from the liveCD of Ubuntu. It will (if present) clean up boot information in the MBR. It is possible that OSX can't boot because of that. It should not harm anything.

Try to boot with option command too (alt), so you are confronted with different boot options.

---

### Post by Tycho59 on 2010-02-03
If all you want to do is switch between Mac OS X and Ubuntu try holding down Option key.  Once you  hear the startup chime, press the option key and you will be shown a screen with every disc (HardDrive/CD/DVD) that you can boot from.  

Hope this helps you.

---

### Post by zAfi on 2010-02-04
> **Tycho59 said:**
> If all you want to do is switch between Mac OS X and Ubuntu try holding down Option key.  Once you  hear the startup chime, press the option key and you will be shown a screen with every disc (HardDrive/CD/DVD) that you can boot from.  

Hope this helps you.
this! Or you can boot directly by pressing x after pressing the power key.

There's no need to overwrite the internal MBR, I just installed Karmic on a 5,1 MacBook and wrote Grub2 to the mbr (because it didn't boot with grub at /boot) and everything works as it did before.

---

### Post by Romu on 2010-02-05
Hi guys (maybe girls),
I didn't find the time to try the "linuxopjemac" tips.

@Tycho59: Thanks, I'll give this a try.

@zAfi: I already crashed my internal HDD MBR. All I want to do know is to recover a way to boot normally again.

I tried the following tips in the past 2 days:
- Pressing Alt at startup: doesn't work
- Resetting PRam: same,
- booting with a Techtool DVD: Techtool is not able to perform any task on my hdd, strange.

Here I am, more news soon.

---

### Post by Romu on 2010-02-07
> **linuxopjemac said:**
> try to remove the boot code in the MBR, so you at least boot osx (from liveCD)
```

sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```

So, I tried and same.

I finally fix the problem like this:
- I installed OSX on the USB HDD,
- backup the data on this external HDD
- then re-installed Snow Leopard from scratch, re-do the partitionning and formating.

Everything runs fine now.

---

