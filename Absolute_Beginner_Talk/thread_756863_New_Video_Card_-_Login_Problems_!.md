---
title: "New Video Card - Login Problems !"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by drsox1899 on 2008-04-16
I added a nVidia 7300SE PCIE card to my working Ubuntu 7.1 installation and switched to that from the onboard video.  

Login refused to work in any mode other than safe mode.  It loaded a full screen Terminal window and left me with the <user>@<host>:~$ login.  I even disabled the Proprietary Driver that I had needed to run the onboard video.  No effect.

Since I didn't know what else to do I reinstalled from the live CD (the new card worked OK in the live CD).  Now the card is working OK.

What would have been the smart thing to do when presented with the <user>@<host>:~$ login ?

---

### Post by Inxsible on 2008-04-16
You should have simply done a ```
sudo dpkg-reconfigure -pHigh xserver-xorg
```That would have reset your video card to a generic driver. After logging in, you could have enabled your drivers for the new NVidia card.

---

### Post by drsox1899 on 2008-04-16
Thanks.

What else does that reset ?  Is it a general purpose "GetOutOfJail" command ?

---

