---
title: "Help with Macpup install !!!!!"
date: 2011-04-26
forum: Any Other OS
---

### Post by krisdeniseriley on 2011-04-26
Im installing Macpup on my netbook for the first time by way of USB. Im in the installing stage and have hit a snag. A window comes up asking to "Please find the latest Puppy files vmlinuz, initrd.gz and macpup_520.sfs, Then Highlight any one of them and click the OK button." The window has three boxes each marked Home, Desktop, and Documents, along with some basic routes to follow. Can someone help me with this install issue.....im lost!

---

### Post by stoogiebuncho on 2011-04-27
Yer in the wrong help forums :P

How are you installing it?  Are you booted from a Macpup LiveCD?  USB?

Are you doing a frugal install or a full install?

edit: I see now you said you're doing this by USB.  You'll need to navigate to your usb drive (I believe it will be in the /mnt/ folder, and may be called something like sbd1, sbd2 etc).  The files should be there.

I've never received this message when installing, however.  Can you provide more info on how you are installing it?

---

### Post by Perfect Storm on 2011-04-27
Moved to Other OS/Distro Talk.

---

### Post by macrophenomenal on 2011-05-01
Hi, 
 
 
I am running a netbook HP Mini 2133 that has no optical drive and currently using Ubuntu 11.04. 
Hence I am unable to burn the .iso to a CD, or even read a CD. 
 
I would like to install macpup to my harddrive using just a USB stick in an existing Ubuntu 11.04 installation. 
 
Does anybody know how to do this without using a live CD? 

 I would appreciate any help I could get on this. 
  
Thank you.

---

### Post by Timmer1240 on 2011-05-01
couldnt you just download and store the Iso on the Usb drive and set your bios to boot from the USB drive first anybody?

---

### Post by Timmer1240 on 2011-05-01
To do the hard drive installation MacPup needs to be able to see the files.
I had the same problem and did the following.
In my case, the iso was located on a hard drive partition but should be nearly the same from usb.

I extracted the iso files to the same location as the iso file (e.g. to the usb in your case).
In order to allow MacPup installer to see them, add the location to fstab.
I used blkid to get the UUID and added a line to fstab to make it show up in the file browser.
Leaving the file browser open, point the installer to the partition (or usb) extracted files.

This should work to install to hard drive ... did in my case.
If not, copy the files to a hard drive partition and point fstab to there.

That should do the trick.
If you have grub2 installed already, then do not install grub from MacPup installation.
Just update grub2 from wherever you initially installed grub2 from.
This will make MacPup accessible from your grub2 menu.

Hope this helps!

---

### Post by NormanFLinux on 2011-05-02
I have the same netbook. Get a USB stick from Walmart - 4 GB is around $15 - and download Unetbootin and burn your iso. to it. Turn on the netbook, hold down F9 and choose boot with USB. In the menu, choose safe graphics if offered.

Once you get to the desktop in live mode, run the installer program to install it to your hard drive. No one uses CDs anymore!

---

