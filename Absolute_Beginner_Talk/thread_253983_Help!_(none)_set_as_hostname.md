---
title: "Help! (none) set as hostname"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Kouros on 2006-09-09
Can anyone help? As the fool I am, I've accidentally changed my hostname to blank on my networking GUI settings... obviously this now shows up as (none) in the terminal and login.

I've since heard that this can lead to problems in Gnome, and indeed it has. Networking will no longer load to allow me to change it back, and I do not seem to be able to edit the /etc/hostname file...

Any advice would be gratefully received! ](*,)

---

### Post by bodhi.zazen on 2006-09-09
LOL, Try:
```
sudo hostname hostname
```
whare hostname=your old hostname (or new if you want)

If that does not work:
```
sudo nano /etc/hostname
```
enter your hostname in this file.
Ctrl-X to exit; "Y" to save.

---

### Post by Kouros on 2006-09-09
Hi,

Thanks for the response. I have tried both of these solutions. These are the responses I get...

For sudo hostname hostname (obiously relacing the second hostname with my own choice) I get:-

```
sudo: unable to lookup (none) via gethostbyname()
```

I get exactly the same response for your second suggestion! Is there anything else I may be missing? Thanks!

---

### Post by bodhi.zazen on 2006-09-09
If you set the hostname, reboot.

If not, boot with the "live cd", mount and edit HD-Mount_point/etc/hostname from the CD.

---

### Post by Kouros on 2006-09-09
Ah! That's where I get even more unstuck. I am runnig a Thinkpad X20 and was only able to find a way to install from a Windows netinstall procedure from XP ([https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows))

---

### Post by bodhi.zazen on 2006-09-09
Well, I won't ask why.

Looked at the site, did you partition and install ubuntu in a Linux partition? If so, you should be able to access the partion with the  live CD.

If not, can you then access the file (/etc/hostname) if you boot to windows?

---

### Post by Kouros on 2006-09-09
You can ask why if you like - the thinkpad X20 does not have an internal CD drive, and the external one isn't bootable (or at least the one I have isn't).

I am not dualbooting to Windows on this laptop, just to make things more fun.

If you could recommend a way to reinstall from this point, would gladly go down that route - nothing of any importance is on the lappy yet.

---

### Post by bodhi.zazen on 2006-09-09
LOL. You are more of an expert then I with such an install.

Perhaps I can help you boot to CD ROM.

Starting with the obvious, did you set your BIOS to boot to CD ROM as the first device?

Do you have a floppy drive you can boot to?

With your ubuntu install, did you try booting to recovery mode?

---

### Post by Kouros on 2006-09-09
Yes, I did set the BIOS to CD ROM - well, I would if it were an option, but it's not. I can boot from floppy, but am not aware of a floppy Ubuntu install. Even if I use Smartboot Manager it still doesn't recognise the CD Drive.

I have just attepted to boot to recovery mode. These are the results I get from following your advise at the top...

HURRAH! I tried the "hostname mercer" command (with mercer as the new hostname natch) with success! When I log into Gnome from here, I have my hostname back.

**BUT** when I reboot, it is no longer there! Whether this is connected or not, I still cannot load the Networking application, and this after rebooting! Thanks for all your help so far... any other ideas what may be causing this?

---

### Post by bodhi.zazen on 2006-09-09
Looks like you need to update your BIOS to boot from CD ROM.

This should not be difficult. Start here
[IBM](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4P52BM)

As far as your hosts file, I do not know.

I would write a (boot) script to re-set your host name when you boot.

Or start a new thread re: Hostname reset at boot?

---

### Post by bodhi.zazen on 2006-09-09
Since you do not have windows installed (He he he...),

Here are instructions on how to do this with a BIOS disk
[Update with BIOS disk](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4P52BL)

---

### Post by Kouros on 2006-09-09
Sorry, I should have said, I have updated the BIOS - no joy.

I'm getting a little close to chucking the whole thing in the bin, and getting a new(er) lappy.

---

### Post by bodhi.zazen on 2006-09-09
Here is a how-to in Gentoo to create a grub floppy to boot to CD without using BIOS.

You will have to adapt, but it may work.

[Gentoo GRUB boot CDROM](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB)

Otherwise google GURB how to boot CDROM....

---

### Post by bodhi.zazen on 2006-09-09
And here is another how-to for Knoppix. Looks easier to follow:

[Grub Boot to CD](http://linuxgazette.net/107/anonymous.html)

> Consider the following (chain) boot loaders:

    [http://bootcd.narod.ru/bcdw150z_en.zip](http://bootcd.narod.ru/bcdw150z_en.zip)
    [http://btmgr.sourceforge.net/download.html](http://btmgr.sourceforge.net/download.html)

Both of them can create a boot diskette that starts a (bootable) CD even if the CD-ROM is unable to boot.

---

### Post by Kouros on 2006-09-09
Thanks - I've tried Smartboot Manager before, and to no avail. It just doesn't see the CD drive.

---

### Post by bodhi.zazen on 2006-09-09
> **Kouros said:**
> Thanks - I've tried Smartboot Manager before, and to no avail. It just doesn't see the CD drive.

OK, now you are just being difficult. I am soooooo glad I did not ask why.

My only other thought for you (just came to me) is you may need to edit your hosts file as well.

in /etc/hosts you should have a like like this:
> 127.0.0.1 localhost.localdomain mercer
Assuming mercer is your new host name.

---

### Post by Kouros on 2006-09-10
> **bodhi.zazen said:**
> OK, now you are just being difficult. I am soooooo glad I did not ask why.

My only other thought for you (just came to me) is you may need to edit your hosts file as well.

in /etc/hosts you should have a like like this:

Assuming mercer is your new host name.

I probably am being difficult, but not intentionally - maybe it's the hardware I'm using, it is somewhat antiquated.

Alas, still no good, Permission Denied to change the file above! I give up!

This reply does bump the thread... maybe someone else will see it, and know of another way, otherwise to the bin the lappy goes, and to the store go I.

---

