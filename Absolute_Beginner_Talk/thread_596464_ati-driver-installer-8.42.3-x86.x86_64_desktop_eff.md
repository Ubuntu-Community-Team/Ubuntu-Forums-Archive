---
title: "ati-driver-installer-8.42.3-x86.x86_64 desktop effects not working?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-10-29
I just installed the new driver, but now it says Desktop effects could not be enabled when i turn them on?

Does anybody know how i can fix this? i thought the new drivers should support them ?

chris@chris-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.0.6958 Release

---

### Post by mech7 on 2007-10-31
bump

---

### Post by ConfidentiaL on 2007-10-31
I think our card is blacklisted or something. 
Try installing the package xserver-xgl.
Then do a xserver restart and try to enable the effect again.

---

### Post by Regel on 2007-10-31
I can't turn them on either. This driver should support AIGLX, but you might want to wait a bit before using fglrx with aiglx, it seems to be a bit bugged.

---

### Post by mech7 on 2007-10-31
> **Regel said:**
> I can't turn them on either. This driver should support AIGLX, but you might want to wait a bit before using fglrx with aiglx, it seems to be a bit bugged.


aarrrr waited so long for this :(

---

### Post by mech7 on 2007-11-05
How should i uninstall these so i can atleast get the desktop effects back again under XGL ?

---

### Post by carlosjuero on 2007-11-05
The ATI X700 is listed in the Blacklist of the Compiz install

[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

To uninstall the new ATI driver you will have to run the ATI uninstall script:
```

Automatic or Custom Driver Installations

If the ATI Proprietary Linux Driver was installed using either the Automatic or Custom options, then do the following:

   1. Launch the Terminal Application/Window and navigate to the /usr/share/fglrx folder.
   2. With super user permissions, enter the command "sh./fglrx-uninstall

``` (From ATI's website)

You will then have to reconfigure X to use a different display driver
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by mech7 on 2007-11-06
Can i just ignore it ? the blacklist is it safe? also i now installed XGL again but it is superslow :(

---

### Post by ConfidentiaL on 2007-11-09
I had to use the 8.39.4 driver, and with xgl it  works quite smooth. Then again, the 8.42.3 driver doesn't work at all for me.

---

### Post by wadageek on 2007-11-09
Mech7
you need to whitelist the FGLRX driver

refer to the link
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) and scroll down to the bottom

sudo gedit /usr/bin/compiz and fglrx to 
# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

Hope that helps

---

### Post by Da King on 2007-11-09
am using the Intel 82815...Can i also use this config..or is there anywhere i can get the config help

---

### Post by twizler on 2007-11-09
> 
SKIP_CHECKS=yes compiz

TRY THAT in the command line term
I have a dell at HOME == did 8.42 the ati UPDATE -- not problem 
... Dell at work -- GX745 x1300 ATI HELL __~!ERRRRRRRR

ATI 8.42 works .. But jacked up... only way to get it to go is

---

