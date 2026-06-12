---
title: "iBook G4 trackpad no longer working"
date: 2011-10-16
forum: Apple Hardware Users
---

### Post by kensanata on 2011-10-16
I have an iBook G4. The trackpad used to work in earlier versions of Ubuntu, but I just finished upgrading and it no longer works in Ubuntu 11.10.

[FONT=Courier New]alex@orientalibombus:~$ sudo trackpad show
no trackpad !
[/FONT]
I checked /var/log/Xorg.0.log and searched for ADB mouse and this seemed to be the relevant part:

[FONT=Courier New][    46.323] (II) config/udev: Adding input device ADB mouse (/dev/input/event2)
[    46.323] (**) ADB mouse: Applying InputClass "evdev pointer catchall"
[    46.323] (II) Using input driver 'evdev' for 'ADB mouse'
[    46.323] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    46.323] (**) ADB mouse: always reports core events
[    46.323] (**) ADB mouse: Device: "/dev/input/event2"
[    46.323] (--) ADB mouse: Found 3 mouse buttons
[    46.323] (--) ADB mouse: Found relative axes
[    46.323] (--) ADB mouse: Found x and y relative axes
[    46.323] (II) ADB mouse: Configuring as mouse
[    46.323] (**) ADB mouse: YAxisMapping: buttons 4 and 5
[    46.328] (**) ADB mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.328] (**) Option "config_info" "udev:/sys/devices/virtual/input/input2/event2"
[    46.328] (II) XINPUT: Adding extended input device "ADB mouse" (type: MOUSE)
[    46.328] (II) ADB mouse: initialized for relative axes.
[    46.328] (**) ADB mouse: (accel) keeping acceleration scheme 1
[    46.328] (**) ADB mouse: (accel) acceleration profile 0
[    46.328] (**) ADB mouse: (accel) acceleration factor: 2.000
[    46.328] (**) ADB mouse: (accel) acceleration threshold: 4
[    46.338] (II) config/udev: Adding input device ADB mouse (/dev/input/mouse0)
[    46.338] (II) No input driver/identifier specified (ignoring)
[/FONT]
There are sections regarding my Logitech mouse, the ADB keyboard, powerbutton, etc. Can you spot anything suspicious?

---

### Post by rsavage on 2011-10-17
Not tried 11.10 so don't know if there is a problem, but have you tried editing your xorg.conf file?  I don't like an overcomplicated one as I think it leads to more problems if things change in an update.  What happens if you remove your input device section?  More info on how to do this [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1)

---

### Post by kensanata on 2011-10-17
Thanks for the answer. I'll check that. In the mean time I noticed that the problem is much less severe than I thought. If the laptop boots without the external Logitech mouse connected, the trackpad will work. Weird. :)

---

### Post by jumil on 2011-10-17
I just did a fresh install of 11.10 on my ibook G4  and the trackpad worked out of the box.

I checked your log against mine and they are identical. At least in the section you posted.
So nothing suspicious there.

Also no problems with my external mouse. Just a normal 3 button and a wheel one. Weird indeed.
What kind of mouse is it. Anything fancy?

---

### Post by rsavage on 2011-10-17
jumil, welcome to the forum!  Did you use a live cd to install 11.10 and when did you download the image?  Did you have any problems with the install?

---

### Post by jumil on 2011-10-17
The 11.10 mini iso I downloaded did not recognize the ibooks hard drive during install. I don't know if that has been fixed by now.

So I used the 11.04 mini iso to install a command line system and ran the upgrade from there.
Upgrading 11.04 on my desktop had not properly switched from GDM to LightDM. And since I was primarily after trying how LightDM would perform on the iBook I wanted to do a clean install.

After upgrading the base system to 11.10 I installed Ubuntu via tasksel.

---

### Post by jumil on 2011-10-20
kensanata, since you seem to be using Ubuntu 11.10 on an iBookG4 can you please tell me if you are experiencing the same problems I am?

I have described theese in another thread
[http://ubuntuforums.org/showthread.php?t=1863407](http://ubuntuforums.org/showthread.php?t=1863407)

Also what Display manager are yu currently using? Did the transition from GDM to LighDM happen for you?

I will try switching my system to GDM later to see if my problems might be connected to that.

---

