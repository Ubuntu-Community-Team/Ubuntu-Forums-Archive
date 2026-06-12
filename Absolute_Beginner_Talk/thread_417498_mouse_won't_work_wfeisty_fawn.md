---
title: "mouse won't work w/feisty fawn"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by 3rdgear on 2007-04-21
I have just spent 2 days now, trying to install feisty fawn. I was able to install clean using the alternate CD for feisty, but when I booted up into feisty, my mouse would not work. I use a KVM switch so that I can use the same mouse, keyboard, and monitor with my windows machine as with my linux machine.

I have been using dapper right along without problems, except when I switch back and forth from the windows unit. Then the mouse would become erratic and not useable. However, I could just reboot linux and I could control things again.

I tried efty edge, and things worked fine with the mouse. Then I tried to upgrade to feisty, and everything went fine until I rebooted into feisty. It acts like the mouse isn't there at all. The pointer just sits in one spot. I tried rebooting, same result. Thinking that it might be the kvm switch, I plugged the mouse directly into the ps/2 port on the linux box, and still nothing. I left it plugged in there and rebooted, and still nothing.

Any suggestions out there????

---

### Post by leibowitz on 2007-04-21
It seems critical.

This is what probably happened: you launch the upgrade, then switch your kvm to your windows station. While the ubuntu is upgrading, it see no mouse. And unfortunatly it reconfigures your xserver (which also configure your keyboard and mouse) and see no mouse, so do not care about configuring it.

Now you switch your kvm back to ubuntu, and still can use the mouse (of course, because the Xorg ain't restarted yet). Then you restart, and bam! no more mouse.

That's only a suggestion !

To confirm this, please go to the Applications menu, Accessories, Terminal. Then execute this command and paste the output in here.

```
cat /etc/X11/xorg.conf | grep InputDevice -n --after-context=10
```

---

### Post by catalytic on 2007-04-22
I have been having very similar issues with my mouse, it seems to only work when it wants to. Here output can someone please help me figure out what may be wrong?
41:Section "InputDevice"
42-     Identifier      "Generic Keyboard"
43-     Driver          "kbd"
44-     Option          "CoreKeyboard"
45-     Option          "XkbRules"      "xorg"
46-     Option          "XkbModel"      "pc105"
47-     Option          "XkbLayout"     "us"
48-EndSection
49-
50:Section "InputDevice"
51-     Identifier      "Configured Mouse"
52-     Driver          "mouse"
53-     Option          "CorePointer"
54-     Option          "Device"                "/dev/input/mice"
55-     Option          "Protocol"              "ImPS/2"
56-     Option          "ZAxisMapping"          "4 5"
57-     Option          "Emulate3Buttons"       "true"
58-EndSection
59-
60:Section "InputDevice"
61-     Driver          "wacom"
62-     Identifier      "stylus"
63-     Option          "Device"        "/dev/input/wacom"
64-     Option          "Type"          "stylus"
65-     Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
66-EndSection
67-
68:Section "InputDevice"
69-     Driver          "wacom"
70-     Identifier      "eraser"
71-     Option          "Device"        "/dev/input/wacom"
72-     Option          "Type"          "eraser"
73-     Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
74-EndSection
75-
76:Section "InputDevice"
77-     Driver          "wacom"
78-     Identifier      "cursor"
79-     Option          "Device"        "/dev/input/wacom"
80-     Option          "Type"          "cursor"
81-     Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
82-EndSection
83-
84-Section "Device"
85-     Identifier      "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
86-     Driver          "ati"
--
129:    InputDevice     "Generic Keyboard"
130:    InputDevice     "Configured Mouse"
131:    InputDevice     "stylus"        "SendCoreEvents"
132:    InputDevice     "cursor"        "SendCoreEvents"
133:    InputDevice     "eraser"        "SendCoreEvents"
134-EndSection
135-
136-Section "DRI"
137-    Mode    0666
138-EndSection

---

### Post by 3rdgear on 2007-04-22
[QUOTE=leibowitz;2504377]It seems critical.

This is what probably happened: you launch the upgrade, then switch your kvm to your windows station. While the ubuntu is upgrading, it see no mouse. And unfortunatly it reconfigures your xserver (which also configure your keyboard and mouse) and see no mouse, so do not care about configuring it.

Now you switch your kvm back to ubuntu, and still can use the mouse (of course, because the Xorg ain't restarted yet). Then you restart, and bam! no more mouse.

That's only a suggestion !

To confirm this, please go to the Applications menu, Accessories, Terminal. Then execute this command and paste the output in here.

```
cat /etc/X11/xorg.conf | grep InputDevice -n --after-context=10
```[/QUOTE

I couldn't do this because the mouse would not work to get into terminal. I haven't figured out how the keyboard works without the mouse, so couldn't use keys either.

I reinstalled Edgy.

---

