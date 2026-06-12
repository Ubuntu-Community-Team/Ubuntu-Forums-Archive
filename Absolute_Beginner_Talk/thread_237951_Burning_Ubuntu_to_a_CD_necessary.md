---
title: "Burning Ubuntu to a CD necessary?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Badmagic on 2006-08-17
Sorry to post what’s probably an irritating question but I did not see it covered in the sticky topic instructions.

Is it possible to install Ubuntu to a brand new system large SATA drive without burning to a CD (I am in that Windows wont see sata hell at the moment), my burner still reads fine but has not burned discs in some time, its not been an issue before as I never need to burn discs but this is the deciding factor in whether I have to go and buy another burner (and discs).

On my secondary system I can hook the drive up through a sata/usb interface and I can access the disc like this through the Windows Disk Management utility so I was trying to work out if I could install directly to the new disc in this way then plug it into the new system.

Anyway, sorry again for posting what’s probably an inane question.

---

### Post by Badmagic on 2006-08-17
So I extracted the files into a folder and launched ‘Start.exe’, it tells me to leave the CD in the drive and boot from it but I am just looking to directly install this to my spare drive, anyone know how to do this?

---

### Post by Drakkor on 2006-08-17
Doesn't matter where you want to install it,you still have to burn and boot from the CD

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by bodhi.zazen on 2006-08-17
It is possible, very difficult. Beyond my technical expertice for sure.

What extraction method did you use? Some of the files may appear to be Zip files to windows, but they are not zip files and extracting them does not likely to be helpful for you.

Probable easier to borrow a CD burner or fix your current one.

---

### Post by Drakkor on 2006-08-17
Or if you want to wait you can have them ship you free copies

---

### Post by theratster on 2006-08-17
Hmm.. technically couldn't you open up the iso, and copy all the files to a USB key?

If you set up your BIOS right, you can boot off of the USB key, and then install it that way.

---

### Post by Badmagic on 2006-08-17
> **Drakkor said:**
> Doesn't matter where you want to install it,you still have to burn and boot from the CD

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

Cheers, I will just have to go and buy more.

> **bodhi.zazen said:**
> It is possible, very difficult. Beyond my technical expertice for sure.

What extraction method did you use? Some of the files may appear to be Zip files to windows, but they are not zip files and extracting them does not likely to be helpful for you.

Probable easier to borrow a CD burner or fix your current one.

I just used 7-zip, I have not experienced issues with unpacking other exe and iso files in the past but it’s always a possibility.

---

### Post by Badmagic on 2006-08-17
> **theratster said:**
> Hmm.. technically couldn't you open up the iso, and copy all the files to a USB key?

If you set up your BIOS right, you can boot off of the USB key, and then install it that way.

I can certainly try this, thanks for the tip.

---

### Post by DSn0wMan on 2006-08-17
I have used the alternate-disk/network install method for AIX (Unix) and Windows. You just point your multiboot setup to the install image on a separate drive or a network drive. I'd be suprised if there wasn't a way to accomplish this in Ubuntu. 

How do you deploy it to corporate desktops? I cant see Admins/Help desk guys running around to every desktop with a disk, and installing it.

I havn't tried it, but this thread may help.

[http://ubuntuforums.org/showpost.php?p=2493&postcount=2](http://ubuntuforums.org/showpost.php?p=2493&postcount=2)

---

### Post by Ellidi on 2006-08-17
I'm assuming there's no way to boot from the ISO image itself ?

---

### Post by jak on 2006-08-17
> **theratster said:**
> Hmm.. technically couldn't you open up the iso, and copy all the files to a USB key?

If you set up your BIOS right, you can boot off of the USB key, and then install it that way.

This won't work that easily unfortunately. It is possible, although the people working on it haven't got the Dapper Live CD booting off a USB drive just yet. You **can** do it with Hoary, just follow the instructions at [http://www.usbuntu.org/](http://www.usbuntu.org/)

Jak

---

### Post by Badmagic on 2006-08-17
Thanks for your suggestions everyone, I am afraid nothing worked so I am going to go and buy a DVD-RW today.

Just to be safe however can I burn the ISO to a blank DVD or should I buy a pack of blank CD’s?

---

### Post by Madpilot on 2006-08-17
> **Badmagic said:**
> 
Just to be safe however can I burn the ISO to a blank DVD or should I buy a pack of blank CD&#8217;s?

The ISO should fit on one standard 800Mb CD-R.[1]

You also shouldn't be unpacking it - leave it as one giant ISO file, and burn it that way.

Please see [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) which includes Windows instructions.

[1] Unless you downloaded the (much larger) DVD ISO, which obviously needs a DVD-R!

---

### Post by Drakkor on 2006-08-17
The ubuntu-6.06.1-desktop-i386.iso is 698.4 Mb,it's designed to fit on a 700 Mb 80 min CDR or CDRW. :razz: And Madpilot is right about burning the whole 
.iso image,which is what it is,**as an image**,there's no unzipping or
extracting anything from the .iso. Read the instructions on how to burn an .iso, Good Luck ! :)

---

