---
title: "New install of Ubuntu (Running alongside Windows)"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Sexy_Penguin on 2007-07-25
Right, i'm definetly going to get Ubuntu, but, unfortunately, i'm a total noob.
Right then, first question:My Windows Install is on my C drive, my proposed Ubuntu install will be on my E drive, will I need to partition anything?
Second question:If I install Ubuntu to my E drive, can I back up windows data on the E drive?(If so, will it need to be partitioned to do so?)
Third question:Is there any free, recommended programs to do a partition?(If not, what are the recommended non-free ones?)
Thanks for any help recieved:KS

---

### Post by doomster on 2007-07-25
1st question : yes you will have to fromat and partition your E drive
2nd question: Backup all your valuable data before begining the installation
3rd question: the partitioner embeded inside linux installer is your best choice, and its free:)

Welcome to Ubuntu, and free software world:D

---

### Post by Blutack on 2007-07-25
No, yes, no!
1) Not if that is all you want, but see question two...
2) Windows cannot easily write to ext3, the Ubuntu file system.  You will need to split your E drive into 3 - a ~ 1gb linux-swap partition, a root ext3 partition for ubuntu itself and a fat32 or ntfs partition for backing up data
3) Your ubuntu live cd contains a program called gparted under system --> administration -- gparted
Don't forget to back up!

---

### Post by Blutack on 2007-07-25
Dammit!  Beat me!

---

### Post by Sexy_Penguin on 2007-07-25
Thanks for the help Blutack and doomster
Have some popcorn:popcorn::D

---

### Post by Blutack on 2007-07-25
Much appreciated, enjoy ubuntu!

---

### Post by Sexy_Penguin on 2007-07-25
Also, my E drive has 43gb worth of important data to me, where can I back this up?
(Both my other drives have less combined full free space with nothing on them, than the whole of my E drives used space:mad:)

---

### Post by Blutack on 2007-07-25
Erm...you need a usb drive?  Or a stack of dvd's and a lot of patience.  Or use one of your other drives.  Or install ubuntu on a flash stick...

---

### Post by Sexy_Penguin on 2007-07-25
> **Blutack said:**
> Erm...you need a usb drive?  Or a stack of dvd's and a lot of patience.  Or use one of your other drives.  Or install ubuntu on a flash stick...
Any free online backups?:confused:
*searches google*:KS

---

### Post by Blutack on 2007-07-25
43gb!?!  You either have a hell of an ISP or a hell of a lot of time on your hands :-)
Tried compressing it (7zip etc)?

---

### Post by Sexy_Penguin on 2007-07-25
> **Blutack said:**
> 43gb!?!  You either have a hell of an ISP or a hell of a lot of time on your hands :-)
Tried compressing it (7zip etc)?
Good idea that man!:popcorn:
:KS

---

### Post by Blutack on 2007-07-25
That man!?!
(well, ok, I am, but there are women hanging around the ubuntu forums...somewhere)
...OMG!  PONIES!
Get one of those big ol' usb externals (aria.co.uk/bigpockets.co.uk etc).  Fantastic things (even put ubuntu on em..)

---

### Post by Sexy_Penguin on 2007-07-26
> **Blutack said:**
> That man!?!
(well, ok, I am, but there are women hanging around the ubuntu forums...somewhere)
...OMG!  PONIES!
Get one of those big ol' usb externals (aria.co.uk/bigpockets.co.uk etc).  Fantastic things (even put ubuntu on em..)
I'm going to do what you first said(even though I didn't notice at the time)and create a partition for the parts I want to back up:guitar:

---

