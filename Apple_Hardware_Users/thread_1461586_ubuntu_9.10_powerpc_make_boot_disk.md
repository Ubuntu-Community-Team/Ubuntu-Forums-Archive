---
title: "ubuntu 9.10 powerpc make boot disk"
date: 2010-04-24
forum: Apple Hardware Users
---

### Post by hawtboi on 2010-04-24
I have OS9 and a PC with Win7.  what is the best tool to burn the CD in Windows or OS9?

I used Transmac on the PC but the G4 Cube won't boot from the disk though it reads it in OS9.

---

### Post by linuxopjemac on 2010-04-26
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by hawtboi on 2010-04-27
thanks, will try that.

---

### Post by hawtboi on 2010-04-30
none work.  I'm installing on a Power Mac G4 Cube 450.  Mac OS 9 reads the disk but won't start from it.

---

### Post by shawnhcorey on 2010-04-30
What version of the ISO are you trying?  The Desktop version does not completely fit onto a 700MB CD.  Use the Alternative CD instead.  The only difference between them is that the Desktop CD use the graphical install, the Alternative uses the text-based one.  All the other files are identical.

Some CDs allow for overburning but whether they can do it depends on the manufacturer.  If you want to use the Desktop CD, buy an oversized CD.  They're available up to 900MB.

---

### Post by avtolle on 2010-04-30
Not a direct answer, just an observation or two:

I have two Cubes. Neither will boot Ubuntu from an iso burned to CD-RW. Both will boot from CD-R burned at 8x or slower (4x is best), and will boot from DVD-R burned at a slow rate (only did it once, cannot recall speed used). Good luck.

---

### Post by hawtboi on 2010-05-02
I tried everything here.  Burned at slower speeds, on DVD and CD, why won't this thing boot from the CD?  I'm using a Lite-on DVDRW-DL unit that's about 4 years old.  Verbatim media.  I tried the desktop and alternative ISO.

The computer has a DVDROM, I tried to use another DVDROM and CDROM.  I tried holding down the Option key, Command key, C key or the Command-Option-F-I key combo.

is there something that I can use to burn the disk from withing OS9 and maybe the computer needs an update?

---

### Post by llamabr on 2010-05-02
> **hawtboi said:**
> I tried everything here.  Burned at slower speeds, on DVD and CD, why won't this thing boot from the CD?  I'm using a Lite-on DVDRW-DL unit that's about 4 years old.  Verbatim media.  I tried the desktop and alternative ISO.

The computer has a DVDROM, I tried to use another DVDROM and CDROM.  I tried holding down the Option key, Command key, C key or the Command-Option-F-I key combo.

is there something that I can use to burn the disk from withing OS9 and maybe the computer needs an update?

So you've got the disk burned, and now you're trying to install via an external cd rom?  It seems the question has changed slightly.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by shawnhcorey on 2010-05-02
> **llamabr said:**
> So you've got the disk burned, and now you're trying to install via an external cd rom?  It seems the question has changed slightly.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

The question has changed a lot.  The only way to boot a PowerMac from any device other than the internal hard drive or the internal DVD/CD is through Open Firmware.

See [Linux on your Apple Mac]("http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=85") and search for **HOWTO Boot PowerMacs From A USB Drive In Open Firmware**.  Modify the technique as needed.

---

### Post by linuxopjemac on 2010-05-02
Yes, booting with USB is possible, although not with all Macs. I have two Pismo PowerBooks, exactly the same models. One will boot from USB, the other not.

dd an iso to a stick like
```
sudo dd if=/your_installation.iso of=/dev/sda
```
where /dev/sda could be your USB stick....find this out with Gparted !!!

Then boot from USB in open firmware either with:
```
boot usb0/disk@1:2,\\yaboot
```
or
```
boot usb1/disk@1:2,\\yaboot
```

good luck

---

### Post by hawtboi on 2010-05-02
i'm NOT booting from an external device.

---

### Post by hawtboi on 2010-05-02
i'm NOT booting from an external device.

---

