---
title: "915resolution problems !!!"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by xs0me0nex on 2006-09-28
Hey guys,
I have been reading the many posts about 915resolution but I can not get it to work. I installed 915resolution and edited it so it looks like this:

Mode=auto

XRESO=1280
YRESO=800

BIT=

Is that correct?
My xorg.conf looks like this:

Section "Screen"
      Indentifier        "Default Screen"
      Device             "Intel Corporation Mobile Integrated
                          Graphics Controller"
      Monitor            "Generic Monitor"
      DefaultDepths      24
      SubSection "Display"  
               Depth          1
               Modes          "1280x800"
      SubSection "Display"  
               Depth          4
               Modes          "1280x800" 
      SubSection "Display"  
               Depth          8
               Modes          "1280x800" 
      SubSection "Display"  
               Depth          15
               Modes          "1280x800" 
      SubSection "Display"  
               Depth          16
               Modes          "1280x800" 
      SubSection "Display"  
               Depth          24
               Modes          "1280x800"
      EndSubsection
EndSection

I don't know what to do and help would be greatly appreciated :) 

Thanks
s0me0ne

---

### Post by Arthur Archnix on 2007-09-28
Try this:
```
sudo apt-get remove 915resolution
sudo apt-get install xserver-xorg-video-intel
```
Then restart X with Ctrl+ALT+Backspace

If that doesn't work, check your xorg.conf to make sure the driver is "intel" not "i810".

Lastly, reverse the suggestions and post the make and model of your video card. Also, have you backed up your xorg before making changes? If so, restore that, post the relevant sections and let us know what you're trying to do. Enable a different resolution I would assume, but there can be many ways to do this.

---

