---
title: "gsynaptics and xorg.conf"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by kristiansuhl on 2007-03-01
Hi everyone! I got some good help in fixing alot of problems in this forum, so I got another good question for you! ;-)

I succeeded with your help in installing Gsynaptics and some other things - but when I try to start the gsynaptics "touchpad" in preferenses menu - it does not work and I get this message:

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

Should I really try to change in this file? - last time I tried changing something there - I ended up without graphical enviroment! ;-)

---

### Post by Carlos Santiago on 2007-03-01
Yes you must do it. 
To edit it, type: 
sudo gedit /etc/X11/xorg.conf

then just add 
Option 'SHMConfig' 'true' 
inside the section synaptics. 

If you want to install qsynaptics only to switch off tapping click, i must tell you that you dont need to.

Just add 
Option          "MaxTapTime"            "0"
inside the synaptics section

---

### Post by Brent099 on 2007-03-05
I'm having the same or similar problem with Ksynaptics.  After editing /etc/X11/xorg.conf as described it still gives the error message:
"Shared Memory is not accessible.
Please add the option 'SHMConfig ''on''' into the touch pad section of /etc/X11/xorg.conf"

the kontrol module still loads, but everything is greyed out and under the information section it reads:
"using libsynaptics version: 0.14.6a"
"Using driver version: none"
So this is making me think that I've not installed it correctly/completely.  (installed through Adept Manager)

Any help point be greatly appreciated.

---

### Post by xenblend on 2007-04-01
I am having the same problem with qsynaptics and ksynaptics.  I have already added 'Option "SHMConfig" "on"' to my xorg.conf.  Someone help!  Is there anything else that I must add to xorg.conf?

xb

---

### Post by groggyboy on 2007-04-01
i don't know what to suggest.  gsynaptics works fine for me.  k/q/gsynaptics should work if you have your xorg set up properly (keep in mind you have to restart X whenever you tweak your xorg.conf file).  xenblend, you could try running k/qsynaptics from the terminal - that might give you an idea of what's going wrong.  here's what the relevant part of my xorg looks like:```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection

```

---

### Post by xenblend on 2007-04-01
I figured out the problem with my setup from another post.  I was using the 'mouse' driver instead of the 'synaptics' driver for xserver-xorg.  Now qsynaptics works fine! =)

EXAMPLE (as seen above):
Section "InputDevice"
   Identifier "My Touchpad"
   Driver "synaptics"
   ...
   Option "SHMConfig" "true"
EndSection

---

### Post by jackmc on 2007-04-14
I dont have the synaptics section in xorg. can I just add it (with the modification for gsynaptics) or do I somehow have to install the touchpad. It works fine, but is overly sensative.

---

### Post by jenikone on 2007-05-27
Hi all,

Thank you for your help here, I needed it too.
I just want to emphasize that

you probably should insert the new line ("SHMConf...")
AT THE END of the Synaptic section, and maybe use double quotes,

because I did not do this and my GUI did not start then :-)

Hope it helps,

Bye :-)

---

### Post by SophianicIrony on 2007-07-03
I don't have a synaptics section after Gsynaptics is installed, any help?

---

