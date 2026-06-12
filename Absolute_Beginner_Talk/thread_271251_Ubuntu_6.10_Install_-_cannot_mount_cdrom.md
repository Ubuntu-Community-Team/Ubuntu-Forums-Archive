---
title: "Ubuntu 6.10 Install - cannot mount cdrom"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by twood_us on 2006-10-04
This is a i386 - stand alone Ubuntu 6.10 Server install.

I ran:  **sudu apt-get install ubuntu-desktop**

It ran great until it asked me to insert the disk labeled:

**Ubuntu-Server 6.10 _Edgy Eft_ - Beta i386 (20060927.3)** 

I inserted the media, but the server doesn't recognize the CD as the above listed media.  The disk label on the CD is "Ubuntu 6.10".  

Can anyone help me get this CDROM properly mounted? 

Tim

---

### Post by jorn on 2006-10-04
To see if the cd-drive is mounted at startup you might aste into terminal:
> sudo vi /etc/fstab
Maybe you need the Ubuntu-Server 6.10 _Edgy Eft_ - Beta i386 (20060927.3)?

---

### Post by twood_us on 2006-10-04
Thanks for the advice.   Didn't work out. 

I re-formatted the drive and installed v6.06

That worked just fine and the cdrom mounts properly. 

Thanks anyway.](*,)

---

