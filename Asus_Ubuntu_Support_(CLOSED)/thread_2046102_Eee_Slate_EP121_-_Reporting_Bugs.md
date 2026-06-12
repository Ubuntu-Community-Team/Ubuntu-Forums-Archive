---
title: "Eee Slate EP121 - Reporting Bugs"
date: 2012-08-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by deadland on 2012-08-22
Dear Eee Slate EP121 Users,

since the Slate functionality in ubuntu is faaaar from perfect I would like to report all bugs related to this piece of hardware and Ubuntu 12.10 - Quantal Quetzal to launchpad.

So I am searching in a first step allies which want to become "responsibles" of one or several bugs (sending bug reports and follow up). In a next step we should identify the hardware related bugs and distribute them according the individual interest of each "responsible".

Who wants to report bugs?!
[B][COLOR="Red"]
Also I would be very gratefull, if you could click for each bug on the corresponding bug-reporting-page: "This bug affects X person. Does this bug affect you?"[/COLOR][/B]


**Bugs by category**

_Touchscreen_

[INDENT]Bug: [1041930 - Cannot navigate in nautilius using touchscreen of Asus Slate ep121]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1041930")
Description: *Touching (with a finger) once the screen making it imposible to navigate within nautilus, even with a conventional mouse. (became alreadya problem after upgrading from 11.10 to 12.04). The sidebar still works, but I can't navigate by double-clicking on the "big" Icons in the main-panel.*
Reported by: deadland 
Responsible: **to be defined**
Status: [COLOR="Red"]**New**[/COLOR]
[/INDENT]

[INDENT]Bug: [1041935 - Simulated Secondary Click does not work ]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1041935")
Description: [I]I have activated the "Simulated Secondary Click" in System Settings -> Universal Acces, but it does not work with any input device (1) convential mouse (2) egalax touchscreen (3) wacom ISDv4 90 Pen.
[/I]Reported by: deadland 
Responsible: **to be defined**
Status: [COLOR="Red"]**New**[/COLOR][/INDENT]


[INDENT]_Bug: **to be reported**_
Description: No Multitouch[/INDENT]


_Wacom_
[INDENT]Bug: [1037657 - Asus B121 integrated wacom tablet not recognized]("https://bugs.launchpad.net/ubuntu/+source/libwacom/+bug/1037657")
Description: *The eraser is not recognized, nor it produces a mouse right-click when pressed.*
Reported by: gianlucadv 
Responsible: gianlucadv
Status: [COLOR="Yellow"]**Confirmed**[/COLOR][/INDENT]

[INDENT]Bug: [1041927 - cannot calibrate Wacom ISDv4 90 Pen ]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1041927")
Description: *When I click the "Calibrate..."-Button in System Settings-> Wacom Graphics Tablet nothing happens.*
Reported by: deadland 
Responsible: **to be defined**
Status: [COLOR="Red"]**New**[/COLOR]
[/INDENT]



_Video_

[INDENT]Bug: [1041894 - compiz crashed with SIGSEGV]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041894")
Description: Compiz crashs frequently (same as in 12.04)
Reported by: deadland 
Responsible: **to be defined**
Status: [COLOR="Red"]**New**[/COLOR][/INDENT]


_Audio_

_Bluetooth_
[INDENT]Bug: [1041923 - Cannot enable bluetooth on Asus Slate ep121]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1041923")
Description: *If I right-click on the bluetooth-applet an hit "Turn on Bluetooth" the applet indicates "Bluetooth: On" but when I open "Bluetooth setting ..." it indicates that bluetooth ist "off" and I cannot link it with any bluetooth device.*
Reported by: deadland 
Responsible: **to be defined**
Status: [COLOR="Red"]**New**[/COLOR]
[/INDENT]

_Wlan_
[INDENT]_Bug: **to be reported**_
Description: Disconnects frequently.[/INDENT]


_Onboard (Software)_

