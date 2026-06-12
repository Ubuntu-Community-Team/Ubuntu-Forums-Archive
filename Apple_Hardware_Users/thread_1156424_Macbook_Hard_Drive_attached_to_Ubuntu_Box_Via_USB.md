---
title: "Macbook Hard Drive attached to Ubuntu Box Via USB"
date: 2009-05-11
forum: Apple Hardware Users
---

### Post by gizzardjr on 2009-05-11
I have a notebook which has crashed.  The user split pop or something in it.  Well I can attach and mount the hard drive to my ubuntu box but some folders are not accessable.  A good example would be most of the Users profile directors located in the "user" folder on the Mac hard drive.  I get this message when trying to access the files on the mac notebook hard drive from my ubuntu box connected via usb.

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "Pictures".

So when I try to chmod or chown I get this message

chmod: changing permissions of `Macintosh HD/Applications/Address Book.app/Contents/Resources/pt.lproj/ABSelectEncodingsPanel.nib': Read-only file system

READ-ONLY File System!!!!

This is killing me I need to get this data off the hard dirve.

Any help would be greatly appriciated.

---

### Post by cyberdork33 on 2009-05-12
those files belong to another user, therefore your Ubuntu user cannot mess with them. root, however, can override user permissions.

Open a nautilus browser with gksudo.

---

