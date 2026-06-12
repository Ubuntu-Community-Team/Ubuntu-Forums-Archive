---
title: "Lost My Ubuntu"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by eppoh on 2006-12-20
Decided to give a try to PCLinux OS. Figured I had room on my second drive for it. It installed LILO but I could not find the ubuntu boot partition when I set it up. Tried also to use GRUB, with the same results. 

It keeps asking me for the partition and the name of the "image" to boot. 

Sure would like to find it so I can run either and compare.

---

### Post by Dusty545 on 2006-12-20
If you boot from the Ubuntu Live CD, open a terminal and enter the following (if you're still using GRUB):

'sudo grub'

'find /boot/grub/stage1'

It will tell you where your boot image is in a manner like '(hd0,2)'

type:  'root (hdx,y)' using the answer from the output on the previous line.

type 'setup (hd0)'

type 'quit'

When you reboot your computer it will put up your previously installed boot setup.  

Just a point of note, if you have two distros installed, it will give you two answers on the 'find /boot/grub/stage 1'.  Just pick the right one.  If you don't then repeat the procedure and choose the other partition.

:)

---

### Post by eppoh on 2006-12-20
> **Dusty545 said:**
> If you boot from the Ubuntu Live CD, open a terminal and enter the following (if you're still using GRUB):

'sudo grub'

'find /boot/grub/stage1'

It will tell you where your boot image is in a manner like '(hd0,2)'

type:  'root (hdx,y)' using the answer from the output on the previous line.

type 'setup (hd0)'

type 'quit'

When you reboot your computer it will put up your previously installed boot setup.  

Just a point of note, if you have two distros installed, it will give you two answers on the 'find /boot/grub/stage 1'.  Just pick the right one.  If you don't then repeat the procedure and choose the other partition.

:)

thanks tried it and it returned (hd1,0)
I setup hd0 and it when I rebooted it took me to the Grub with only the PCLinux and Windows, etcccc., but no Ubuntu image.

Tried to root  hd1 and it said "file system type unknown, usiing entire disk
then I setup hd1 and it returned Cannot mount selected partition.

Maybe I buggered the Ubuntu root partition when I loaded PCLOS

Any other way to find the Ubuntu?

---

### Post by Dusty545 on 2006-12-20
Another possibility is if you can go into '/boot/grub/' on the Ubuntu partition and look for a file called 'menu.lst'.  If you have a look at that then you should find the entries for what images to look for to boot.

The problem is, if you are using anything other than the original images or if you don't know the right details for your partition setup then things are not too bright.

I'm a relative noob but I've been trying distros like mad recently and can't find anything to match Ubuntu so I've gotten very used to repairing my grub entries.  Another option that I came across in the past was to use the Live CD to repair grub.  Have a look here:

[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by eppoh on 2006-12-20
That link was dead.
I am really liking PCLOS. and the guy behind it was a real asset to the Mandrake community when I was using Mandrake. I think it is faster than Ubuntu and easier to set up out of the box. I may just stick with it.

Thanks

---

