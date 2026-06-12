---
title: "Installed on MacBook5,2"
date: 2009-04-04
forum: Apple Hardware Users
---

### Post by Libard on 2009-04-04
Ok, so I got a brand spankin new MacBook. I always liked dual booting into Ubuntu on the last Mac Mini I had, and it worked fine. I saw some things about installing on a MacBook5,2 that you had to do something with the ACPI. Before I changed that, it never even went past the boot screen.
After I changed the settings, it booted up and installed. No errors I could see while installing. It finished, and I restarted. When I restarted, I got a blank white screen, and nothing happened. So I tried holding down the option key to choose where to boot from. When I tried that, all I got was a folder icon that had a question mark on it. It just flashed over and over, and nothing I've done has fixed it.
Currently getting ready to take it to an apple retail store to get it repaired, but just asking around here to give people a heads up, and see if I can get some information as to why this happened.

Any help is appreciated.

---

### Post by pxwpxw on 2009-04-04
> **Libard said:**
> Ok, so I got a brand spankin new MacBook. I always liked dual booting into Ubuntu on the last Mac Mini I had, and it worked fine. I saw some things about installing on a MacBook5,2 that you had to do something with the ACPI. Before I changed that, it never even went past the boot screen.
After I changed the settings, it booted up and installed. No errors I could see while installing. It finished, and I restarted. When I restarted, I got a blank white screen, and nothing happened. So I tried holding down the option key to choose where to boot from. When I tried that, all I got was a folder icon that had a question mark on it. It just flashed over and over, and nothing I've done has fixed it.
Currently getting ready to take it to an apple retail store to get it repaired, but just asking around here to give people a heads up, and see if I can get some information as to why this happened.

Any help is appreciated.

It is normal. You need the rEFIt CD, update the MBR, that enables OSX restart. Then you need to reinstall grub to the MBR to enable boot linux. See the intel mac faq sticky.

---

### Post by Libard on 2009-04-05
It may seem like I'm stupid, but I don't really get any of that. Burning CD? Yeah, can do that. Burning a CD on Windows since I can't use my Mac? No clue.

---

### Post by pxwpxw on 2009-04-05
> **Libard said:**
> It may seem like I'm stupid, but I don't really get any of that. Burning CD? Yeah, can do that. Burning a CD on Windows since I can't use my Mac? No clue.

Should be ok to burn in windows or another mac, or there is a usb stick version I think - see the rEFIt web site.
I dont know the windows procedure.

---

### Post by Libard on 2009-04-05
Well, how would it work even if I could put it on a USB stick? I don't have a computer to run the enable.sh file, or is that not necessary? I got a friend on a Mac to get me the files from the .dmg version, but would the format of the USB stick matter?

EDIT: Running the files from the USB stick didn't work. Still didn't see it on boot up.

---

### Post by pxwpxw on 2009-04-05
> **Libard said:**
> Well, how would it work even if I could put it on a USB stick? I don't have a computer to run the enable.sh file, or is that not necessary? I got a friend on a Mac to get me the files from the .dmg version, but would the format of the USB stick matter?

EDIT: Running the files from the USB stick didn't work. Still didn't see it on boot up.

Ah, I forgot you need to bless refit.efi on the usb stick, but your friend can do that from Mac OSX with enable.sh, or using the OSX bless function, and it will be seen by your mac. It needs to be on an HFSplus (MacOS extended) partition on the usb.

Or you friend could burn a refit cd, it does not require blessing, and should be bootable, that is the way I recover from the unbootable OSX situation, the refit cd should still boot.

One other possibility is you may still be able to boot a utuntu i386 live cd if thats what you have  (restart using the option key). If so, you can download a linux refit package and run gptsync from ubuntu desktop to update the MBR. (Dont think the package is available for amd64)
```

sudo apt-get update
sudo apt-get install refit
sudo gptsync /dev/sda

```

---

### Post by Libard on 2009-04-05
Well, thanks that was really helpful.
Unfortunately, didn't realize what format my flash drive had to be, it's fat 32 I'm pretty sure. He's also not local, being a friend online. Also unfortunately, I have the Ubuntu 9.04 live CD (I think, I installed from it anyway) amd64 version, as he said that since my MacBook is x86_64, I'd have to install that one. It doesn't really matter right now. If you don't get back to me by tonight, then I'll be taking it way outa town to see if it will get repaired, $90 for the consulting fee. I'll try booting from the CD before I take it though.

Edit: There is no rEFIt for amd64 9.04 it seems. I can't burn a disk, or fix the partitions any other way could I?

Edit2: Thanks for all your help. I just did it a different way. Used the DVD I burned to start up successfuly for once, and made a new partition map from within it. Got the MacOSX disk to boot up, and am currently installing MacOSX once again in my MacBook, couldn't be happier, :D

---

### Post by pxwpxw on 2009-04-06
> **Libard said:**
> Well, thanks that was really helpful.
Unfortunately, didn't realize what format my flash drive had to be, it's fat 32 I'm pretty sure. He's also not local, being a friend online. Also unfortunately, I have the Ubuntu 9.04 live CD (I think, I installed from it anyway) amd64 version, as he said that since my MacBook is x86_64, I'd have to install that one. It doesn't really matter right now. If you don't get back to me by tonight, then I'll be taking it way outa town to see if it will get repaired, $90 for the consulting fee. I'll try booting from the CD before I take it though.

Edit: There is no rEFIt for amd64 9.04 it seems. I can't burn a disk, or fix the partitions any other way could I?

Edit2: Thanks for all your help. I just did it a different way. Used the DVD I burned to start up successfuly for once, and made a new partition map from within it. Got the MacOSX disk to boot up, and am currently installing MacOSX once again in my MacBook, couldn't be happier, :D
That sounds interesting.

I posted a new thread for i386/amd64 gptsync packages in case you need it again

gptsync packages for MBR sync update intel macs
[http://ubuntuforums.org/showthread.php?t=1117464](http://ubuntuforums.org/showthread.php?t=1117464)

---

