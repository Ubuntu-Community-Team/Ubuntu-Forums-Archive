---
title: "What download???"
date: 2013-01-28
forum: Apple Hardware Users
---

### Post by anw0625 on 2013-01-28
I just tried twice to download and burn to a disk 12.10 ubuntu and when I insert the dist it comes up a error.  Am I doing something wrong?

---

### Post by oldfred on 2013-01-28
How are you writing it to DVD or flash drive? You have to install it not copy, so it is extracted and becomes bootable. The ISO is not directly bootable.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

    
Many also like this:
       How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

            [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by anw0625 on 2013-01-28
I am trying to do it from a dvd.  I have tried both from the utilities and from burn.  Should I be using the 32 bit or 64 bit?

---

### Post by anw0625 on 2013-01-28
I have a macbook pro and I burn the dvd and it is verified I insert the dvd and it says: "the disk you inserted was not readable by this computer" what am I doing wrong?

---

### Post by iMac71 on 2013-01-29
> **anw0625 said:**
> I have a macbook pro and I burn the dvd and it is verified I insert the dvd and it says: "the disk you inserted was not readable by this computer" what am I doing wrong?first of all, you should use a DVD-RW.
This said, proceed as follows:

[LIST=1]
[*]download the ISO from [this link]("http://releases.ubuntu.com/quantal/"); if you have a core 2 you can download the 64 bit release (I suggest the Mac-specific one), otherwise you have to download the 32 bit one;
[*]burn it on the DVD;
[*]once the burning process has ended, reboot your mac while holding the ALT key;
[*]when the icons of the HD and of the DVD are displayed, click on the DVD icon (don't care that the DVD is labeled as Windows): the installation process will then start.
[/LIST]

---

### Post by imacg3ppc on 2013-02-20
i think we're missing a step here.

Don't just burn the .iso file to a cd or dvd. It has to be "extracted", if you will, from the image somewhat like a .zip file.

In windows 7 you dont need any app to do this you can just double click the iso and it will burn the proper way.

in mac you will need toast or whatever utility to "Burn CD/DVD Image" and select your install iso.

If you just drag the iso onto a disc you will have a disc with an iso file on it.

---

