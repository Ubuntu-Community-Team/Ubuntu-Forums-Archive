---
title: "Permission issues on external media"
date: 2014-03-26
forum: Any Other OS
---

### Post by cody9 on 2014-03-26
Good evening!

Just want to start out  by saying i'm very new to linux, and have learned everything I know over the past ~3 weeks thanks to google and numerous forums. That being said, I am stuck and at I point where I have to reach out for some guidance.  I am successfully running linux elementary which is based off of Ubuntu as I understand it (I apologize if this is the wrong spot to post). I can use the main drive without any issues and got everything I wanted to done aside from installing flash but thats a separate issue that is equally as frusturating.

I am trying to access a thumb drive via USB and a SD card via a built in port on my laptop. Initially I couldn't see them at all listed under devices, so I formatted them in windows as fat32 and now they are visible. Problem is when I try to make a folder or copy a file to them I get an error message saying "There was an error creating the directory in /media/usb1. Error creating directory: Permission denied"   If I click on the drive and click properties the info shows "owner=root, group=root, permissions drwxr-xr-x 755" for both drives.

What do I need to do to get access to these drives? I am the only use on the computer and am set as administrator. There aren't any files I need on these devices yet so if I need to reformat them in Linux I am open to that but didn't see a way to do that either.

Thanks in advance for the assistance, I greatly appreciate it! If you need any more information please let me know and I will answer as best I  can :)

---

### Post by coffeecat on 2014-03-26
> **cody9 said:**
> /media/usb1

I'd put serious money on your having installed the application usbmount. If you have, please uninstall it. Then the autmounting functionality built into the desktop versions of Ubuntu will work as they should. Usbmount is designed for server installations and breaks usb mounting of the GUI.

---

### Post by coffeecat on 2014-03-26
I didn't notice this when I posted before:

> **cody9 said:**
> I am successfully running linux elementary which is based off of Ubuntu

I've moved this to Other OS/Distro Support as the main support forums are only for the official flavours of Ubuntu. Elementary uses its own desktop GUI which may or may not have the USB mounting functionality of the official flavours, so my assumption that you have installed usbmount may or may not be correct. Did you? :)

---

### Post by cody9 on 2014-03-31
You were 100% correct! When you mentioned that, I immediately looked at my installed programs and I didn't see it but when I looked at the history I saw it. At first I was stumped at how to remove it but then I did a search for it and it said installed so I just removed it that way. I'm guessing I tried to install that as a fix when the usb drive what wasn't formatted properly wasn't showing up. From what I understand though, NTFS formatted drives should work properly in Linux generally, although on mine they don't seem to...More inviesigation is needed on that front but I was wanted to let you know that you were correct and to thank you! :D

---

### Post by pkadeel on 2014-04-03
> **cody9 said:**
> From what I understand though, NTFS formatted drives should work properly in Linux generally, although on mine they don't seem to...
For NTFS formated drives you might need to have installed ntfs-3g package.

---

