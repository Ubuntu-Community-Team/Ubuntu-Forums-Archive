---
title: "Macbook Pro Adjust Backlight and Brightness Defaults"
date: 2012-07-08
forum: Apple Hardware Users
---

### Post by porterrakter on 2012-07-08
I installed 12.04 on my Macbook Pro 8,2 and am having trouble finding a way to adjust the keyboard backlight and screen brightness defaults.  On boot the welcome screen always shows both at full brightness and doesn't allow me to change either with keyboard shortcuts.  After I log in I am able to change the settings to a more comfortable level using the keyboard shortcuts but these settings are promptly erased when I reboot, defaulting back to the annoying full brightness/backlight when I log in again.  How can I adjust these defaults?  Is there a way to make Ubuntu remember my last setting for the next time I log in?

---

### Post by GreatDanton on 2012-07-08
I am not familiar with Macbooks so I can't tell you for sure. Macbooks does have BIOS or not? If they have check that in Bios. At least on the regular computer I solve my problem with Bios.

---

### Post by porterrakter on 2012-07-09
I believe MacBooks use EFI (or at least new ones do, and I have a new one) because EFI is used with the new Intel technology Apple started using in 2006.  However, according to Wiki (_[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Platforms_using_EFI.2FUEFI](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Platforms_using_EFI.2FUEFI)_), Macs still have BIOS compatibility because of a firmware update.  Does that help?  I'm pretty new to all this EFI/BIOS stuff so I'm just writing stuff I learned about five minutes ago.

---

### Post by GreatDanton on 2012-07-09
I don't know what Macbook has, definitely some kind of Bios. On normal computer if you hold delete (some laptops f2) during the boot up you are prompted to Bios screen, where you can adjust default brightnes. Try different keys and you will see.

---

### Post by porterrakter on 2012-07-09
Will that work for the keyboard backlight too?  And isn't there a way to control it with the GUI?  Mac OS had no problem keeping my old settings when I logged in...

---

### Post by Kopkins on 2012-07-09
If you edit your /etc/rc.local file you can add a couple lines to set screen and keyboard brightness which is run shortly after boot. 

```

echo '5' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
## this adjusts the screen backlight, the values range from 1 to 15.

echo '25' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
## this adjusts the keyboard brightness and ranges from 1 to 255.

```Those are the two lines I use. I have a macbook 8,1.

