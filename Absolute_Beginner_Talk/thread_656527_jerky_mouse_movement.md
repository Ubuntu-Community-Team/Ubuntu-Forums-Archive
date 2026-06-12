---
title: "jerky mouse movement"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by occams_beard on 2008-01-02
Hi,

I have a rather annoying problem with jerky mouse movement. For example, whenever Firefox first loads up a webpage, my mouse pointer will freeze for about 1/2 a second causing it to kind of stutter or jerk.  

I thought the CPU might be redlining, but this jerkiness also occurs consistently when Rhythmbox is playing with little CPU usage.

The mouse is a USB optical mouse...

So far I've tried the following without success:

[LIST]
[*]added "irqpoll" and "acpi=off" to my kernel boot line.
[*]disabled desktop effects
[*]Edited the mouse section of xorg.conf as:
[/LIST]
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    #Option         "Protocol" "ImPS/2"
    Option         "Protocol" "auto"
    Option         "ZAxisMapping" "4 5"
    #Option         "Emulate3Buttons" "true"
    Option         "Emulate3Buttons" "false"
EndSection
```

Anything else I can try? This is really driving me nuts:confused:

---

### Post by mmb1 on 2008-01-02
Did your mouse work fine before ubuntu?

---

### Post by jeffus_il on 2008-01-02
mmm, you said its optical, so you remember the dirty mouse ball days.
Did you check your mouse motion settings. acceleration and sensitivity in 
System->Preferences->Mouse???

---

### Post by occams_beard on 2008-01-02
mmb1,

Yes, it works just fine in Windows.  

jeffus_il,

The Gnome mouse settings seem to make no difference. The "jerkiness" also occurs in xfce, so I think its probably something non-gnome specific.

---

### Post by jeffus_il on 2008-01-02
How about:
In a ctrl-alt-f1 console

run straight X using
sudo X :1,0

then run firefox
firefox --display :1,0

and then 
ctrl-alt-f8
it should be there, and you could see if you have the problem on bare X

Here you run firefox alone with X

you could run sudo /etc/init.d/gdm stop

as well

If this works, your mouse and X settings are OK, and gnome the problem, if not  ... we could try something else.

---

### Post by occams_beard on 2008-01-02
Hmm..

Where do I run this from?

firefox --display :1,0

I can start X, but there's no terminal. If I ctrl+alt+f2 and start firefox from there, it says it can't access display 1,0.

---

### Post by occams_beard on 2008-01-02
Nevermind my last post. I started it with  "DISPLAY=:1 firefox &" and was able to get to it on pty9.

Sadly, however, the jerky mouse still occurs even with 1 single bare instance of X running. Anything else I can try?

Thanks!

---

### Post by Saint Angeles on 2008-01-02
perhaps you are using the wrong video driver?

have you done ```
sudo dpkg-reconfigure xserver-xorg
``` ?

---

### Post by occams_beard on 2008-01-02
I'm using the 1.0-9639 nvidia driver with a GeForce fx5200. 

reconfiguring the xserver kind of worries me. What all does it reconfigure? Could I back up my current xorg.conf and restore it later if it doesn't work?

---

### Post by jeffus_il on 2008-01-03
Sorry about the typo, yes backup the xorg.conf, 
sudo cp xorg.conf xorg.conf.backup.

Try the open source driver, edit xorg.conf and change the driver name nvidia to nv.

Here is a good Wiki on the drivers:
[http://gentoo-wiki.com/HOWTO_nVidia_Drivers#Explanation:_XOrg_Drivers_vs._nVidia_Drivers](http://gentoo-wiki.com/HOWTO_nVidia_Drivers#Explanation:_XOrg_Drivers_vs._nVidia_Drivers)

you are not changing the mouse driver, maybe there is some sort of side effect.

---

### Post by dwhitney67 on 2008-01-03
This may sound silly, but do you by chance have a wireless mouse?  Maybe the batteries are well-done.

---

### Post by occams_beard on 2008-01-03
Nope, it's jerky with the "nv" driver as well. (Plus 2d performance seems worse with "nv")

Incidentally I DID try changing the mouse driver to...

```
Section "InputDevice"
         Identifier      "Configured Mouse"
         Driver          "evdev"
         Option          "Device" "/dev/input/mice"
EndSection

```

And that didn't help either. Ack!

](*,)

---

### Post by occams_beard on 2008-01-03
dwhitney67,

No, it's just a generic wired USB optical mouse.

---

### Post by jeffus_il on 2008-01-03
Where could the problem be?

Have you tried another mouse?
Have you checked the bios USB settings, Is legacy USB support enabled?
Try get your full mouse details, name model number etc and do a google search for the correct xorg settings

e.g. google for "MickyMouse MM2008 usb xorg"

---

