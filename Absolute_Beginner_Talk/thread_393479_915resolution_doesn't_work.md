---
title: "915resolution doesn't work"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by pillu on 2007-03-25
Hi all,

I recently messed around with Beryl and as a consequence crashed my x window system. I reconfigured it using 
```
sudo dpkg-reconfigure xserver-xorg
```
and now I have a gui again. The problem is that I cannot increase my screen resolution to 1200x800 from the default 1024x768. I tried to use the 915resolution program and used the following guide
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Here is the output of 915resolution -l

[CODE]anand@zorg:/etc/init.d$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x800, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x800, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 24 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x800, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel [\CODE]

Could anyone help me with my screen resolution problem ?

thanks
pillu

---

### Post by Arby on 2007-03-26
I'm not sure I can help you specifically but I can show you what I have for a similar Intel graphics card (which is currently working at 1200x800) and see if you can modify it to suit.

sudo 915resolution -l returns the following ```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel

```

What do you have in the file /etc/defaults/915resolution? I have this. ```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1200
YRESO=800
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=24

```

Maybe you can spot a setting you need to change. I had a similar problem, I eventually fixed it but I was never quite sure how unfortunately. I tried lots of things, I'm not really sure which one works. I'll also attach my xorg.conf file for you. Check the Device and Screen sections to make sure you have 1200x800 set as one of the available modes. I'm currently using beryl on feisty so there are a few extras in there that you don't need to worry about. If you're confused just ask. If all else fails post /etc/default/915resolution and /etc/X11/xorg.conf here and let people take a look. Xorg can be a strange beast in my (limited) experience.

Arby

---

### Post by pillu on 2007-03-26
Hi,

I modified my /etc/default/915resolution to look just like yours. It still doesn't help. I think the problem is with xorg.conf. I am posting the section which I think is relevant below
```
ection "Screen"
        Identifier      "Default Screen"
        Device          "Intel i945"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


```
As you can see, there is no 1200x800 mode available. I will try to manually edit the file if you can post your xorg.conf. Hopefully changing that will make some difference.
Thanks

---

### Post by pillu on 2007-03-26
I added 1200x800 to all the relevant lines in xorg.conf. Then I used 915resolution again to set the mode to 1200x800 and restarted x. I think it has worked this time. How do I tell ? The change is perceptible to the eye but my monitor resolution shows current resolution to be 640x480 (which is obviously false) and it still only goes upto 1024x768. I there any way to tell for sure what my resolution is ?

Thanks

---

### Post by macogw on 2007-03-26
It sounds like you did everything right, but if it's not working now, well, I can tell you that in April if you redo it, it'll work because Feisty sort of automates it when you install it.  Don't take this as a reason to switch to Feisty right now though.  It's not ready for anyone who would have trouble living in a world without X.

---

### Post by pillu on 2007-03-26
> **macogw said:**
> It sounds like you did everything right, but if it's not working now, well, I can tell you that in April if you redo it, it'll work because Feisty sort of automates it when you install it.  Don't take this as a reason to switch to Feisty right now though.  It's not ready for anyone who would have trouble living in a world without X.

Oh...I don't have trouble without X. I think I can get along fine except for browsing the web and posting on this forum :). But I do think it has worked this time. How the hell do I tell ? Looking forward to fiesty though. Is Beryl going to be included in it ?

cheers

---

### Post by Arby on 2007-03-27
If it looks like 1200x800 by eye then it's probably right. I use KDE so I'm not familiar with the GUI versions of setting resolutions in Gnome. Wherever that tool is in gnome it should show the correct resolution. As you say if it really was 640x480 you'd know. It sounds as if the resolution is being reported wrongly but I have no idea why that would be.

---

### Post by pillu on 2007-03-27
> **Arby said:**
> If it looks like 1200x800 by eye then it's probably right. I use KDE so I'm not familiar with the GUI versions of setting resolutions in Gnome. Wherever that tool is in gnome it should show the correct resolution. As you say if it really was 640x480 you'd know. It sounds as if the resolution is being reported wrongly but I have no idea why that would be.

I think I got the correct resolution the last time. You can tell the difference when you open web pages. But after a restart things have gone back to the square one. X is behaving in a very funny way. I guess I will hunt around more till I come up with a solution or just wait for feisty.

---

### Post by pillu on 2007-03-27
hi all,

after endless tinkering around with my xorg.conf, I have resolved the issue with the screen resolution and reinstalled beryl successfully. Thanks for your help

pillu
:guitar:

---

### Post by macogw on 2007-03-28
the resolution script has to run on every boot, thats why it disappeared after rebooting

compiz will be installed and disabled by default.  beryl is in the repos.

---

