---
title: "Screen Refresh Rate"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by MatthiasMatthias on 2006-06-02
Hello friends:

I am running Ubuntu 6.06 LTS - the Dapper Drake :) 

I would like to increase my screen refresh rate, but I don't have any other options other than 60 Hz.  :( 

I have three screen resolutions to choose from also:  1024 x 768
                                                                                       800 x 600
                                                                                       640 x 480

I have an 256mb NVIDIA GEFORCE 5200 video card 

My monitor is definately not the problem. 

I don't know ANYTHING about Linux, but I've been trying to familarize myself with the menus etc.  :p 

What's sad is I could help anyone else with anything windows based (it's not taboo to talk about windows here is it?), but I can't help myself at all here.  :???: 

You're help would be greatly appreciated.

---

### Post by blackjack6.21.91 on 2006-06-02
add
VertRefresh 60
In the /etc/X11/xorg.conf under Monitor

Umm i looked that up on google b/c you had no replies.  I don't know what that's talking about but maybe it'll help you?

---

### Post by BobSongs on 2006-06-02
First: no, it's not taboo to speak of Windows. Ubuntu means human kindness, it doesn't mean fanatic obsession with an operating system. ;)

Second: search the threads to see if your video card drivers are up-to-date; make sure you get any updating tips from threads geared towards Dapper Drake.

Third: you may have to mess with a file called **xorg.conf**. But before you do remember to **[COLOR="Red"]proceed with caution[/COLOR]**. Back up the file before you touch it```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Feel free to rename the copied file as you wish. Some people prefer a date attached to the file like 'xorg.conf.200606021655' (meaning 2006/06/02 16:55). [COLOR="Red"]**Messing with this file is a last resort for a new user.**[/COLOR] You'll need to review your monitor's manual and key in critical information.

I won't build an entire tutorial on how to do it here because there are folks who've already done so. You'll need to read through some of the threads for that.

Fourth: Don't panic. Some one else has already gone through this.

**Edit**: Upon re-reading your thread I noticed that you've got 1024 x 768. I assume this is the size you're going to use. Okay, head over to your **monitor's** website (i.e., HP, IBM, Compaq, etc.) and look for the technical manual. It's usually in a **.pdf** form.

Okay download it and look for the horizontal and vertical sync figures. They should be represented by something like 69-150 and 32-175... that sort of range.

Now back up your xorg.conf file and then open it in an editor.

Look for the horizontal/vertical entries in the file. Replace the "default" ones with the numbers allowed by the manufacturer's specs.

Save the file and restart your PC.

Suddenly you'll have all your allowed refresh rates at 1024 x 768.

---

### Post by tseliot on 2006-06-02
Install Nvidia's proprietary driver:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by kamil212 on 2006-06-13
Where do I change the settings? I don't see anything that has to do with refresh rate.
I'm stuck at 85

Section "Monitor"
    Identifier     "NEC FE950+"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV35 [GeForce FX 5900XT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV35 [GeForce FX 5900XT]"
    Monitor        "NEC FE950+"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by u.b.u.n.t.u on 2006-06-13
I have Nvidia, 6600GT, and I can change the screen resolution but the refresh rate is locked. I have the Nvidia drivers installed. They are buggy.

---

### Post by kamil212 on 2006-06-13
My screen i shaking
It wasn't in the liveCD mode, I was able to change it to 60 in live CD mode???

---

### Post by u.b.u.n.t.u on 2006-06-13
[QUOTE=kamil212]My screen i shaking
It wasn't in the liveCD mode, I was able to change it to 60 in live CD mode???[/QUOTE]

It seems you have the 3D Nvidia drivers installed? Same here. That is what I think is the problem - just a guess.

---

