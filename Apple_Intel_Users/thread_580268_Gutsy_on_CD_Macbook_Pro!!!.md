---
title: "Gutsy on CD Macbook Pro!!!"
date: 2007-10-18
forum: Apple Intel Users
---

### Post by voided3 on 2007-10-18
Wow, this is by far the most Intel Mac friendly live CD i've used on my MBP yet! Mine is a Core Duo 2.16ghz, 2GB, 15.4" system w/ a 256mb x1600 mobility and EVERYTHING except for trackpad scrolling and two finger right click worked immediately. All I did was install the ATI driver using the restricted manager and I have a perfectly functioning system. Even the keyboard backlight, screen brightness, and volume controls work perfectly (dare I say even better than on Bootcamp w/ XP on the same machine!). This makes me want to install it natively, but I only have a 100GB drive and I have lots of music and two OSes already... haha. BTW, i'm posting this from the live CD on this machine! Good stuff, good stuff indeed.

---

### Post by theltemes on 2007-10-18
The install went flawlessly, but I have encountered several problems:
[LIST]
[*]The GRUB boot and shutdown splashes aren't showing up, I'm just getting a blank screen.
[*]Suspend and Hibernate lock up my machine.
[*]I have the fglrx drivers installed, but I can't get the Screen/Graphics configuration to work with an external monitor. My external 1600x1200 monitor mirrors my laptop LCD, but when I try to do an extended desktop, it screws up and borks the resolution for both monitors.
[/LIST]

I'm running a rev 1 CD MacBook Pro with 2GB of RAM.

---

### Post by theltemes on 2007-10-19
Well, I was able to fix the most minor problem - no grub boot splashes. It turns out that the install sets the wrong resolution for the Apple LCD on the MacBook. Here is what I did to fix the problem:

Edit the file: /etc/usplash.conf

Change the resolution inside the conf file (it was 1280x1024, I set it to 1440x900 (MacBook Pro resolution))

Run: sudo update-initramfs -u

Correct after reboot.

To fix the heat/whine issue, I added this to rc.local (after doing modprobe applesmc):


echo 3000 > /sys/devices/platform/applesmc.768/fan1_min
echo 3000 > /sys/devices/platform/applesmc.768/fan2_min
echo 2 > /sys/module/processor/parameters/max_cstate

Which sets the fans to 3000 rpm (what I have them set to in SMCFanControl on the OSX side).

---

