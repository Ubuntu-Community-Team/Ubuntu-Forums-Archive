---
title: "I get 800x600 resolution. It's the highest setting in options."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by foolios on 2007-10-25
How can I change this. I went to envy's site and dl a file then used it. Nothing changed. 
I still can't go any higher. In windows this monitor supports 1040 res.

Thanks in advance for any info

---

### Post by overdrank on 2007-10-25
> **foolios said:**
> How can I change this. I went to envy's site and dl a file then used it. Nothing changed. 
I still can't go any higher. In windows this monitor supports 1040 res.

Thanks in advance for any info

Hi and this link may help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Also which version of ubuntu are your using, 7.10 Gutsy, Feisty 7.04? 
You could post the output of this command in the terminal
```
cat /etc/X11/xorg.conf

```
And we maybe able to help. :)

---

### Post by khughitt on 2007-10-25
Heya,

Go to **System** -> **Administration** -> **Screens and Graphics**.
What is listed there under the screen tab, and under the Graphics card tab? (Which drivers are being used?)

Also, what kind of graphics card do you have?

---

### Post by jdfreshwater on 2007-10-25
You can always try the following command.
> sudo dpkg-reconfigure xserver-xorg
This command will take you through a console based Xorg settup and allow you to select resolutions.

---

### Post by snickers295 on 2007-10-25
I also get this problem when enabling the Nivdia Acceleration Driver.
if i turn this driver off it will work fine and i can get my 1280x1024.
i think it has something to do with compiz enabled by default because it uses the driver.
and the above command does not help either.

---

### Post by slibuntu on 2007-10-25
If you're using an integrated intel graphics card, [this]("http://slibuntu.wordpress.com/2007/03/13/using-915resolution-to-change-resolution/") tutorial on my blog might help, its worked flawlessly on the laptops I've tried it on.

---

### Post by snickers295 on 2007-10-25
i use a nivdia card.

---

### Post by foolios on 2007-11-09
I dl'd a new version of Ubuntu and it's set at a higher resolution automatically this time.

Section "Device"
        Identifier      "ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL E772p"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
        Monitor         "DELL E772p"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Thanks all.

---

