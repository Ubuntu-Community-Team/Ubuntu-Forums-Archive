---
title: "reinstall macos after ubuntu"
date: 2021-09-01
forum: Apple Hardware Users
---

### Post by mkborregaard on 2021-09-01
Not really a ubuntu question, sorry, but I was hoping someone here could help me.

I have a macbook pro retina 13'' 2015 and have ubuntu installed. Now my daughter has inherited the machine, and she greatly prefers the original MacOS. I'd like to reinstall MacOS Big Sur.

AFAIU I should create a bootable big sur usb, and also (perhaps using that) reformat my harddrive to APFS (apple's file system) (and rename the disk to Macintosh HD). I think gparted can do macos file system extended but not APFS.

Can anyone help me direct me how I can go about this? I do have access to a mac with macos installed if that is helpful.

Thanks!

---

### Post by scorp123 on 2021-09-02
Just boot with MacOS Big Sur and let it handle all the disks. If the installer doesn't recognise any usable harddrive / SSD then launch the "Disk Utility" (from MacOS's installer screen) and let it erase the harddrive. The installer should definitely be able to recognise the harddrive / SSD after that.

---

### Post by scorp123 on 2021-09-02
> **mkborregaard said:**
>  I do have access to a mac with macos installed if that is helpful.

As for the "boot with MacOS Big Sur" part I mentioned in my previous post:  You will need to create a bootable USB stick for your other Mac.

[https://9to5mac.com/2020/09/03/how-to-create-bootable-macos-11-big-sur-usb-install-drive-video/]("https://9to5mac.com/2020/09/03/how-to-create-bootable-macos-11-big-sur-usb-install-drive-video/")

---

### Post by mkborregaard on 2021-09-05
Thanks a lot Scorp123, it does sound very promising, and I was able to generate the big sur installer usb by following the instructions in the link you provided. 
However, I don't seem to be able to boot from it. On a Mac you would normally hold down "Option" under startup to enter the boot menu, but no matter what I press during startup it just enters into the ubuntu install. How would I boot into the USB?

(Just an additional consideration, which may not be important but may be: When this machine had MacOS installed, the keyboard and trackpad didn't work, and I only used it with an external keyboard and mouse. After installing Ubuntu on the machine, it magically started working! So if you are supposed to have it enter the boot menu by pressing Option even with ubuntu installed, I wonder if maybe the MacOS and BIOS use a different keyboard listening protocol and so the mac bios simply just doesn't register the keystrokes. Just a thought I'd mention.)

---

### Post by sferguson3 on 2021-11-01
Apologies for replying to an older thread, 

However, for others reading this. You should be able to hold down **shift, option, command + R **on an Intel based Mac - As the Mac starts up you will be given options for downloading and reinstalling Mac OS. I have used this method on a Macbook Air on multiple occasions in the past. Hope this helps.

Source: [https://support.apple.com/en-gb/HT204904](https://support.apple.com/en-gb/HT204904)

---

