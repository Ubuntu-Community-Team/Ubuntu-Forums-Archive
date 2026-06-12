---
title: "Installing a Macbook Pro 2019 with ubuntu-21.10-desktop-amd64"
date: 2022-02-05
forum: Apple Hardware Users
---

### Post by dstromberg on 2022-02-05
I'm attempting to perform the install (to an external USB-C disk) described in the title.

It seems no matter what I try, I get a black screen shortly after selecting my external disk to boot from.

I tried copying the .iso to my little USB flash drive using dd on macOS or cp on Linux.  I also tried converting the .iso to .img using:
[INDENT]hdiutil convert ubuntu-21.10-desktop-amd64.iso -format UDRW -o ubuntu-21.10-desktop-amd64.img
[/INDENT]
...but I still get a black screen when I try to boot from it.  BTW, I got a .img.dmg file, not a .img file, and dd'd that.

What do I need to do to initiate the install process?

Thanks!

---

### Post by dstromberg on 2022-02-05
I could've been more clear: the install never starts; when I boot from the little flash drive with Ubuntu's installer on it, that's when I get the black screen.

---

### Post by QIII on 2022-02-05
Moved to ***Apple Hardware Users***

---

### Post by dstromberg on 2022-02-07
I also tried erasing the drive, as described at [https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#3-prepare-the-usb-stick](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#3-prepare-the-usb-stick) .  It did not appear to help.

I'm going to try Etcher as an alternative to dd and cp, but probably not right away.

---

### Post by dstromberg on 2022-02-12
I followed all of [https://ubuntu.com/tutorials/create-a-usb-stick-on-macos](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos) in full detail, including erasing the USB-C flash drive and giving it a GPT partition table, and using etcher, but still I get nothing but a black screen when booting from the flash drive with the Ubuntu 21.10 amd64's installer on it.  I can see an external disk light blinking, so the system seems to be doing *something*, but whatever it is, I can't see it on the display.

I did not try to write a .img file.  I seemed to be getting a .dmg anyway.

---

### Post by dstromberg on 2022-02-12
I just tried UNetbootin, but it had the same problem as Etcher, dd and cp: shortly after booting from the flash drive that contains the Ubuntu installer, the screen goes black and stays black.

---

### Post by draginbyu on 2022-02-20
You've gotten farther than me,  I cant even get to the install screen

Im using a 2021 A2442 macbook pro and I have created the bootable however I cant even get it to recognize on the Startup Options.  I only see the MAC HD and Options however nothing else appears. Did you come across this or did yours boot up to the install screen from first try?  Your an error ahead of me it seems :)

---

### Post by albertobarbes on 2022-02-22
You can try using balena ([https://www.balena.io/etcher/](https://www.balena.io/etcher/)) to create the USB bootable. It worked perfectly for me...

Good luck :P

---

### Post by albertobarbes on 2022-02-22
Sorry; I see you've already tried that...

---

### Post by gsahli on 2022-02-26
I'm sorry to say I'm not sure from your description(s) what is happening...
Is it actually booting but ending in a black screen? That's more likely a graphics card/driver issue.
Or is it not booting?
I used reFind as my bootloader besides making the USB stick. Did you consider this?
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
Did you try a more tried and tested long term support version 20.04?
Please try to give us all the details - we're not there with you.

---

