---
title: "Improve battery life and ACPI functions on the macbookpro"
date: 2009-07-17
forum: Apple Hardware Users
---

### Post by crocowhile on 2009-07-17
I recently got one the newest MacBookPro 13" and after giving a 2 weeks trial period to OSX I decided to switch back to ubuntu and I certainly don't regret it. The only two things I *really* loved in OSX were:

* longer battery life (apple claims up to 7 hours and my experience is on that line)

* very fast and efficient suspend/resume

Those two weren't quite the same in an out-of-the box ubuntu 9.04 installation but with some hacks here and there I got them working not too bad. Here I want to describe what I did and then hopefully with a bit of team work we'll get even better!

**Suspend/Resume**

Suspend and Resume actually didn't work at all after installation. I figured the reason was that I didn't have the latest EFI version. So I rebooted in OSX, did the upgrade to 1.7 and voila. Worked fine. 
They were still a bit slower than OSX, though. Especially resume (which is the one we care the most, of course). To fix it I did the following

install a package called uswsusp
```
sudo apt-get install uswsusp
```
the package carries two nice tools: s2ram and s2disk
First of all make sure they work launching
```
sudo s2ram --force
```
to suspend to ram or 
```
sudo s2disk
```
to hibernate.

I personally don't care too much about hibernation. Nice thing about s2ram, though, is that it goes to sleep maintaining somehow the proper wifi settings so that when you open up the lid again the machine is immediately connected to the internet, exactly as it happens in OSX. The resume takes about 5 seconds and you are ready to go. 

By default gnome prompts you with the password after resume. If you don't like this behaviour, you can change it running 
```
gconftool -s /apps/gnome-power-manager/lock/suspend -t bool false

```

you can of course use s2ram and s2disk as default tools. to do so, you need to replace two of the existing scripts.
```

sudo cp /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux.bak
sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux.bak
```
and then
```
 sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
```
replace what you find with:
```

#!/usr/bin/env bash
/usr/sbin/s2disk

```
```
 sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
```
replace what you find with:
```

#!/usr/bin/env bash
/usr/sbin/s2ram --force

```

