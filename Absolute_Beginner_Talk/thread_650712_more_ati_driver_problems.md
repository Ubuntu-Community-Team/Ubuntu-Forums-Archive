---
title: "more ati driver problems"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by GreyWalker on 2007-12-26
i'm trying to find a way to install the drivers for an ati 9200 video card on a i686, 32bit system, running ubuntu/gutsy.i'm an absolute beginner and i've been have a ton of problems getting this to work none of the threads or howtos seem to answer my needs any advice would be helpful

---

### Post by spiderbatdad on 2007-12-26
heres a link showing youtube vids using your card. Apparently with xgl. [http://www.youtube.com/results?search_query=ubuntu+Ati+9200&search=Search](http://www.youtube.com/results?search_query=ubuntu+Ati+9200&search=Search)

---

### Post by OffAxis on 2007-12-26
You just need to enable the Restricted Driver.
Try this (I believe it's the same procedure for ati drivers).
[http://www.psychocats.net/ubuntu/nvidia]("http://www.psychocats.net/ubuntu/nvidia")

You may need to enable the 'Extra Repositories'.

There's also an installer on ati's website (ati.com) for the linux driver as well as an open source driver under development.

and here's an unofficial ati driver wiki that's helped me in the past
[http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")

---

### Post by GreyWalker on 2007-12-26
thanks for the link, so there's evidence its possible to get this card running but none of them actually showed how they did it.i haven't given up hope yet, i have a nvidia card but i don't think my power supply is higher enough it will only run for a little while before freezing up, as a last resort i'll upgrade but i can't really afford it nor do i really know how :-)

---

### Post by wormser on 2007-12-26
I have a different ATI card and installed it with Restricted Drivers.  It was easy.  System> Administration> Restricted Drivers.  Yours might be different but have a look there.

---

### Post by OffAxis on 2007-12-26
Absolutely it's possible; I've gotten a 9200 SE up and running before on 6.10.
I did it the hard way by downloading the driver from ati
[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html") running the install script, and modifying the xorg.conf file by hand.
The 'Restricted Drivers Manager' (which I never tried with this driver) is substantially easier; like night and day.
If it'll work, that should be your first stop. It's under **System Administration-->System Settings-->Display** or some such thing.

Edit: What he said (wormser).

---

### Post by xeth_delta on 2007-12-26
GreyWalker, you may want to check whether the ati proprietary drivers actually support 3D hardware acceleration for your video card, should you need it. From the model number you mentioned, I deduce it is not quite new.
An older laptop of mine has and ati mobility radeon 9000 IGP. The proprietary drivers don't provide 3D acceleration for it, but the open source ones included in X (radeon) work actually quite well.

Xeth

---

