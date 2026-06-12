---
title: "Some configurations"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-05-30
hi, how can i enable a confirmation message on deleting files? the option is selected in the file manager but it works only with <shift + delete> but with delete directly trash without confirmation.

another thing here that can i disable my laptop touch pad from ubuntu?? cuz the laptop bios there is no option to do so.

---

### Post by dannyboy79 on 2007-05-30
i thought there was a setting for this within the file manager preferences dialog box somewhere. or it might be within the system, preferences, blah blah pick. I am not at home so I can't help you look but I know it's possible. 

As far as inactivating your touchpad, it hsould be set within your /etc/X11/xorg.conf file, under the inputs section. This is what my touchpad settings look like within that file for my laptop

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Just put a # symbol at the beginning of each line, and then do a restart and it shouldn't work. So it would look like this:

#Section "InputDevice"
#        Identifier      "Synaptics Touchpad"
#        Driver          "synaptics"
#        Option          "SendCoreEvents"        "true"
#        Option          "Device"                "/dev/psaux"
#        Option          "Protocol"              "auto-dev"
#        Option          "HorizScrollDelta"      "0"
#EndSection

If that's not it i'd have to gogle it. I'll post back when I find the confim on delete preference.

---

### Post by dannyboy79 on 2007-05-30
i found out that tthis is a bug kind of, they made it so you have to hold the shift key if you want it to ask you. it will however ask you before you delete the stuff from you trash can.

---

### Post by Hobo Joe on 2007-05-30
There is an option. In the file browser, go to 'edt>Preferences>Behaviour', there are a couple of option there concerning confermation messages with the trash.

---