**Restart**
Restart also doesn't seem to work out of the box. With kernels 2.6.28-13 and -14 the system would go throughout the entire rebooting procedure then hang at the very end with "Restarting System". As a workaround, install kexec-tools and make sure it's active. This will enable kexec restart (meaning, when you restart the computer will skip EFI/GRUB and load directly the kernel.
```

sudo apt-get install kexec-tools
gedit /etc/default/kexec

```
and make sure the load exec is set to True.

[B]Extend Battery life.
[/B]

This is a bit trickier. First of all, we should be aware of what the goal is. Let's learn more about the battery:
```
gg@ggmac:~$ cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         54500 mWh
last full capacity:      55300 mWh
battery technology:      rechargeable
design voltage:          10950 mV
design capacity warning: 250 mWh
design capacity low:     100 mWh
capacity granularity 1:  10 mWh
capacity granularity 2:  10 mWh
model number:            bq20z45189ABCDEF0123456789ABCDE
serial number:           
battery type:            LIONz45189ABCDEF0123456789ABCDE
OEM info:                DPONz45189ABCDEF0123456789ABCDE
```

What we are interested in is the total capacity, in my case about 55W.
Now, we need to know what the consumption is. To do this, the best way is to use powertop
```
sudo apt-get install powertop

```
and then:
```
powertop -d

```
powertop will run for 15 seconds and collect info about the system. There's plenty of documentation out there: go dive. For now let's say what you care the most is this line:
```
Power usage (ACPI estimate): 16.3W (2.7 hours) 
```
It says that your laptop consumes about 16W/hour meaning that with a full charge you'd get 55/16=~3.5 hours of battery. Our goal is to go down to something between 9 and 10 W.

Here's how. First of all, the video. You probably have some new version of the nvidia driver. Open xorg.conf and add the following lines to the section Device:

```
    
Option "OnDemandVBlankInterrupts" "True"
Option "RegistryDwords" "PowerMizerLevel=0x3"

```

and the following to the section screen:

```
Option	   "Coolbits" "1"

```

these lines will enable VBlankondemand and will set powermizer to "ondemand"; the latter will allow overclocking/downclocking of the GPU.

After having done this, you want to change a couple of kernel settings.
Open /boot/grub/menu.list and add to the kernel line the following:
```
usbcore.autosuspend=1 hpet=force

```
so, your kernel line should read something like this:
```
kernel		(hd0,2)/boot/vmlinuz-2.6.28-13-generic root=/dev/sda3 ro quiet splash usbcore.autosuspend=1 hpet=force vga=791
```

Finally, the more juicy part. Create a file called 99-savings
```
gedit ~/99-savings

```
and copy and paste the following code
```
#!/usr/bin/env bash

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then
  # Set the drive to mostly stay awake.  Some may want to change -B 254
  # to -B 255 to avoid accumulating Load_Cycle_Counts
  hdparm -B 254 -S 240 -M 254 /dev/sda

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=60 /
  mount -o remount,commit=60 /home

  # Turn off the laptop mode disk optimization
  #echo 0 > /proc/sys/vm/laptop_mode

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk
  # activity.
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  
  # Set the SATA to max performance
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Enable the webcam driver
#  modprobe uvcvideo

  #restart bluetooth #you can also decide to use RFKILL here. 
  sudo /usr/sbin/hciconfig hci0 up

  # Start optional  services
#  sudo /etc/init.d/cron start
  sudo /etc/init.d/bluetooth start
  sudo /etc/init.d/preload start

  #reset brightness of screen and keyboard
  sudo nvclock -S 85
  sudo echo 50 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness

  #Enable eth0
  sudo ifconfig eth0 up

  #reset clock nvidia card (requires coolbits=1)
  sudo nvidia-settings -a GPU2DClockFreqs=100,0
  sudo nvidia-settings -a GPU3DClockFreqs=450,0

else # Save power

  # Set the disks to aggressively save power and use the lowest acoustic
  # level.  Some might find these settings too aggressive.  If so, change 
  # "-S 4" to something larger like -S 24 (two minutes) and -B 128 to -B 254.
  hdparm -B 128 -S 4 -M 128 /dev/sda
  
  # Change the ext3 commit times to 10 minutes.  This reduces diskhcd
  # activity
  mount -o remount,commit=600 /

  # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945 driver to power savings.
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Set sound card power savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set SATA to minimum power
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
  
  # Remove the webcam driver
#  modprobe -r uvcvideo

  #Disable eth0
  sudo ifconfig eth0 down

  # Stop unneccessary  services
#  sudo /etc/init.d/cron stop
  sudo /etc/init.d/bluetooth stop
  sudo /etc/init.d/preload stop

  #poweroff bluetooth
  sudo /usr/sbin/hciconfig hci0 down

  #dim screen and keyboard brightness to minimum
  sudo nvclock -S 15
  sudo echo 0 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness

  #downclock nvidia card (requires coolbits=1)
  sudo nvidia-settings -a GPU2DClockFreqs=25,0
  sudo nvidia-settings -a GPU3DClockFreqs=125,0

fi
```

Most of the content of this script comes from this [thread]("http://ubuntuforums.org/showthread.php?t=847773") and has been tweaked to my needs. Based on your personal taste you can also decide to uncomment the lines with the load/load video module and cron.

install the script doing
```
sudo install 99-savings /etc/pm/sleep.d
sudo install 99-savings /etc/pm/power.d

```

In the thread I linked above you also find a script called 99-nvidia You may want to install that one too.

Doing so I get a usage of 9.5W, equivalent of about 6 hours. This is with WIFI on, browsing the internet and having the screen brightness very low.
Still not quite like OSX but not too bad either.

Let me know how it works for you.
(YMMV)

---

### Post by hvthao on 2009-07-17
Using laptop-mode can get me 6 hours working!

---

### Post by crocowhile on 2009-07-18
> **hvthao said:**
> Using laptop-mode can get me 6 hours working!Switching laptop mode is the first thing I tried but hardly made a difference. I am suprise to hear it does for you. What's your setup?
I have 9.04, 2.6.28-13

---

### Post by hvthao on 2009-07-18
First, enable laptop-mode in /etc/default/acpi-support

Second, do some configurations in /etc/laptop-mode/conf.d

---

### Post by tripundra on 2009-07-19
How would you do the Video CPU tweak if you had the Intel GMA video card as the Macbook2,1's have?

I followed your directions and it's saving up some watts.
But I wanted to be more aggressive and save on the GPU unit as well.
Does the Intel GPU accept underclocking?
 
Thanks
Edgar


P.S:
tried going to the Xorg.conf file and it comes out blank, nothing written! is this normal?
just to check, it is located in /etc/X11/xorg.conf

---

### Post by crocowhile on 2009-07-19
> **hvthao said:**
> First, enable laptop-mode in /etc/default/acpi-support
Second, do some configurations in /etc/laptop-mode/conf.d

That is what I did but it really doesn't help. Actually all I get is trouble if I touch hal and tty.

> **tripundra said:**
> I followed your directions and it's saving up some watts. But I wanted to be more aggressive and save on the GPU unit as well. Does the Intel GPU accept underclocking?Sorry, I don't know.

---

### Post by Nikos.Alexandris on 2009-07-21
> **crocowhile said:**
> ...
The only two things I *really* loved in OSX were:

* longer battery life (apple claims up to 7 hours and my experience is on that line)

* very fast and efficient suspend/resume

Those two weren't quite the same in an out-of-the box ubuntu 9.04 installation but with some hacks here and there I got them working not too bad.
...

Thanks for this. I am about to try this out today on a MPB 5,1. Did anybody else give a try to an MBP 5,1?

Best regards, Nikos

---

### Post by inphektion on 2009-07-21
> **hvthao said:**
> First, enable laptop-mode in /etc/default/acpi-support

Second, do some configurations in /etc/laptop-mode/conf.d

what configs did you edit in conf.d or does anyone recommend certain ones to do the most good?

---

### Post by Rog-Mahal on 2009-07-21
@tripundra

No, I don't think that's normal. It should have some basic settings in there, but a lot of stuff has been moved to the new fdi system. Are you sure you typed in the correct path? Did you make sure to use sudo?

---

### Post by Nikos.Alexandris on 2009-07-23
> **Nikos.Alexandris said:**
> Thanks for this. I am about to try this out today on a MPB 5,1. Did anybody else give a try to an MBP 5,1?

Best regards, Nikos

I am unsure if all this is worthy for an MBP5,1 15". The difference is the NVIDIA GeForce 9600M GT graphics in the 15" models. That's actually the "main" problem with respect to battery life.

Kind regards, Nikos

---

### Post by crocowhile on 2009-07-23
I actually have the MBP 13", that has only one GPU (9400) and yet with this system I save at least 4W. I wish I could save more, though.

---

### Post by Nikos.Alexandris on 2009-07-28
> **Nikos.Alexandris said:**
> I am unsure if all this is worthy for an MBP5,1 15". The difference is the NVIDIA GeForce 9600M GT graphics in the 15" models. That's actually the "main" problem with respect to battery life.

In the following thread/post [[COLOR="Blue"]http://ubuntuforums.org/showpost.php?p=7691208&postcount=905[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7691208&postcount=905") I've posted a screenshot of the mbp5,1 running for almost 2 hours when using the onboard graphic card. Currently I can't get the power-manager and display/keyboard brightness to work correctly. I suppose that battery life will improve when dealing with these issues.

Kind regards, Nikos

---

### Post by stockley on 2009-07-28
> * longer battery life (apple claims up to 7 hours and my experience is on that line)

From my experience its been more like 5 hours max, running word or flicking through the web. Generally thought, its been more like 3 or 4 because of other applications like iTunes or something. But 7 hours... wow... macbooks do have good batteries, but are you sure its 7 hours? Maybe its the new-ish models or the pro, I've got 3 macbooks and an iBook in my house, no pros :P

---

### Post by crocowhile on 2009-07-28
> **stockley said:**
> From my experience its been more like 5 hours max, running word or flicking through the web. Generally thought, its been more like 3 or 4 because of other applications like iTunes or something. But 7 hours... wow... macbooks do have good batteries, but are you sure its 7 hours? Maybe its the new-ish models or the pro, I've got 3 macbooks and an iBook in my house, no pros :P

This is the one I was referring to:
[http://www.apple.com/macbookpro/specs-13inch.html](http://www.apple.com/macbookpro/specs-13inch.html)

I haven't measure precisely the 7 hours to be honest, it's more of a feeling.

---

### Post by hvthao on 2009-07-28
Cannot get 7 hours with web surfing!

---

### Post by raronson on 2009-07-30
Thanks for the howto.  Using a macbook4,1(non-pro) the suspend-resume portion fixed some issues with not properly waking or waking in a lagged state that made mousing and using the keyboard extremely difficult.

If you don't mind, I'm going to post a link to the Karmic forum and suggest that these tools be looked at instead of the current default.

Thanks again.

---

### Post by Takala on 2009-09-20
> **crocowhile said:**
> I recently got one the newest MacBookPro 13" and after giving a 2 weeks trial period to OSX I decided to switch back to ubuntu and I certainly don't regret it. The only two things I *really* loved in OSX were:

* longer battery life (apple claims up to 7 hours and my experience is on that line)

* very fast and efficient suspend/resume

Those two weren't quite the same in an out-of-the box ubuntu 9.04 installation but with some hacks here and there I got them working not too bad. Here I want to describe what I did and then hopefully with a bit of team work we'll get even better!

**Suspend/Resume**

Suspend and Resume actually didn't work at all after installation. I figured the reason was that I didn't have the latest EFI version. So I rebooted in OSX, did the upgrade to 1.7 and voila. Worked fine. 
They were still a bit slower than OSX, though. Especially resume (which is the one we care the most, of course). To fix it I did the following

install a package called uswsusp
```
sudo apt-get install uswsusp
```the package carries two nice tools: s2ram and s2disk
First of all make sure they work launching
```
sudo s2ram --force
```to suspend to ram or 
```
sudo s2disk
```to hibernate.

I personally don't care too much about hibernation. Nice thing about s2ram, though, is that it goes to sleep maintaining somehow the proper wifi settings so that when you open up the lid again the machine is immediately connected to the internet, exactly as it happens in OSX. The resume takes about 5 seconds and you are ready to go. 

By default gnome prompts you with the password after resume. If you don't like this behaviour, you can change it running 
```
gconftool -s /apps/gnome-power-manager/lock/suspend -t bool false

```you can of course use s2ram and s2disk as default tools. to do so, you need to replace two of the existing scripts.
```

sudo cp /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux.bak
sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux.bak
```and then
```
 sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
```replace what you find with:
```

#!/usr/bin/env bash
/usr/sbin/s2disk

``````
 sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
```replace what you find with:
```

#!/usr/bin/env bash
/usr/sbin/s2ram --force

```**Restart**
Restart also doesn't seem to work out of the box. With kernels 2.6.28-13 and -14 the system would go throughout the entire rebooting procedure then hang at the very end with "Restarting System". As a workaround, install kexec-tools and make sure it's active. This will enable kexec restart (meaning, when you restart the computer will skip EFI/GRUB and load directly the kernel.
```

sudo apt-get install kexec-tools
gedit /etc/default/kexec

```and make sure the load exec is set to True.

[B]Extend Battery life.
[/B]

This is a bit trickier. First of all, we should be aware of what the goal is. Let's learn more about the battery:
```
gg@ggmac:~$ cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         54500 mWh
last full capacity:      55300 mWh
battery technology:      rechargeable
design voltage:          10950 mV
design capacity warning: 250 mWh
design capacity low:     100 mWh
capacity granularity 1:  10 mWh
capacity granularity 2:  10 mWh
model number:            bq20z45189ABCDEF0123456789ABCDE
serial number:           
battery type:            LIONz45189ABCDEF0123456789ABCDE
OEM info:                DPONz45189ABCDEF0123456789ABCDE
```What we are interested in is the total capacity, in my case about 55W.
Now, we need to know what the consumption is. To do this, the best way is to use powertop
```
sudo apt-get install powertop

```and then:
```
powertop -d

```powertop will run for 15 seconds and collect info about the system. There's plenty of documentation out there: go dive. For now let's say what you care the most is this line:
```
Power usage (ACPI estimate): 16.3W (2.7 hours) 
```It says that your laptop consumes about 16W/hour meaning that with a full charge you'd get 55/16=~3.5 hours of battery. Our goal is to go down to something between 9 and 10 W.

Here's how. First of all, the video. You probably have some new version of the nvidia driver. Open xorg.conf and add the following lines to the section Device:

```
    
Option "OnDemandVBlankInterrupts" "True"
Option "RegistryDwords" "PowerMizerLevel=0x3"

```and the following to the section screen:

```
Option       "Coolbits" "1"

```these lines will enable VBlankondemand and will set powermizer to "ondemand"; the latter will allow overclocking/downclocking of the GPU.

After having done this, you want to change a couple of kernel settings.
Open /boot/grub/menu.list and add to the kernel line the following:
```
usbcore.autosuspend=1 hpet=force

```so, your kernel line should read something like this:
```
kernel        (hd0,2)/boot/vmlinuz-2.6.28-13-generic root=/dev/sda3 ro quiet splash usbcore.autosuspend=1 hpet=force vga=791
```Finally, the more juicy part. Create a file called 99-savings
```
gedit ~/99-savings

```and copy and paste the following code
```
#!/usr/bin/env bash

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then
  # Set the drive to mostly stay awake.  Some may want to change -B 200
  # to -B 255 to avoid accumulating Load_Cycle_Counts
  hdparm -B 200 -S 240 -M 254 /dev/sda

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=60 /
  mount -o remount,commit=60 /home

  # Turn off the laptop mode disk optimization
  #echo 0 > /proc/sys/vm/laptop_mode

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk
  # activity.
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  
  # Set the SATA to max performance
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Enable the webcam driver
#  modprobe uvcvideo

  #restart bluetooth
  sudo /usr/sbin/hciconfig hci0 up

  # Start optional  services
#  sudo /etc/init.d/cron start
  sudo /etc/init.d/bluetooth start
  sudo /etc/init.d/preload start

  #reset brightness of screen and keyboard
  sudo nvclock -S 85
  sudo echo 50 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness

  #Enable eth0
  sudo ifconfig eth0 up

  #reset clock nvidia card (requires coolbits=1)
  sudo nvidia-settings -a GPU2DClockFreqs=100,0
  sudo nvidia-settings -a GPU3DClockFreqs=450,0

else # Save power

  # Set the disks to aggressively save power and use the lowest acoustic
  # level.  Some might find these settings too aggressive.  If so, change 
  # "-S 4" to something larger like -S 24 (two minutes) and -B 1 to -B 255.
  hdparm -B 1 -S 4 -M 128 /dev/sda
  
  # Change the ext3 commit times to 10 minutes.  This reduces diskhcd
  # activity
  mount -o remount,commit=600 /

  # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945 driver to power savings.
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Set sound card power savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set SATA to minimum power
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
  
  # Remove the webcam driver
#  modprobe -r uvcvideo

  #Disable eth0
  sudo ifconfig eth0 down

  # Stop unneccessary  services
#  sudo /etc/init.d/cron stop
  sudo /etc/init.d/bluetooth stop
  sudo /etc/init.d/preload stop

  #poweroff bluetooth
  sudo /usr/sbin/hciconfig hci0 down

  #dim screen and keyboard brightness to minimum
  sudo nvclock -S 15
  sudo echo 0 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness

  #downclock nvidia card (requires coolbits=1)
  sudo nvidia-settings -a GPU2DClockFreqs=25,0
  sudo nvidia-settings -a GPU3DClockFreqs=125,0

fi
```Most of the content of this script comes from this [thread]("http://ubuntuforums.org/showthread.php?t=847773") and has been tweaked to my needs. Based on your personal taste you can also decide to uncomment the lines with the load/load video module and cron.

install the script doing
```
sudo install 99-savings /etc/pm/sleep.d
sudo install 99-savings /etc/pm/power.d

```In the thread I linked above you also find a script called 99-nvidia You may want to install that one too.

Doing so I get a usage of 9.5W, equivalent of about 6 hours. This is with WIFI on, browsing the internet and having the screen brightness very low.
Still not quite like OSX but not too bad either.

Let me know how it works for you.
(YMMV)

I just bought a new macbook pro 5,5 and I was horrified how low was the battery life in Ubuntu jaunty. However, I did the quoted tutorial, and the power consumption came down from 16.something W to 8.6W. Amayzing! I created this ubuntuforum account just to say thank you very, very much!


```

PowerTOP 1.11   (C) 2007, 2008 Intel Corporation 

Collecting data for 15 seconds 


Cn              Avg residency
C0 (cpu running)        ( 4.4%)
polling          0.0ms ( 0.0%)
C1 mwait      0.0ms ( 0.0%)
C2 mwait      0.1ms ( 0.0%)
C4 mwait      7.0ms (95.6%)
P-states (frequencies)
  2.27 Ghz     0.0%
  2.13 Ghz     0.0%
  1.87 Ghz     0.0%
  1.60 Ghz     0.0%
   798 Mhz   100.0%
Wakeups-from-idle per second : 137.2    interval: 15.0s
Power usage (ACPI estimate): 8.6W (0.9 hours) 
Top causes for wakeups:
  27.2% ( 57.5)       <interrupt> : ohci_hcd:usb3 
  27.2% ( 57.5)   USB device  3-6 : Apple Internal Keyboard / Trackpad (Apple Inc.) 
   9.8% ( 20.7)      <kernel IPI> : Rescheduling interrupts 
   6.2% ( 13.2)     <kernel core> : hrtimer_start (tick_sched_timer) 
   5.4% ( 11.4)     <kernel core> : scan_async (ehci_watchdog) 
   5.2% ( 11.0)       <interrupt> : extra timer interrupt 
   3.6% (  7.6)       <interrupt> : ahci 
   2.8% (  6.0)    wpa_supplicant : wl_add_timer (wl_timer) 
   2.6% (  5.6)       <interrupt> : ehci_hcd:usb2 
   2.2% (  4.7)   USB device  2-5 : Card Reader (Apple) 
   2.2% (  4.6)    gnome-terminal : schedule_hrtimeout_range (hrtimer_wakeup) 
   1.9% (  4.0)       <interrupt> : eth1, HDA Intel 
   0.5% (  1.1)           firefox : futex_wait (hrtimer_wakeup) 
   0.5% (  1.0)       <interrupt> : ohci1394, nvidia 
   0.5% (  1.0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer) 
   0.4% (  0.9)   hald-addon-stor : schedule_hrtimeout_range (hrtimer_wakeup) 
   0.3% (  0.7)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.3% (  0.7)              Xorg : schedule_hrtimeout_range (hrtimer_wakeup) 
   0.2% (  0.3)    gnome-terminal : do_nanosleep (hrtimer_wakeup) 
   0.2% (  0.3)   gnome-power-man : schedule_hrtimeout_range (hrtimer_wakeup) 
   0.1% (  0.3)       compiz.real : schedule_hrtimeout_range (hrtimer_wakeup) 
   0.1% (  0.2)   update-notifier : schedule_hrtimeout_range (hrtimer_wakeup) 
   0.1% (  0.2)       gnome-panel : schedule_hrtimeout_range (hrtimer_wakeup) 
   0.1% (  0.2)              hald : schedule_timeout (process_timeout) 
   0.1% (  0.1)       <interrupt> : acpi 
   0.1% (  0.1)         ssh-agent : schedule_hrtimeout_range (hrtimer_wakeup) 
   0.1% (  0.1)    NetworkManager : schedule_hrtimeout_range (hrtimer_wakeup) 
   0.0% (  0.1)     <kernel core> : input_handle_event (input_repeat_key) 
   0.0% (  0.1)           syslogd : hrtimer_start (it_real_fn) 
   0.0% (  0.1)     <kernel core> : neigh_add_timer (neigh_timer_handler) 
   0.0% (  0.1)          gconfd-2 : schedule_hrtimeout_range (hrtimer_wakeup) 
   0.0% (  0.1)              hald : schedule_hrtimeout_range (hrtimer_wakeup) 
   0.0% (  0.1)              Xorg : laptop_io_completion (laptop_timer_fn) 
   0.0% (  0.1)           pdflush : schedule_timeout (process_timeout) 
   0.0% (  0.1)     <kernel core> : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.1)           firefox : schedule_hrtimeout_range (hrtimer_wakeup) 

A USB device is active 100.0% of the time:
USB device  2-5 : Card Reader (Apple)

Suggestion: Enable USB autosuspend by pressing the U key or adding 
usbcore.autosuspend=1 to the kernel command line in the grub config

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

Recent USB suspend statistics
Active  Device name
100.0%    USB device 4-1.1 : Bluetooth USB Host Controller (Apple, Inc.)
100.0%    USB device  3-6 : Apple Internal Keyboard / Trackpad (Apple Inc.)
100.0%    USB device  3-5 : IR Receiver (Apple Computer, Inc.)
100.0%    USB device  4-1 : BCM2045B2 (Broadcom)
100.0%    USB device  2-5 : Card Reader (Apple)
100.0%    USB device  1-4 : Built-in iSight (Apple Inc.)
100.0%    USB device usb4 : OHCI Host Controller (Linux 2.6.28-15-generic ohci_hcd)
100.0%    USB device usb3 : OHCI Host Controller (Linux 2.6.28-15-generic ohci_hcd)
100.0%    USB device usb2 : EHCI Host Controller (Linux 2.6.28-15-generic ehci_hcd)
100.0%    USB device usb1 : EHCI Host Controller (Linux 2.6.28-15-generic ehci_hcd)


```

---

### Post by ercoppa on 2009-09-20
I have an error:
```
ercoppa@ercoppa-laptop:~/Desktop$ sudo nvidia-settings -a GPU2DClockFreqs=25,0

  Attribute 'GPU2DClockFreqs' (ercoppa-laptop:0.0) assigned value 25,0.
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 69 error_code 2 request_code 139 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
ercoppa@ercoppa-laptop:~/Desktop$ sudo nvidia-settings -a GPU3DClockFreqs=125,0

  Attribute 'GPU3DClockFreqs' (ercoppa-laptop:0.0) assigned value 125,0.
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 69 error_code 2 request_code 139 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

What's wrong? I have an MacBook 5,1.

---

### Post by HighCommander540 on 2009-10-07
Just an FYI, this script helps a lot, but there is now way you can get 6-7 hours if you are using the computer.

If you look in finer detail to what MAC says you can get 7 hours from. It uses pretty much nothing. The tests are for no wireless no bluetooth. And running small *** programs that use no memory.

I can get mine to run for 7 hours on Ubuntu, but only if I have everything turned off and the lib closed...Then I an get like 8 hours or 9. But there is no way even using your computer at its lowest, is going to get you 7 hours. Unless you like to watch your screen saver.

Anyway, everyone should use this script if they have a MacBook or Pro. It helps with power consumption a lot. Plus, if you just let Ubuntu's own ACPI do it's thing it helps a bit.

---

### Post by MadEgg on 2009-10-09
I see the script is deactivating bluetooth... While I do not use bluetooth most of the time and I do have bluetooth disabled on Mac OSX when on battery power, this seems an important limitation.

Isn't there any way the bluez stack could implement a feature to enable/disable bluetooth so the various bluetooth front-ends in KDE and Gnome can disable this from the GUI? Just like wireless using network-manager?

Anyway, as soon as I fix my stability and wifi problems on Kubuntu 9.10 on my MBP 5,5, I'll try some of these things, thanks!

---

### Post by amd-64 on 2009-10-09
I got rid of the stability problem on a 5,3 by recompiling and installing the wl module. 

[http://forum.notebookreview.com/showthread.php?t=418403#wireless](http://forum.notebookreview.com/showthread.php?t=418403#wireless)

---

### Post by N_Nick on 2009-10-11
I'll try these on my 4,1 MBP and post the details.

I don't have any hopes though as my battery life the past couple of months is really messed up, i can only get 2 hours out of a full charge.

---

### Post by crocowhile on 2009-10-22
> **MadEgg said:**
> I see the script is deactivating bluetooth... While I do not use bluetooth most of the time and I do have bluetooth disabled on Mac OSX when on battery power, this seems an important limitation.

Isn't there any way the bluez stack could implement a feature to enable/disable bluetooth so the various bluetooth front-ends in KDE and Gnome can disable this from the GUI? Just like wireless using network-manager?

Anyway, as soon as I fix my stability and wifi problems on Kubuntu 9.10 on my MBP 5,5, I'll try some of these things, thanks!

There are two ways:
1) you create a small bash script that puts BT up and down; you launch the script whenever you need to.

2) Use RFKILL (should be in the package wireless-tools ). Your Kernel needs to have RFKILL either enabled or as module ( sudo modprobe rfkill ).
Once RFKILL is enabled, if you want a GUI applet you can use the one you find here:
[http://www.mail-archive.com/sony-vaio-z-series@lists.launchpad.net/msg00327.html](http://www.mail-archive.com/sony-vaio-z-series@lists.launchpad.net/msg00327.html)

Or else simply issue a "sudo rfkill block bluetooth" or "sudo rfkill unblock bluetooth"

---

### Post by crocowhile on 2009-10-24
I modified the hdparm values in the scripts. I found them way too aggressive and they aren't good for hard disk life. 128 is a more conservative value.

Also, I notice I had some periodic inode errors on the filesystem and obviously that is no good.

---

### Post by rockstar1 on 2009-11-02
Does it work on Macbook 5,1?, or Do I have to try in my Macbook?

---

### Post by faust99 on 2009-11-11
Sorry for el noob questions, but the part of the power saving instructions re. changing the kernel settings in /boot/grub/menu.list is giving me problems. When I opened this file it was empty. I then inserted:

kernel		(hd0,2)/boot/vmlinuz-2.6.28-13-generic root=/dev/sda3 ro quiet splash usbcore.autosuspend=1 hpet=force vga=791

Was this the correct thing to do? It seems like I've make a mistake as the power usage has only gone down minimally (~5W).

---

### Post by crocowhile on 2009-11-11
> **faust99 said:**
> When I opened this file it was empty. I then inserted:That file is not supposed to be empty. You are typing the wrong path or you are using another boot manager, I suppose.

---

### Post by faust99 on 2009-11-11
Yes of course, I'm using refit. Thanks for the hint :)

---

### Post by leemckelvey on 2009-11-16
So has anyone got this working for a macbook 5,1?

if not how can i get some power saving my battery life is way too short.

---

### Post by ringo999 on 2009-11-22
here: 9.10 Macbook Pro 5,5 EFI 1.7

your script works except some issues:

i can only suspend manually from command line, not from gnome panel. 
I guess this is because things are a bit different on Karmic, I looked in the /var/log/pm-suspend.log and found this:

```
/etc/pm/power.d/99-savings: line 74: /sys/bus/pci/drivers/iwl????/0000:??:00.0/power_level: No such file or directory
3337 sudo: /etc/init.d/preload: command not found
3338 sudo: nvclock: command not found
3339 0
3340 
3341 ERROR: The control display is undefined; please run `nvidia-settings
3342        --help` for usage information.
3343 
3344 
3345 ERROR: The control display is undefined; please run `nvidia-settings
3346        --help` for usage information.
3347 
3348 Returned exit code 1.
```Would be nice if you could help me to get this to work, I'm sure there are other users out there with similar problems.

Cheers

// Ringo

---

### Post by hvthao on 2009-11-22
> **ringo999 said:**
> 
[code]/etc/pm/power.d/99-savings: line 74: /sys/bus/pci/drivers/iwl????/0000:??:00.0/power_level: No such file or directory



MBP 13 uses a different wireless card. I think we should delete this line.

> 
3338 sudo: nvclock: command not found


Install package nvclock: sudo apt-get install nvclock

---

### Post by ringo999 on 2009-11-22
actually, I just realized that the problem is laptop-mode related. I'll be happy to report back once I got it to work.

---

### Post by ringo999 on 2009-11-24
so enabling laptop tools it seems like choosing suspend form gnome panel results in screensaver. same for hibernate. any idea why that could be?

Furthermore, is laptop-mode a requirement for 99-savings? Or, why not only use laptop-mode, i saw a lot of config files?

---

### Post by luigi.viggiano on 2009-11-24
Hi crocowhile, and all. 

This post helped me to make the suspend/resume much quicker.
I copied this on my blog, with your permise, linking to here and giving credit to you.

I also found that when I was closing the lid of the laptop the NetworkManager was disconnected, so it was taking additional 8-9 seconds to reconnect on resume. I found that this can be avoided commenting two lines in /usr/lib/pm-utils/sleep.d/55NetworkManager

```

#!/bin/sh
# If we are running NetworkManager, tell it we are going to sleep.
# TODO: Make NetworkManager smarter about how to handle sleep/resume
#       If we are asleep for less time than it takes for TCP to reset a
#       connection, and we are assigned the same IP on resume, we should
#       not break established connections.  Apple can do this, and it is
#       rather nifty.

. "${PM_FUNCTIONS}"

suspend_nm()
{
	# Tell NetworkManager to shut down networking
	dbus_send --print-reply --system                         
		--dest=org.freedesktop.NetworkManager  
		/org/freedesktop/NetworkManager        
		org.freedesktop.NetworkManager.sleep 2>&1 > /dev/null
}

resume_nm()
{
	# Wake up NetworkManager and make it do a new connection
	dbus_send --print-reply --system                        
		--dest=org.freedesktop.NetworkManager 
		/org/freedesktop/NetworkManager       
		org.freedesktop.NetworkManager.wake 2>&1 > /dev/null
}

case "$1" in
	hibernate|suspend)
		**[COLOR=red]#[/COLOR] suspend_nm**
		;;
	thaw|resume)
		**[COLOR=red]#[/COLOR] resume_nm**
		;;
	*) exit $NA
		;;
esac

```

Thanks.
Luigi.

---

### Post by mellofone on 2009-11-25
I have the 13 MBP 5,5 and have just about everything working. I'm having problems with ACPI stuff lagging or stalling at random times. When it happens, anytime I access the battery stats (gkrellm or manually cat), it seems to pause the system for a few seconds. As long as I don't poll anything, the system is normal. 

This was a fresh install of Karmic and so far everything has been great but this. Any ideas?

---

### Post by luigi.viggiano on 2009-11-26
It still happens to my MacBook 5.1 that on resume it may take up to 20-25 seconds, most of the time with a black screen doing nothing, then proceding to do the actual resume in few seconds (3-4).
This doesn't happen if I reboot the system, then I do a suspend/restore, but happens after some suspend/restore cycles. 

I have no idea on what's wrong or how to debug this... what is it doing during the "black screen" time...? maybe grub is involved? maybe EFI / rEFIt?

---

### Post by hachre on 2009-12-23
> **ringo999 said:**
> here: 9.10 Macbook Pro 5,5 EFI 1.7

your script works except some issues:

i can only suspend manually from command line, not from gnome panel. 
I guess this is because things are a bit different on Karmic, I looked in the /var/log/pm-suspend.log and found this:

```
/etc/pm/power.d/99-savings: line 74: /sys/bus/pci/drivers/iwl????/0000:??:00.0/power_level: No such file or directory
3337 sudo: /etc/init.d/preload: command not found
3338 sudo: nvclock: command not found
3339 0
3340 
3341 ERROR: The control display is undefined; please run `nvidia-settings
3342        --help` for usage information.
3343 
3344 
3345 ERROR: The control display is undefined; please run `nvidia-settings
3346        --help` for usage information.
3347 
3348 Returned exit code 1.
```Would be nice if you could help me to get this to work, I'm sure there are other users out there with similar problems.

Cheers

// Ringo

Yea, Karmic is not using the default files described in the original post anymore... So closing the lid or choosing suspend from the gnome panel doesn't execute the changes and doesn't use the new suspend command.

Does anyone know what Gnome calls to go to suspend now?

---

### Post by luigi.viggiano on 2010-01-02
Sometimes it happens to my mbp5.1 that on resume the laptop goes again to suspend. Anyone found this? How to debug it?

---

### Post by hachre on 2010-01-02
> **luigi.viggiano said:**
> Sometimes it happens to my mbp5.1 that on resume the laptop goes again to suspend. Anyone found this? How to debug it?

This is because the MBP sends the lid event both on closing and opening the lid. Sometimes even several times... There's no easy way to fix it. Rather the code that handles the lid events would need to ignore subsequent events for a certain duration.

---

### Post by cocoa117 on 2010-01-24
Regarding to the battery life on MBP 5,5, the information provided on the Apple web site seems to suggests the Adaptive Charging algorithm is done by the system management controller. Does anyone know if this was done on the chipset itself, or it was done through software in OS X? I have checked many tutorials, and no much people mention of this, so I assumed it's done on the chip itself. Anyone knows it differently?

---

### Post by luigi.viggiano on 2010-01-25
> **hachre said:**
> This is because the MBP sends the lid event both on closing and opening the lid. Sometimes even several times... There's no easy way to fix it. Rather the code that handles the lid events would need to ignore subsequent events for a certain duration.

I solved following the steps from [here]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic#Suspend%20&%20Hibernate") :

Suspend works out of the box, but has a bug if you unplug the power adapter before waking (see [gnome-power-manager bug #425411]("https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-power-manager/+bug/425411")).  This is resolved by the following: 

[LIST=1]
[*]Run gconf-editor 
[*]Go to **apps** -> **gnome-power-manager** -> **actions** 
[*]Uncheck the box next to ***event_when_closed_battery***. 
[/LIST]

---

### Post by Silmathoron on 2011-05-01
Hi everyone. I'm using a Macbook Pro 5,3 and I recently installed Natty (the amd64 version). As I didn't get along with Unity, I chose to install Gnome 3.
I'm now trying to improve my battery life but using this script didn't do anything to reduce the power consumption which is around 19 W... and I'm unable to understand where the problem is.
I enabled laptop mode tools without any success either. I also tried to install the script in /etc/acpi and /etc/acpi/events.
Any ideas about what could be wrong ?

Edit : as a matter of fact, I'm also unable to get the keyboard backlight to stay at 0 with pommed, whereas I didn't have any problem when I used Maverick...

---

### Post by nwalkey on 2013-02-25
> **HighCommander540 said:**
> Just an FYI, this script helps a lot,  but there is now way you can get 6-7 hours if you are using the  computer.

If you look in finer detail to what MAC says you can get 7 hours from.  It uses pretty much nothing. The tests are for no wireless no bluetooth.  And running small *** programs that use no memory.

I can get mine to run for 7 hours on Ubuntu, but only if I have  everything turned off and the lib closed...Then I an get like 8 hours or  9. But there is no way even using your computer at its lowest, is going  to get you 7 hours. Unless you like to watch your screen saver.


Lol yes they can get their laptops to run for 7 hours but to do that means you are using the laptop for nothing with the screen barely visible... 4 hours sounds about right to me if you are actually using the computer and have screen brightness turned up a bit.

---

### Post by hachre on 2013-02-25
Maybe on Ubuntu you can't. On OS X I easily get eight hours out of my MacBook Air and that's not by doing nothing...

---

### Post by JJW5432 on 2013-10-08
I have gotten about 5 hours on my Macbook Pro 8,2 running Linux Mint 14. I followed much of this guide: [http://blog.tkassembled.com/364/intel-graphics-on-a-2011-macbook-pro-in-linux/](http://blog.tkassembled.com/364/intel-graphics-on-a-2011-macbook-pro-in-linux/) with some exceptions. I used make menuconfig and made these options built-in:

[LIST]
[*]Processor types and features
[LIST]
[*]EFI stub support
[*]Built-in kernel command line (set to ```
root=UID=INSERTUIDHERE ro quiet spalsh
```, replacing INSERTUIDHERE with the UID of your root partition, which can be obtained with  ```
[COLOR=#373737][FONT=Courier 10 Pitch]blkid -o value "$(df -P / | tail -1 | cut -d ' ' -f 1)" | sed '1q;'[/FONT][/COLOR]
``` in terminal
[/LIST]

[*]Device Drivers
[LIST]
[*]&#8203;Graphics support
[LIST]
[*]&#8203;Direct Rendering Manager
[*]Intel I810
[*]Intel 8xx/9xx/G2x/G4x/HD Graphics
[/LIST]
[/LIST]
[/LIST]
&#8203;Later on in the guide, when copying the grub extensions, I had to copy them to a different directory so my EFI partition looks like this:
.
&#9500;&#9472;&#9472; BOOTLOG
&#9492;&#9472;&#9472; EFI
    &#9500;&#9472;&#9472; APPLE
    &#9474;   &#9500;&#9472;&#9472; EXTENSIONS
    &#9474;   &#9474;   &#9492;&#9472;&#9472; Firmware.scap
    &#9474;   &#9492;&#9472;&#9472; FIRMWARE
    &#9474;       &#9500;&#9472;&#9472; PortMicro.bin
    &#9474;       &#9492;&#9472;&#9472; ThorUtil.efi
    &#9492;&#9472;&#9472; BOOT
        &#9500;&#9472;&#9472; BOOTX64.EFI
        &#9500;&#9472;&#9472; grub.cfg
        &#9492;&#9472;&#9472; x86_64-efi
            &#9500;&#9472;&#9472; GRUB EXTENSIONS HERE

My grub.cfg file is also notably different:

```
#grub.cfg
menuentry 'Linux Mint 15 Cinnamon 64-bit, 3.8.8+igd (/dev/sda7)' --class linuxmint --class gnu-linux --class gnu --class os {
	set debug=fb
    	insmod efi_uga	
	insmod gzio
	insmod part_gpt
	insmod ext2


	set gfxpayload=keep


	outb 0x728 1 # Switch select
 	outb 0x710 2 # Switch display
	outb 0x740 2 # Switch DDC
	outb 0x750 0 # Power down discrete graphics	


	set root='hd0,gpt7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7 INSERTUIDHERE
	else
	  search --no-floppy --fs-uuid --set=root INSERTUIDHERE
	fi
	linux	/boot/vmlinuz-3.8.8+igd root=UUID=f7048b3e-bff5-45c6-82ee-a7090adcdc57 ro splash $vt_handoff
		i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0 \
        	i915.i915_enable_rc6=1 acpi_backlight=vendor vt_handoff=7 splash


	initrd	/boot/initrd.img-3.8.8+igd
}

```

If you're copying and pasting be sure to replace the INSERTUIDHEREs with the UID of your root partition as explained above.



Also note that some people cannot see the full first 2 lines of disable-ati.c, which are:
```

[COLOR=#000000][FONT=monospace]#include [/FONT][/COLOR][FONT=monospace]<stdio.h>[/FONT][COLOR=#000000][FONT=monospace][/FONT][/COLOR][COLOR=#000000][FONT=monospace]#include [/FONT][/COLOR][FONT=monospace]<sys/io.h>[/FONT][COLOR=#000000][FONT=monospace][/FONT][/COLOR]
```

Good luck, if you get it right you should get huge power saving gains.

---

### Post by JJW5432 on 2013-10-08
I have gotten about 5 hours on my Macbook Pro 8,2 running Linux Mint 14. I followed much of this guide: [http://blog.tkassembled.com/364/intel-graphics-on-a-2011-macbook-pro-in-linux/](http://blog.tkassembled.com/364/intel-graphics-on-a-2011-macbook-pro-in-linux/) in order to boot in EFI mode and choose only the integrated graphics card, which uses much less power than the dedicated one. Otherwise, Linux only uses the dedicated and doesn't switch between them on demand like OSX does, leading to the difference between battery life. However, I made some changes:
When choosing kenrel options, I used make menuconfig and made these options built-in:

[LIST]
[*]Processor types and features
[LIST]
[*]EFI stub support
[*]Built-in kernel command line set to ```
root=UID=INSERTUIDHERE ro quiet spalsh
```, replacing INSERTUIDHERE with the UID of your root partition, which can be obtained with  ```
[COLOR=#373737][FONT=Courier 10 Pitch]blkid -o value "$(df -P / | tail -1 | cut -d ' ' -f 1)" | sed '1q;'[/FONT][/COLOR]
``` in terminal
[/LIST]

[*]Device Drivers
[LIST]
[*]&#8203;Graphics support
[LIST]
[*]&#8203;Direct Rendering Manager
[*]Intel I810
[*]Intel 8xx/9xx/G2x/G4x/HD Graphics
[/LIST]
[/LIST]
[/LIST]
&#8203;Later on in the guide, when copying the grub extensions, I had to copy them to a different directory  name x86_64-efi so my EFI partition looks like this:
```
.
&#9500;&#9472;&#9472; BOOTLOG
&#9492;&#9472;&#9472; EFI
    &#9500;&#9472;&#9472; APPLE
    &#9474;   &#9500;&#9472;&#9472; EXTENSIONS
    &#9474;   &#9474;   &#9492;&#9472;&#9472; Firmware.scap
    &#9474;   &#9492;&#9472;&#9472; FIRMWARE
    &#9474;       &#9500;&#9472;&#9472; PortMicro.bin
    &#9474;       &#9492;&#9472;&#9472; ThorUtil.efi
    &#9492;&#9472;&#9472; BOOT
        &#9500;&#9472;&#9472; BOOTX64.EFI
        &#9500;&#9472;&#9472; grub.cfg
        &#9492;&#9472;&#9472; x86_64-efi
            &#9500;&#9472;&#9472; GRUB EXTENSIONS HERE

```
My grub.cfg file is also notably different:

```
#grub.cfg
menuentry 'Linux Mint 15 Cinnamon 64-bit, 3.8.8+igd (/dev/sda7)' --class linuxmint --class gnu-linux --class gnu --class os {
    set debug=fb
        insmod efi_uga    
    insmod gzio
    insmod part_gpt
    insmod ext2


    set gfxpayload=keep


    outb 0x728 1 # Switch select
     outb 0x710 2 # Switch display
    outb 0x740 2 # Switch DDC
    outb 0x750 0 # Power down discrete graphics    


    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  INSERTUIDHERE
    else
      search --no-floppy --fs-uuid --set=root INSERTUIDHERE
    f i
    linux    /boot/vmlinuz-3.8.8+igd root=UUID=INSERTUIDHERE ro splash $vt_handoff
        i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0 \
            i915.i915_enable_rc6=1 acpi_backlight=vendor vt_handoff=7 splash


    initrd    /boot/initrd.img-3.8.8+igd
}

```

If you're copying and pasting be sure to replace the INSERTUIDHEREs with the UID of your root partition as explained above.



Also note that some people cannot see the full first 2 lines of disable-ati.c, which are:
```

[COLOR=#000000][FONT=monospace]#include [/FONT][/COLOR][FONT=monospace]<stdio.h>
[/FONT][COLOR=#000000][FONT=monospace]#include [/FONT][/COLOR][FONT=monospace]<sys/io.h>[/FONT]
```

Good luck, if you get it right you should get huge power saving gains.

---

