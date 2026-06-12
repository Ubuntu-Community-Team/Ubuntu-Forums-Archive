---
title: "Ubuntu 9.04 login resolution is too big in Parallels 4"
date: 2009-05-11
forum: Apple Hardware Users
---

### Post by Coldhearth on 2009-05-11
Hi,

I'm running Ubuntu 9.04 under parallels 4 on my intel iMac.
I have a screen with 1680x1050 as resolution and I have changed the video settings of my parallels machine to about 11mb to support this resolution.

Now once logged in the resolution of my screen is supperb just like it should be. But on the login screen itself it is waay to big for my screen zo I get scrollbars in my parallels window.

Does anybody know how this comes and how I could get this fixed?

Thx,
Coldhearth

---

### Post by m00se3724 on 2009-05-12
I am having the exact same problem with Ubuntu 9.04 running in Parallels 4 on my Macbook Pro.  Most suggested solutions I have read have been to edit the xorg file, looking for sections that look like the following:

SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection

and changing the resolutions accordingly, but mine does not look like that under the display section. I still have not figured it out. After entering nano /etc/X11/xorg.conf, here is a portion of my xorg:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by cyberdork33 on 2009-05-12
you need to check out changing the resolution of gdm not xorg.

---

### Post by onno-itmaze on 2009-05-13
Without digging, sounds like your video resolution wasn't detected properly by the Ubuntu installation.

Did you change the resolution before or after you installed Ubuntu?

This will redo the process:
  sudo dpkg-reconfigure xserver-xorg

---

### Post by m00se3724 on 2009-05-13
The only thing I did before installing Ubuntu was increase the amount of video memory parallels defaults to in order to allow 1400x900 resolution for my macbook pro.  I will look into changing the resolution of gdm as cyberdork suggested.

---

### Post by m00se3724 on 2009-05-13
So I looked around and it seems that all recommendations for changing GDM resolution involve editing xorg, which in my case does not look like what other people's xorg files look like. I'm assuming this is probably related to parallels, I don't have any resolutions listed in my xorg, just "configured devices".  I'm still lost, all I want is my login screen to be the same resolution as my desktop.

---

### Post by cyberdork33 on 2009-05-13
> **sanduskm said:**
> So I looked around and it seems that all recommendations for changing GDM resolution involve editing xorg, which in my case does not look like what other people's xorg files look like. I'm assuming this is probably related to parallels, I don't have any resolutions listed in my xorg, just "configured devices".  I'm still lost, all I want is my login screen to be the same resolution as my desktop.
the problem is that gdm just detects the best resolution that your display can show, and uses that. Since you are running it in a window on that display, your window is actually smaller that the display's resolution. I had found awhile back how to change this, but I cannot find my links anymore. I will look around a little.

I couldn't find anything, and I have to go to other duties now.

you can enable autologin to bypass the screen altogether in System > Administration > Login Window

---

### Post by MarkX on 2009-05-13
The problem is that UBUNTU has always been USELESS with screen resolutions and 9.04 is even worse.
I wish the brains would sort out the most basic things before playing with things like "cloud computing". 

I have wasted most of the day just trying to set the resolution and not succeeded.
It needs a GUI to do it manually when the screen resolution is (usually, in my case) wrongly detected.
I suppose I'll try unplugging the NVIDIA mx440 and just using the mobo vid next.

---

### Post by cyberdork33 on 2009-05-13
there is a GUI. it is in the System Menu.

---

### Post by onno-itmaze on 2009-05-13
> **sanduskm said:**
> So I looked around and it seems that all recommendations for changing GDM resolution involve editing xorg, which in my case does not look like what other people's xorg files look like. I'm assuming this is probably related to parallels, I don't have any resolutions listed in my xorg, just "configured devices".  I'm still lost, all I want is my login screen to be the same resolution as my desktop.

Yes, I too looked around before I posted, which is why I suggested to do this:

```
sudo dpkg-reconfigure xserver-xorg
```

That should automatically create a copy of xorg.conf and redo the detection for you. No manual editing involved.

---

### Post by m00se3724 on 2009-05-14
> **onno-itmaze said:**
> Yes, I too looked around before I posted, which is why I suggested to do this:

```
sudo dpkg-reconfigure xserver-xorg
```

That should automatically create a copy of xorg.conf and redo the detection for you. No manual editing involved.

I have done that in the past and I don't think it did anything. I believe parallels is the culprit. I have not changed my xorg file at all since I installed Ubuntu. It isn't a huge deal that the resolution is off, I can still see the input bar on the login screen, just not the graphic in the lower right, however it would be nice to fix it.

---

### Post by m00se3724 on 2009-05-19
> **Coldhearth said:**
> Hi,

I'm running Ubuntu 9.04 under parallels 4 on my intel iMac.
I have a screen with 1680x1050 as resolution and I have changed the video settings of my parallels machine to about 11mb to support this resolution.

Now once logged in the resolution of my screen is supperb just like it should be. But on the login screen itself it is waay to big for my screen zo I get scrollbars in my parallels window.

Does anybody know how this comes and how I could get this fixed?

Thx,
Coldhearth

Coldhearth, I fixed the problem by adding the following SubSection to my xorg file under the "Screen" section:

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Device"
        SubSection   "Display"
             Depth 24
             Modes "1440x900"
        EndSubSection
EndSection


I have messed around with my xorg file in this manner before but never succeeded in changing the gdm resolution until now. Not sure why it finally worked.

---

### Post by mbaitoff on 2009-12-31
> I have messed around with my xorg file in this manner before but never succeeded in changing the gdm resolution until now. Not sure why it finally worked.

I experimented with Ubuntu within a VirtualBox. Setting up the correct resolution is painfull there. But I think I managed to cope both with login screen and desktop.

The crucial line in xorg.conf seems to be the "Modes" line under "Display" subsection of the "Screen" section. It looks like:
> Modes "1440x900" "1024x768" "800x600" "640x480"
I figured out that login screen always uses the first mode specification from this line, in this case - "1440x900". Desktop uses the mode that you've specified in "Screen resolution" or "Display" applet. So, if you want your login screen to be the same resolution as your desktop is, specify that resolution first in the "Modes" line.

---

