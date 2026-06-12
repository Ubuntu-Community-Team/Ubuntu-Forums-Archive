---
title: "Ubuntu 12.04 boots with full screen brightness and keyboard backlight"
date: 2012-05-26
forum: Apple Hardware Users
---

### Post by princehektor on 2012-05-26
I have dual-booted my Macbook Pro with Ubuntu 12.04 . Whenever i log-in  to Ubuntu, it does so with full screen brightness and keyboard backlight  at full . How do i get rid of this? How can i tweak the start-up  setting for screen brightness and disable keyboard backlight at  start-up?

---

### Post by watgrad on 2012-05-27
I also have this issue - suggestions appreciated

---

### Post by poliva on 2012-05-30
Add this to /etc/rc.local:

```

echo '2' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
echo '0' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness

```

Change the values to match your preference, keyboard brightness from 0 to 255, and screen backlight from 1 to 15.

You might also want to have a look at lightum:

[lightum - MacBook automatic light sensor daemon]("https://github.com/poliva/lightum#lightum---macbook-automatic-light-sensor-daemon")

---

### Post by watgrad on 2012-06-21
Thanks for this - it works well.  

Just one thing - the second line cannot have a value of 0, the lowest setting for the keyboard is 1 (which turns the backlights off)

Thanks for your suggestion.
(for other mac users - I've got macbookpro8,1 running Linux Mint 13 - this worked well for me)

> **poliva said:**
> Add this to /etc/rc.local:

```

echo '2' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
echo '0' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness

```

Change the values to match your preference, keyboard brightness from 0 to 255, and screen backlight from 1 to 15.

You might also want to have a look at lightum:

[lightum - MacBook automatic light sensor daemon]("https://github.com/poliva/lightum#lightum---macbook-automatic-light-sensor-daemon")

---

### Post by mustinet1900 on 2012-12-20
> **poliva said:**
> Add this to /etc/rc.local:

```

echo '2' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
echo '0' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness

```

Change the values to match your preference, keyboard brightness from 0 to 255, and screen backlight from 1 to 15.

You might also want to have a look at lightum:

[lightum - MacBook automatic light sensor daemon]("https://github.com/poliva/lightum#lightum---macbook-automatic-light-sensor-daemon")

The first echo for the display brightness didnt do anything on my macbook 5.5. 
Can someone help with the display brightness

---

### Post by iMac71 on 2012-12-24
> **mustinet1900 said:**
> The first echo for the display brightness didnt do anything on my macbook 5.5. 
Can someone help with the display brightness
you might try this:```
echo 8 > /sys/class/backlight/apple_backlight/brightness
```it works fine on my iMac 7.1

---

### Post by d4m1r on 2013-04-23
Interesting....I have a 2012 13" Macbook Pro (non retina) and this seems   to only work 50%. I can disable the keyboard backlight on boot but   lowering screen brightness does NOT work. It still boots into 100% power   even with the following rc.local:


```

#!/bin/sh -e # # rc.local # # This script is executed at the end of each  multiuser runlevel. # Make sure that the script will "exit 0" on  success or any other # value on error. # # In order to enable or disable  this script just change the execution # bits. # # By default this  script does nothing.  echo '3' >  /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness  echo '1' >  /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness   exit 0

```


I wondered why and when I ran just the below command in terminal, I got the below;

```
sudo echo '5' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
``` (with and without the '#')

```
sudo echo '5' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness: Permission denied
```

Permission denied even with sudo?! :confused:

---

### Post by d4m1r on 2013-04-23
Fix my own problem by just installing xbacklight...not sure why the above didn't work but it probably a bug. You can find xbacklight in the Ubuntu repo's (sudo apt-get install xbacklight) and you can find more info on it below;

[http://linux.die.net/man/1/xbacklight](http://linux.die.net/man/1/xbacklight)

---

### Post by andy_w2 on 2013-08-28
Before you run the code, try ```
sudo su
```

**Then run your commands without the sudo in front.  **


> **d4m1r said:**
> 

```
sudo echo '5' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
``` (with and without the '#')

```
sudo echo '5' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness: Permission denied
```

Permission denied even with sudo?! :confused:

---

### Post by andy_w2 on 2013-08-28
Adding these to /etc/rc.local didn't work for me on Linux Mint running  on a Macbook Air 2012 (it worked up to the login window then after login it quit working).   I had to run a script as sudo at login using  the above commands:  [http://greeennotebook.com/2010/06/run-application-as-root-at-startup/](http://greeennotebook.com/2010/06/run-application-as-root-at-startup/)

First I created a shell script in ~/subfolder/script.sh with the two commands from above: 

```

echo '2' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
echo '0' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
exit 0

```

Then had to edit the sudoers file and enable the custom script to run without a password. 

```
username ALL=NOPASSWD:/full/path/to/script.sh
```

(of course replace username and path with your own)

Then basically just added ```
sudo /full/path/to/script.sh
``` to startup applications.  

This is all explained in the link.

Any suggestions for improvement would be appreciated, but this works for me.

---

### Post by Kin_Li on 2014-01-25
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


echo '2' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
echo '0' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness


exit 0

```

Is it OK?
I just have to replace the original one?

---

### Post by d4m1r on 2014-01-27
What version Macbook do you have? Try it and see ;)

---