[INDENT]Bug: [905636 - firefox awesome-bar and search popup swallow key strokes ]("https://bugs.launchpad.net/onboard/+bug/905636")
Description: *For example when entering a term in the Firefox search box, a list of suggestions pops up and then when you click a letter on Onboard it only gets the focus, and the search box suggestions list disappears, but the letter does not get entered... you have to click it again!*

Additional Links:
[https://bugzilla.mozilla.org/show_bug.cgi?id=715480]("https://bugzilla.mozilla.org/show_bug.cgi?id=715480")
[https://bugs.launchpad.net/onboard/+bug/900196]("https://bugs.launchpad.net/onboard/+bug/900196")

Responsible: **to be defined**
Status: [COLOR="Yellow"]**Confirmed**[/COLOR][/INDENT]

[INDENT]Bug: [1041925 - onboard do not appear on login]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1041925")
Description: *When I try to log in the onscreen keyboard (onboard) does not appear automatically. I have to click on the "universal access" button and uncheck onscreen keyboad and than check it again.*
Reported by: deadland 
Responsible: **to be defined**
Status: [COLOR="Red"]**New**[/COLOR]
[/INDENT]

---

### Post by gianlucadv on 2012-08-25
I am interested.
I have already opened a bug ([https://bugs.launchpad.net/ubuntu/+source/libwacom/+bug/1037657](https://bugs.launchpad.net/ubuntu/+source/libwacom/+bug/1037657)) related to the EP121.

---

### Post by deadland on 2012-08-26
Thank you, I appreciate your participation!

---

### Post by deadland on 2012-08-26
Well, I made a first inventory of all the ep121 related bugs I found so far. Could you please confirm me that you experiencing the same problems and/or inform me if there are more bugs which have to reported/monitored.

---

### Post by gianlucadv on 2012-09-15
I have confirmed on launchpad the bugs I have been able to reproduce.


I also believe that multitouch is not working properly, but I do not know if it is a bug related to EP121 or simply a functionality that is not implemented in ubuntu.

---

### Post by deadland on 2012-09-15
Thanks for your support.

Please could you reconfirm, that you don't have the nautilus-navigation-bug, because this is actually the most annoying bug I have found so far, since it avoids a "normal" usage of Ubuntu. 

It seems, when I touch _once_ the screen with my finger the mouse (Microsoft Comfort Mouse 4500) got to the state "click&hold" and can not be released from this state anymore, even when I unplug it fiscally. 

To illustrate this I've made a screenshot of the shutdown dialogue, where you can see, that when I hover over the dialog the text get selected, even so I don't press the left mouse button.

And my impression is, that only GTK(3) aplications are affected by this bug.

---

### Post by gianlucadv on 2012-09-25
> **deadland said:**
> 

Please could you reconfirm, that you don't have the nautilus-navigation-bug, because this is actually the most annoying bug I have found so far, since it avoids a "normal" usage of Ubuntu. 


I don't have that bug.
But, after a while, touching the screen with the finger becomes a right-click instead of a left-click. That too prevents a normal usage.

---

### Post by onewing on 2013-02-06
Consider me in. I confirmed the bugs that affect me on the appropriate pages.
I definitely have the Nautilus bug.
I have yet to get right-click function under any circumstance, my eraser is not recognized, and the Calibrate button in System Settings does not work.
My bluetooth keyboard was not being re-connected after re-start: I would have to delete it from Devices in Bluetooth Settings and set it up again (for every start-up). As a workaround, I've installed BLUEMAN bluetooth manager, which works like a charm. I just have to  live with two bluetooth applets in my panel.

---

### Post by onewing on 2013-02-06
ps - I'm running Unity 12.10. I have to update my profile. 8-D

---

### Post by deadland on 2013-02-06
> **onewing said:**
> Consider me in. I confirmed the bugs that affect me on the appropriate pages.
I definitely have the Nautilus bug.
I have yet to get right-click function under any circumstance, my eraser is not recognized, and the Calibrate button in System Settings does not work.
My bluetooth keyboard was not being re-connected after re-start: I would have to delete it from Devices in Bluetooth Settings and set it up again (for every start-up). As a workaround, I've installed BLUEMAN bluetooth manager, which works like a charm. I just have to  live with two bluetooth applets in my panel.


Thank you, I thought I'm crazy.

---

### Post by tkingsley on 2013-03-08
I've had the Asus EP121 since it first came out and put Ubuntu on it almost the day I got it. It has gotten a TON better, but it's still frustrating at times. I'll admit that I'm 'tech savvy' but I'm definitely not able to do any type of deep 'detective' work and change things to make it act how I want... Having said that, I'm more than capable of searching the forums and trying 'simple' fixes. 

Touching the screen with my finger seems to work intermittenly, but almost always results in a 'stuck click' behaviour even with the newest eGalax drivers.

Cannot 'double click' using finger touch.

Multitouch doesn't work for me.

Onboard behaviour is also a little annoying at times. When typing in the firefox address or search bar if a suggestion pops down, the keyboard disappears. When placing the cursor in a text entry box on the facebook website the keyboard does not appear.

These are minor gripes, to be sure considering the Wacom drawing capabilities I gain, but every day use issues that keep this from being my 'daily driver.'

I just can't wait until we can use the EP121 with the Ubuntu for Tablets interface!

Amy

---

### Post by JRHigg on 2013-04-28
I was playing with the Slate B121 which is supposed to have the same hardware more or less and installing Ubuntu 13.04 tonight.  Like many others have reported with the device, everything worked fine except the touchscreen.  The issue I was having with it was that it was not registering the end of my click just as the above post described.  I scoured the web for any info in regards to the issue and found things ranging from xorg to drivers.  Every where I looked though led me to 1 common task which was to manually install the eGalax Touch drivers.  So that is what I did, I installed "eGTouch_v2.5.2107.L-x" and during install I selected USB.  From here I rebooted and encountered the same problems.


Here is where my venture started to yield some new information.  Many attempted fixes suggested modifying a file in /etc/X11/xorg/xorg.conf.d/ however I did not have that file and I started investigating.  After several hours of reading through a bunch of information, I decided to investigate if any other distros got it working to see if this was the appropriate path.  I stumbled across a post discussing getting it to work properly in Crunchbang by modifying a similar xorg conf file located under /usr/share/X11.  So I peeked at that location, found the configurations files that were similar to what the "fixes" discussed.  The exact file I keyed in on was /usr/share/X11/xorg.conf.d/52-egalax-virtual.conf.  Now what was interesting about the Crunchbang article was he provided a much more detailed .conf file, so I copied it into the above .conf file and rebooted.  Low and behold all working.

*ADDED* I ran into the issue again after a period of time.  I turned on sound card beep for touch states and it sounded on both.  I switched mouse mode from normal to click on touch and that brought touchscreen functionality back.  From there I started reading the manual and saw an option I have not seen others mention which is meant specifically for HID on the EEEPC Line.  So I turned it on, rebooted and got more calibration options and better function from the touchscreen.  So far with further testing it seems to work well.  As the issue did come back originally after some use, I am not certain this truly resolved the issues, but will update if it does or does not comeback.

*ADDED*  I shut the tablet down last night and powered it back on this morning to test and lost functionality again.  I reran the eGTouchU and notice I lost the calibration options again.  I'll have to investigate why I lost the calibration options.  I suspect that may be related to the issue.  As a side note, switching to click on touch or release still seems to work fine.


So here is a Recap of steps that seem to get it working:

[LIST=1]
[*]Download the eGalax driver (eGTouch_v2.5.2107.L-x) on their webpage
[*]Extract to folder under home
[*]Open terminal to folder from above step, mine was /home/"username"/eGalax
[*]Run sudo sh setup.sh
[*]Choose USB option as interface
[*]Choose 1 controller
[*]Reboot
[*]Open terminal
[*]sudo nano /usr/share/X11/xorg.conf.d/52-egalax-virtual.conf
[*]Paste the following into the file
[*]Reboot
[*]*ADDED* Run eGTouchU found in /usr/bin/
[*]*ADDED* Tool tab has 4pts Cal, Linearization, Clear Parameter, and Draw Test.  Only line test was available till i remodifed the .conf file below to include Option "HidOnEPC" "1"
[/LIST]
```
#Section "InputClass"
#   Identifier "eGalax touch class"
#   MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc."
#   MatchDevicePath "/dev/input/event*"
#   Driver "egalax"
#   Option "Device" "usbauto"
#   Option "Parameters" "/var/lib/eeti.param"
#   Option "ScreenNo" "0"
#   Option "SkipClick" "0"
#EndSection


Section "InputClass"
    Identifier "eGalax touch class"
    MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc."
    MatchDevicePath "/dev/input/event*"
    Driver "evtouch"
    Option "MinX" "0"
    Option "MinY" "0"
    Option "MaxX" "32768"
    Option "MaxY" "32768"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    #Option "TapTimer" "0"
    Option "LongTouchTimer" "350"
    Option "ReportingMode" "Raw"
    # Option "Emulate3Buttons"
    # Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    # Option "maybetapped_action" "click"
    # Option "maybetapped_button" "3"
    Option "longtouched_action" "down"
    Option "longtouched_button" "1"
    Option "oneandahalftap_action" "click"
    Option "oneandahalftap_button" "3"
    # Option "ButtonNumber" "4"
    # Option "Calibrate" "1"
    #original parameters to use with the "void" driver
    #Option "Device" "usbauto"
    #Option "Parameters" "/var/lib/eeti.param"
    #Option "ScreenNo" "0"
    #Option "SkipClick" "0"
    Option "HidOnEPC" "1"
EndSection


#Section "InputClass"
#   Identifier "eGalax mouse class"
#   MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc.|eGalaxTouch Virtual Device"
#   MatchDevicePath "/dev/input/mouse*"
#   Driver "void"
#EndSection


#Section "InputClass"
#   Identifier "eGalax joystick class"
#   MatchProduct "eGalax Inc.|Touchkit|eGalaxTouch Virtual Device"
#   MatchDevicePath "/dev/input/js*"
#   Driver "void" 
#EndSection
```

[HR][/HR]Sources:

[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1041930](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1041930)
[*][http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)
[*][http://olitin.wordpress.com/2011/10/14/eee-slate-install-notes-for-debian-contd/](http://olitin.wordpress.com/2011/10/14/eee-slate-install-notes-for-debian-contd/)
[/LIST]

---

### Post by deadland on 2013-05-06
Happy news today, finally found a solution to the touchsreen problem. The evdev input driver is the bad guy! So I just replaced evdev driver with the wacom driver and tataaa it works.

gksudo gedit /usr/share/X11/xorg.conf.d/10-evdev.conf 

and make the following ajustment

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        **Driver "wacom"**
EndSection

Thats it

---

### Post by deadland on 2013-05-06
Happy news today, finally found a solution to the touchsreen problem. The evdev input driver is the bad guy! So I just replaced evdev driver with the wacom driver and tataaa it works.

```
gksudo gedit /usr/share/X11/xorg.conf.d/10-evdev.conf 

```
and make the following ajustment

```
Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        **Driver "wacom"**
EndSection

```
Thats it

---

### Post by gershom on 2013-06-15
Have they released a tablet based install for ubuntu yet I keep hearing about it and see the docmentation on it but dont see a specific download unless its coupled with the standard desktop version or am I missing something here!

I dont mind setting up the DBoot option on my ep121 but would like an update on peoples experience. It seems like there are only a few of us out here with ep121's and even fewer trying to run Linux or even know what linux is. I wanna run a full linuxOs on this unit but need it tablet focused with wacom functionality.

@DEADLAND, Noticed you mentioned you resolved the touchscreen/wacom issue! and you give some more details and experience update

---

