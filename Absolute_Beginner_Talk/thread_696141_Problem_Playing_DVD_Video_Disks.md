---
title: "Problem Playing DVD Video Disks"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-02-13
I want to be able to play legally purchased DVDs on my computer. When I pop the disk in though, and try to play the disk using Totem or VLC, nothing happens.

I haven't installed any extra packages on Ubuntu 7.10 Gusty Gibbon, but I do have the Ubuntu Restricted extras package. I thought this should cover me, but I can't play DVDs.

Can someone help?

---

### Post by Blutack on 2008-02-13
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+b1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+b1_i386.deb)
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+b1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+b1_amd64.deb)
pick the one that suits your install type -  if you don't know it's probably i386.

---

### Post by Jimmey on 2008-02-13
You need to install a separate package. See** [this link]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")**

---

### Post by Presto123 on 2008-02-13
Yeah, it will not do everything you need. Go to: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Update your sources list as determined by your version and when it reloads, install libdvdcss from the Synaptic Package Manager.

*LOL. I keep getting beat to the punch here. To the best of my knowledge, you really only need one of the library packages to run DVD's and that will be the one listed above."

---

### Post by Crumpets and Jam on 2008-02-14
Thankyou.

---

### Post by pedro_orange on 2008-02-14
```
sudo apt-get install ubuntu-restricted-extras
```

That will install DVD/mp3/mpeg codecs etc, Java virtual machine, Flash player......why choose anything else? :)

---

