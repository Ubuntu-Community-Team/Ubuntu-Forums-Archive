---
title: "Install Ubuntu to USB drive"
date: 2006-11-29
forum: Apple PPC Users
---

### Post by macman213 on 2006-11-29
Hi,
I'm trying to install Ubuntu to an external usb drive with macosx. I have simply no idea how. Can anyone help me???:confused:

---

### Post by ciscosurfer on 2006-11-29
> **macman213 said:**
> Hi,
I'm trying to install Ubuntu to an external usb drive with macosx. I have simply no idea how. Can anyone help me???:confused:This is helpful: [http://www.google.com/search?q=install+ubuntu+to+usb+drive&ie=utf-8&oe=utf-8&rls=Swiftfox:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=install+ubuntu+to+usb+drive&ie=utf-8&oe=utf-8&rls=Swiftfox:en-US:unofficial&client=firefox-a)

You may find this helpful as well: [http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html](http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html)

---

### Post by Torrance on 2006-11-29
I've done this before by having the boot partition on the main disk, and then the rest of the root on the usb disk. So basically you just configure the disk names during installation, and Ubuntu sets up yaboot which loads from /boot on your main disk, which then loads the /root from your USB disk.

The reason I did this was because I wasn't able to get yaboot to recognise and load directly from a USB disk, without loading the linux kernel first to recognise it (openfirmware, the base software on an apple system, doesn't pcik up on USB disks at this early stage). But I also seem to remember once seeing an argument that you could add to yaboot that would force it recognise USB disks...

---

### Post by macman213 on 2006-11-30
a

---

### Post by macman213 on 2006-11-30
I'm sorry but none of those links were helpful

---

### Post by ciscosurfer on 2006-11-30
> **macman213 said:**
> I'm sorry but none of those links were helpfulAre you trying to install Ubuntu on a USB disc that will also include Mac OS X or are you trying to install Ubuntu onto a USB stick *from* Mac OS X?  If it's the latter, perhaps a Mac forum would be better suited to your question.

Keep searching the forums here or you can also search on Google for some answers to your question.  I'm not trying to be snide, I just don't know what else to offer up to you.

---

