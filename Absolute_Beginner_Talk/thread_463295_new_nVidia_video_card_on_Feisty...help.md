---
title: "new nVidia video card on Feisty...help"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-06-03
Changing from using integrated video on the motherboard to a new video card.  I have ordered a nVidia  CHAINTECH LA-FX20-H GeForce FX5200 video card for my PC and need help on how to get the drivers installed.  I am using the lousy Unichrome video integrated on my motherboard which I hate.  I'm using Feisty and don't know if I have to do something prior to instaling the new card or if I just install it and then I will instructed to install the new drivers at boot up???  What is the correct Ubuntu way to update your video card on an existing system?????.............HELP

---

### Post by jhenager on 2007-06-03
Don't worry - it's easy as can be.
Install the card and boot up.
You won't be prompted, but the easiest way is to use Add/Remove and search on nvidia.
Check the box labeled 'NVidia binary X.Org driver, and you're done.

---

### Post by rggavubt on 2007-06-03
Thanks for the reply.  I was worrying that I would get the black screen of death and it would not boot up!

---

### Post by rggavubt on 2007-06-06
> **jhenager said:**
> Don't worry - it's easy as can be.
Install the card and boot up.
You won't be prompted, but the easiest way is to use Add/Remove and search on nvidia.
Check the box labeled 'NVidia binary X.Org driver, and you're done.

It wasn't that easy.  The system would not boot up with the new video card.  Don't I have to uninstall the drivers I have now?  I am using Openchrome drivers with my integrated UniChrome Pro Graphics video on Fiesty.  I tried to leave the new video card in and reconnect the VGA plug to the motherboard video but that didn't work.  I had to remove the new video card and then connect to the old video and I was able to boot up.  Any help would be appreciated???

---

### Post by rggavubt on 2007-06-08
In reference to trying to load drivers for FX 5200 video card.  I reinstalled 7.04 and now I get a black screen and can't boot up.  The only way I can boot up now is to use the CD and the safe graphics mode.  I loaded the nVidia binary Xorg drivers and enabled them in the restircted drivers manager but I still get the black screen.  When I edit files when I boot up on the CD, am I editing my files on my PC harddrive or am I editing the files on the boot up CD?? How do I edit my xorg.conf when I can't boot up on the harddrive?
I got to the terminal but "sud nvidia-settings'' or "gksudo gedit /etc/x11/xorg.conf" don't work????

---

### Post by pnix on 2007-06-08
> **rggavubt said:**
>  When I edit files when I boot up on the CD, am I editing my files on my PC harddrive or am I editing the files on the boot up CD?? How do I edit my xorg.conf when I can't boot up on the harddrive?
I got to the terminal but "sud nvidia-settings'' or "gksudo gedit /etc/x11/xorg.conf" don't work????

To edit file[on harddrive] when boot from liveCD? you need to mount drive first.

but i think , boot in recovery mode, try "sudo nano /etc/X11/xorg.conf".

---

### Post by rggavubt on 2007-06-08
I mounted the drive but the xorg.conf was read only.  I finally was able to load and boot by doing  as follows....for people who are having the same problem :

I tried to boot up on the hard drive and got the black screen
I hit ctrl, alt and F1 to go to the terminal
I then entered "sudo aptitude update" without the quotations(have to enter password)
I then entered "sudo aptitude install nvidia-glx" without the quotations(have to enter password)
After those ran, I then entered sudo nvidia-xconfig

I was reading all the posts and saw this listed somewhere.  After that I was able to boot up from the hard drive and the screen looks great!!:popcorn:

---

