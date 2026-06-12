---
title: "Can I use Ubuntu to read/copy off failed Mac internal drive?"
date: 2017-09-14
forum: Apple Hardware Users
---

### Post by mike431 on 2017-09-14
Hello guys, in windows machines, I have used Parted magic and Puppy Linux bootable linux discs in the past to copy  data off failed internal HDD's which won't boot, can i do the same on mac machines if I create a bootable Ubuntu linux disc please? If yes, is there a mac specific linux iso or is there one which I can use on both pc and mac?

---

### Post by &amp;KyT$0P# on 2017-09-14
Yes.  Ubuntu can read Mac OS partitions.

In order to boot a Ubuntu live media on a Mac, you need to use [rEFInd]("http://www.rodsbooks.com/refind/").

---

### Post by mike431 on 2017-09-14
Thank you very much I will look into that tomorrow, sorry I forgot to mention that I will be creating a boot disk from a pc. I use paid version of transmac to create bootable mac media, can that work? If yes, all I would need then is a dmg or iso file for ubuntu, if that can work can you link me to that exat ubuntu download file please?

---

### Post by mike431 on 2017-09-16
> **halogen2 said:**
> Yes.  Ubuntu can read Mac OS partitions.

In order to boot a Ubuntu live media on a Mac, you need to use [rEFInd]("http://www.rodsbooks.com/refind/").

I downloaded the rEFInd iso file and created a bootable CD with it via Imgburn,  it works when I pop it in a mac but I am not understanding how to get  the Ubuntu software [iso] unto the rEFInd CD, can anyone advise please?

---

### Post by &amp;KyT$0P# on 2017-09-16
> **mike431 said:**
> I downloaded the rEFInd iso file and created a bootable CD with it via Imgburn,  it works when I pop it in a mac but I am not understanding how to get  the Ubuntu software [iso] unto the rEFInd CD, can anyone advise please?
You don't put both on the same media.  Keep your rEFInd CD as-is, and create a separate live USB for Ubuntu.

---

### Post by mike431 on 2017-09-16
Oh, so i boot the eRFInd first, eject that CD after the software is loaded then insert and boot the Ubuntu disc?

---

### Post by &amp;KyT$0P# on 2017-09-16
Not sure if that way would work or not.  I would insert both the rEFInd CD and Ubuntu disc, then boot into the rEFInd CD and select the Ubuntu disc.

---

### Post by Geoffrey_Arndt on 2017-09-16
You can always get the iso image of any Linux distro by starting out at Distrowatch.com.   Also, a great tool recently introduced for creating USB Bootable Disks (highly recommend usbv3) is "Etcher"

Distrowatch here:   [http://distrowatch.com](http://distrowatch.com)   Etcher here:   [https://etcher.io/](https://etcher.io/)

---

### Post by mike431 on 2017-09-17
> **halogen2 said:**
> Not sure if that way would work or not.  I would insert both the rEFInd CD and Ubuntu disc, then boot into the rEFInd CD and select the Ubuntu disc.

That would mean having to first boot eRFInd from the internal drive then booting Ubuntu from an external drive? If yes, then what would be the situation with a mac which doesn't have a dvd drive?

---

### Post by &amp;KyT$0P# on 2017-09-17
You could put rEFInd on a USB and boot from that.

---

### Post by HermanAB on 2017-09-18
It should work if the Mac disk is not encrypted.

---

### Post by radioactive.exe on 2017-09-18
I have a MacBook Air 13 (2014), all up to date, and I managed to boot into Ubuntu from flash drive, via holding down the "option" key. Granted the Ubuntu I booted into, I installed onto the flash drive (so essentially the flash drive acts as a harddrive) but nonetheless, you can still easily skip rEFInd. It ends up seeing the built in harddrive as just an additional harddrive, and you can easily mount it from the unity dock.

---

### Post by slickymaster on 2017-09-18
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by mike431 on 2017-09-18
> **radioactive.exe said:**
> I have a MacBook Air 13 (2014), all up to date, and I managed to boot into Ubuntu from flash drive, via holding down the "option" key. Granted the Ubuntu I booted into, I installed onto the flash drive (so essentially the flash drive acts as a harddrive) but nonetheless, you can still easily skip rEFInd. It ends up seeing the built in harddrive as just an additional harddrive, and you can easily mount it from the unity dock.

Thanks I created a boot flash drive with Ubuntu desktop, please see attached pic. The HDD had been erased first to reload OSX but assuming I should Ubuntu on a Mac with a working but damage HDD, would this be the correct procedure to choose the Macintosh HDD tab from the left vertical menu then the "Computer" option and Mac's HDD contents will show up?

[ATTACH=CONFIG]276765[/ATTACH]

---

### Post by mike431 on 2017-09-18
Oh sorry, I have no idea why the pic is showing that way in my post so please see this link?

[https://s26.postimg.org/4mbopxzrt/Mac.jpg](https://s26.postimg.org/4mbopxzrt/Mac.jpg)

---

### Post by &amp;KyT$0P# on 2017-09-18
> **mike431 said:**
> assuming I should Ubuntu on a Mac with a working but damage HDD, would this be the correct procedure to choose the Macintosh HDD tab from the left vertical menu then the "Computer" option and Mac's HDD contents will show up?
All you need to do is click "Macintosh HD".

"Computer" is just the root of the Ubuntu's file system tree and not needed here.

---

### Post by mike431 on 2017-09-18
got it, appreciate guys, will try this out next time I work on a mac with a loaded OSX and report back here.

---

### Post by mike431 on 2017-09-18
> **Geoffrey_Arndt said:**
>   Also, a great tool recently introduced for creating USB Bootable Disks (highly recommend usbv3) is "Etcher" here:   [https://etcher.io/](https://etcher.io/)

That's a super easy utility, only 3 simple steps and works great, thanks for the link, wish it would work with discs too but no worries.

---

