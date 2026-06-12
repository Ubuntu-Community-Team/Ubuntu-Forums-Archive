---
title: "Some Questions"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by adewale on 2007-03-14
i have a 40 gb hard disk with windows on it , and about 13gb for my data then an excess 9 gb for nothing when i installed linux it resized my windows partition only and  not making use of my exess 9gb. So i feel my system is a bit slow,could it be because i have like 312 of swap space. 
Also i installed nvidia driver a video card some gave me geforce mx/mx 400 the installation went well but after i login or even before i login the pc freezes could it be my swap
thanks

---

### Post by hyper_ch on 2007-03-14
(1) Ram:
No, that should not affect you I think... you used that swap amount before you resized so resizing shouldn't have any impact...

(2) nVidia:
I guess you'll have to use the legacy drivers for nVidia... Geforce Mx/Mx 400 is quite old, isn't it?

---

### Post by adewale on 2007-03-14
so how do i get the legacy driver can u give me the url thanks

---

### Post by orkim on 2007-03-14
I believe it is part of Xorg by default.  If I remember correctly it is called "nv" and it should take care of MX400 series devices.

-orkim

---

### Post by adewale on 2007-03-14
so what should i do now and how do i edit Xorg

---

### Post by orkim on 2007-03-14
"sudo vi /etc/X11/xorg.conf"  or similar will edit the file.

However, I fear that if you are asking this question you probably won't be able to make sense of that file.  It's a little more complicated than I can go into.  You may want to look for some X11/Xorg tutorials to figure out how it works.  I think "man xorg.conf" is also there which may provide some information.

This one is going to require some footwork on your part.

-orkim

---

### Post by adewale on 2007-03-14
ok i'll try that merci beaucoup

---

### Post by hyper_ch on 2007-03-14
Here's what I did:

```

sudo apt-get install nvidia-glx-legacy

```

Then make a backup of your existing xorg.conf
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Then I did run the xserver config again
```

sudo dpkg-reconfigure xserver-xorg

```

It will ask some questions, just fill the stuff as asked... (don't worry, we have made a backup first)

Once that is finished I kind of merged the two configs... the problem was reconfiguring didn't recognize my graphic card and monitor that well....

So in one terminal I opened the xorg.conf as root
```

sudo nano xorg.conf

```
or you can use instead of *nano* another editor...
In a second terminal I opened the backup file (not as root)
```

nano /etc/X11/xorg.conf.backup

```

I copied now various stuff from the backup to the new one.

--> In the section modules I enabled glx:
        Load    "glx"

--> In the section device I copied my graphic card to the new one and changed Driver to nvidia (if it wasn't already)
        Identifier      "nVidia Corporation NV15 [GeForce2 GTS/Pro]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"

--> Once you verify it works fine and you want to get rid of that nvidia logo upon boot you can add to the device section this option here below (just add it below the BusID):
        Option          "NoLogo"

--> Then I copied from my original xorg.conf the monitor section:
        Identifier      "Acer AL1951"
        Option          "DPMS"
        HorizSync       30-100
        VertRefresh     50-160

--> In the section Screen I also copied over my original three entries
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV15 [GeForce2 GTS/Pro]"
        Monitor         "Acer AL1951"

--> As the legacy driver can't use composite I had to turn it off... at the end of the xorg.conf add this here:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection


Once done restart GDM (or KDM or just simply reboot) and you should see the nVidia logo just before the graphical login appears... (that's test 1)
And once you are logged in, open a terminal and enter
```

glxgears

```
If that works also then the your card runs fine...

This applies to Edgy/Feisty and to legacy drivers. See the list [here]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html")

Basically I followed this tutorial [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") but I had to tweak it a bit

---

