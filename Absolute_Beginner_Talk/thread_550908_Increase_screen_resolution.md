---
title: "Increase screen resolution"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-09-14
Hi, I have a Dell Inspiron e1405 with a beautiful 14.1 1440x900 pixels resolution. I love Ubuntu, but I would like to increase my resolution to at least 1280 x1024. Strange thing is when I boot into puppy my resolution is 1440x900. I can't reconfigure my xorg.conf file because I have no idea which parameters my screen has. Can I copy my xorg.conf file from puppy and paste it into my Ubuntu? THX

---

### Post by John.Michael.Kane on 2007-09-14
> **mikecomua said:**
> Hi, I have a Dell Inspiron e1405 with a beautiful 14.1 1440x900 pixels resolution. I love Ubuntu, but I would like to increase my resolution to at least 1280 x1024. Strange thing is when I boot into puppy my resolution is 1440x900. I can't reconfigure my xorg.conf file because I have no idea which parameters my screen has. Can I copy my xorg.conf file from puppy and paste it into my Ubuntu? THX

You can not increase the resolution beyond 1440 x 900, As this is  the e1405 lcd maximum resolution, however. You can decrease the resolution if you want.


Resolution methods.adjust for the gpu your using.

[screen refresh rates....]("http://ubuntuforums.org/showthread.php?p=2605716#post2605716") 

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

Note: Make sure to have your lcd/crt manual, As you will need to refer to it for certain settings.

---

### Post by Orbital75 on 2007-09-14
Open you your Xorg.config and add 1280 x1024.
Scroll down the file until you start seeing Resolution Sizes.
On the last one put 1280 x1024 as the 1st size....
Save and then then Control Alt Backspace to Restart X.
check in your Gui Settings to see if 1280 x1024 is now available. 

Your all fixed.....   :KS

---

### Post by mikecomua on 2007-09-14
Where should I type my screen resolution?

---

### Post by Maestro23 on 2007-09-14
> **mikecomua said:**
> Where should I type my screen resolution?

Look for this section in **xorg.conf**:

> Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    #1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection


---