Source: [http://ubuntuforums.org/archive/index.php/t-1010532.html](http://ubuntuforums.org/archive/index.php/t-1010532.html)

You can adjust screen brightness with the gui.

System settings > brightness and lock. 

I'm not sure if you can change the keyboard backlight with the gui. 

I don't think Ubuntu remembers the brightness setting on macbooks. Remember that they are different operating systems. Just because OS X behaves one way doesn't mean that Ubuntu has to. 

Kopkins

---

### Post by stefprez on 2012-08-20
I have the same issue that the OP described, except I am on a Macbook Pro version 6,2 (mid-2010 model). I was able to set the screen and keyboard backlight ranges using the instructions [here.]("http://choppit.blogspot.com/p/ubuntu-1204-precise-x64-on-macbook-pro.html") I also added ```
echo X > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness
``` with different values for X into /etc/rc.local, but still when I resume from a suspended computer, or a fresh boot, my retinas burn with the fury that is a max brightness screen. I feel like I am very close to having this solved, but am stuck. Has anyone had any luck with this? Anyone know why my echo X line may not be working?

---

### Post by Kopkins on 2012-08-22
> **stefprez said:**
> I have the same issue that the OP described, except I am on a Macbook Pro version 6,2 (mid-2010 model). I was able to set the screen and keyboard backlight ranges using the instructions [here.]("http://choppit.blogspot.com/p/ubuntu-1204-precise-x64-on-macbook-pro.html") I also added ```
echo X > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness
``` with different values for X into /etc/rc.local, but still when I resume from a suspended computer, or a fresh boot, my retinas burn with the fury that is a max brightness screen. I feel like I am very close to having this solved, but am stuck. Has anyone had any luck with this? Anyone know why my echo X line may not be working?

Can you post your rc.local?

Also please post any output of the following:
One command per line. Use whatever value you have substituted for X.
```

sudo su
echo X > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness
exit

```
Thanks,
Kopkins

---

### Post by stefprez on 2012-09-05
> **Kopkins said:**
> Can you post your rc.local?

Also please post any output of the following:
One command per line. Use whatever value you have substituted for X.
```

sudo su
echo X > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness
exit

```
Thanks,
Kopkins

Sorry for the long delay! Here's my rc.local.

```
#$backlight_brightness range  0-82311
echo $backlight_brightness > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness

#$kbd_brightness range 0-255
echo $kbd_brightness > /sys/class/leds/smc\:\:kbd_backlight/brightness

echo 4 > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness

exit 0
```

When I enter "4" for X on the command you supplied, it dims my screen to almost off, which is what I would expect, however the rc.local doesn't seem to be doing this on boot or wake from sleep. Do I need to include a sudo su command or something in rc.local? Is there another reason why the screen is still defaulting to 1000 suns brightness possibly? Thanks for the help so far!

---

### Post by stefprez on 2012-09-05
> **cismohit said:**
> there is no such way yet..for  last setting for the next time log in..plz reinstall it again

Reinstall what? Ubuntu? That's supposed to solve the problem?

---

### Post by Kopkins on 2012-09-05
> **stefprez said:**
> Sorry for the long delay! Here's my rc.local.

```
#$backlight_brightness range  0-82311
echo $backlight_brightness > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness

#$kbd_brightness range 0-255
echo $kbd_brightness > /sys/class/leds/smc\:\:kbd_backlight/brightness

echo 4 > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness

exit 0
```When I enter "4" for X on the command you supplied, it dims my screen to almost off, which is what I would expect, however the rc.local doesn't seem to be doing this on boot or wake from sleep. Do I need to include a sudo su command or something in rc.local? Is there another reason why the screen is still defaulting to 1000 suns brightness possibly? Thanks for the help so far!

What are those first two executed lines doing? The ones starting with 'echo $*_brightness'? You don't need 'sudo su' because when this script is run, it is run as root. The script should execute near the end of boot, when it enters runlevel 5 and sets up a multiuser graphical session. 

Try using this for your /etc/rc.local for now. Make sure to backup your current one if you want to save it.

If you want to save it. ```
sudo mv /etc/rc.local /etc/rc.local.backup
``` To move it back later. ```
 sudo mv /etc/rc.local.backup /etc/rc.local
``````
#!/bin/sh -e

#$backlight_brightness range  0-82311
#echo $backlight_brightness > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness

#$kbd_brightness range 0-255
#echo $kbd_brightness > /sys/class/leds/smc\:\:kbd_backlight/brightness

echo 4 > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness

exit 0
```Then reboot and see what happens. 

Here is mine, which works on my MBP 8,1, for comparison if you want.
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

echo '5' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
echo '25' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness

exit 0


```
Best of luck,
Kopkins

---

### Post by stefprez on 2012-09-05
> **Kopkins said:**
> What are those first two executed lines doing? The ones starting with 'echo $*_brightness'? You don't need 'sudo su' because when this script is run, it is run as root. The script should execute near the end of boot, when it enters runlevel 5 and sets up a multiuser graphical session. 

Try using this for your /etc/rc.local for now. Make sure to backup your current one if you want to save it.

If you want to save it. ```
sudo mv /etc/rc.local /etc/rc.local.backup
``` To move it back later. ```
 sudo mv /etc/rc.local.backup /etc/rc.local
``````
#!/bin/sh -e

#$backlight_brightness range  0-82311
#echo $backlight_brightness > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness

#$kbd_brightness range 0-255
#echo $kbd_brightness > /sys/class/leds/smc\:\:kbd_backlight/brightness

echo 4 > /sys/devices/virtual/backlight/apple_backlight/subsystem/gmux_backlight/brightness

exit 0
```Then reboot and see what happens. 

Here is mine, which works on my MBP 8,1, for comparison if you want.
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

echo '5' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
echo '25' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness

exit 0


```
Best of luck,
Kopkins

I tried modifying rc.local to just include the echo line you specified, but still on boot it is at max brightness. Just thinking out loud here, is there some sort of user settings file that is overriding the rc.local command when I log on? All your help so far is much appreciated, though!

---

### Post by Kopkins on 2012-09-05
The rc.local file should be executed before login so you should be able to see the screen actually dim as the login screen appears. It would be before you actually login, so there are no user-specific files that could interfere. Here is something I used for a little while before I set everything in my rc.local.

Create a new file and put this in it. ```
import dbus
bus = dbus.SessionBus()

proxy = bus.get_object('org.gnome.SettingsDaemon',
                       '/org/gnome/SettingsDaemon/Power')

iface=dbus.Interface(proxy,dbus_interface='org.gnome.SettingsDaemon.Power.Screen')

iface.SetPercentage(30)
```Save the file in your home directory as '.set_bright_lvl.py'

The preceding '.' makes it a hidden file so you don't have to see it all the time. The '.py' extension makes it executed by python. Other than that, name it whatever you like. Assuming you saved it as ~/.set_bright_lvl.py open terminal and enter the following. ```
sudo chmod +x ~/.set_bright_lvl.py
```Go to your startup apps, and add a new one. Enter the path to your file.

Log out and back in and the screen should be set to 30% brightness.  The '30' in the end of the script dictates the percentage of screen brightness. 

Kopkins

---

### Post by d4m1r on 2013-04-23
Interesting....I have a 2012 13" Macbook Pro (non retina) and this seems  to only work 50%. I can disable the keyboard backlight on boot but  lowering screen brightness does NOT work. It still boots into 100% power  even with the following rc.local:


```

#!/bin/sh -e # # rc.local # # This script is executed at the end of each multiuser runlevel. # Make sure that the script will "exit 0" on success or any other # value on error. # # In order to enable or disable this script just change the execution # bits. # # By default this script does nothing.  echo '3' > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness echo '1' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness  exit 0




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
Fix my own problem by just installing xbacklight...not sure why the  above didn't work but it probably a bug. You can find xbacklight in the  Ubuntu repo's (sudo apt-get install xbacklight) and you can find more  info on it below;

[http://linux.die.net/man/1/xbacklight](http://linux.die.net/man/1/xbacklight)

---

### Post by Kopkins on 2013-04-23
That's what I've ended up using. I created a simple script and modified the sudoers file. The echo thing won't work with sudo, because it needs root for the second half but not the first. So it would technically need to be ```
echo TEXT > sudo tee /path/to/file
```

I modified the sudoers file and .bashrc to allow executing of the file backlight as root without a password. Then created an alias in ~/.bashrc ```
alias backlight='sudo backlight'
```

Then the file script itself. ```

#!/bin/bash

case $1 in
     low)
        xbacklight =20
        echo "$[((90 * 255) / 100) % 256]" > /sys/class/leds/smc\:\:kbd_backlight/brightness
        ;;
    med)
        xbacklight =50
        echo "$[((50 * 255) / 100) % 256]" > /sys/class/leds/smc\:\:kbd_backlight/brightness
        ;;
    high)
        xbacklight =70
        echo "$[((0 * 255) / 100) % 256]" > /sys/class/leds/smc\:\:kbd_backlight/brightness
        ;;
    max)
        xbacklight =100
        echo "$[((0 * 255) / 100) % 256]" > /sys/class/leds/smc\:\:kbd_backlight/brightness
        ;;
    *)
        echo $"Usage $0 {low|med|high|max}"
        exit 1
    
esac

exit


```

Then have this file automatically run when you login. Don't forget to chmod +x

---

