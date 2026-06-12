---
title: "Laptop Mode Troubles"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by deez on 2007-10-20
I'm trying to get the laptop mode to work.  

When I do this:

cat /proc/sys/vm/laptop_mode

I get an output of 

0.

I tried to do this:

sudo /etc/init.d/laptop-mode start

but I still end up with a value of 0.  

Any thoughts?

---

### Post by deez on 2007-10-20
I've just installed PowerTop and it tells me I'm using an average of 19 W and the CPU is waking up 44000 times each second.  I don't know much, but that seems like a lot.  

Cheers

---

### Post by deez on 2007-10-20
Can anyone give me some help on this one?

---

### Post by mozillar on 2007-10-20
Hi, 

I searched for the laptop mode forum posts that helped me get this working in the past, but I couldn't quickly find them. Luckily, I keep a log of what changes I make to my system. I assume you have not yet enabled laptop mode in acpi-support.

I run xubuntu gutsy and use mousepad as my text editor. You may need to replace "mousepad" with the name of your text editor, likely "gedit". 
In terminal:

cd /etc/default/
sudo cp acpi-support acpi-support.old
sudo mousepad acpi-support
  set ENABLE_LAPTOP_MODE=true, was false

sudo cp /etc/laptop-mode/laptop-mode.conf /etc/laptop-mode/laptop-mode.old
sudo mousepad /etc/laptop-mode/laptop-mode.conf
(make these 8 changes and save the file)
  set ENABLE_LAPTOP_MODE_ON_AC=1, was 0
  set LM_AC_HD_IDLE_TIMEOUT_SECONDS=600, was 20
  set LM_BATT_HD_IDLE_TIMEOUT_SECONDS=300, was 20
  set NOLM_HD_IDLE_TIMEOUT_SECONDS=600, was 7200
  set CONTROL_CPU_FREQUENCY=1, was 0
  set BATT_CPU_GOVERNOR=powersave, was ondemand
  set NOLM_AC_CPU_GOVERNOR=ondemand, was performance
  set CONTROL_NOATIME=1, was 0

sudo /etc/init.d/acpi-support stop
sudo /etc/init.d/acpi-support start
sudo /etc/init.d/laptop-mode reload

sudo mousepad /etc/acpi/ac.d/20-wireless_power.sh
(paste these 5 lines below in this new shell script file)
#!/bin/bash
# Change the wireless power mode to AC.
#   This works for ipw3945, not sure about other chipsets
#   Make sure eth1 is your wireless.
/sbin/iwpriv eth1 set_power 6

sudo chmod 755 /etc/acpi/ac.d/20-wireless_power.sh

sudo mousepad /etc/acpi/battery.d/20-wireless_power.sh
(paste these 4 lines below in this new shell script file)
#!/bin/bash
# Change the wireless power mode to Battery.
# I used to use 7 but power top recommends 5
/sbin/iwpriv eth1 set_power 5

sudo chmod 755 /etc/acpi/battery.d/20-wireless_power.sh

sudo mousepad /etc/acpi/ac.d/10-vm_settings.sh
(paste these 7 lines below in this new shell script file)
#!/bin/bash
# Tweak virtual memory for running on AC.
echo 60 > /proc/sys/vm/swappiness
echo 3000 > /proc/sys/vm/dirty_expire_centisecs
echo 500  > /proc/sys/vm/dirty_writeback_centisecs
echo 10   > /proc/sys/vm/dirty_background_ratio
echo 40   > /proc/sys/vm/dirty_ratio

sudo chmod 755 /etc/acpi/ac.d/10-vm_settings.sh

sudo mousepad /etc/acpi/battery.d/10-vm_settings.sh
(paste these 8 lines below in this new shell script file)
#!/bin/bash
# Tweak virtual memory to conserve power when running on batteries.
# Used to use 0 for dirty_writeback_centisecs but powertop recommends 1500
echo 10 > /proc/sys/vm/swappiness
echo 0 > /proc/sys/vm/dirty_expire_centisecs
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 60 > /proc/sys/vm/dirty_background_ratio
echo 95 > /proc/sys/vm/dirty_ratio

sudo chmod 755 /etc/acpi/battery.d/10-vm_settings.sh

sudo cp /etc/fstab /etc/fstab_backup
sudo vi /etc/fstab
  added ",noatime" after remount-ro entry for sda1 drive
  use mount to confirm change after reboot

sudo update-rc.d laptop-mode multiuser

Reboot and check values on AC & battery by these commands in terminal:
```
/sbin/iwpriv eth1 get_power
cat /proc/sys/vm/laptop_mode
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```


I've used the above changes successfully on Edgy & Feisty in the past. Under Gutsy I've noticed some issues with laptop mode starting consistently if I boot on battery. It works correctly if I go from AC to battery or vice versa. Following powertop's advice, I was able to get as low as 12 W with 13 wakeups per second. Amazing.

Hope this helps

---

### Post by deez on 2007-10-20
Thanks so much for all of that.  I went through the steps you provided.  I didn't know what I was doing, but everything went through, so I guess that's great.  After rebooting here's what I get to those commands:

~$ /sbin/iwpriv eth1 get_power
eth1      get_power:Power save level: 6 (AC) OFF

cat /proc/sys/vm/laptop_mode
2

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_gover nor
cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_gover: No such file or directory
cat: nor: No such file or directory


That last one doesn't sound too good.  

What do you think?

I'm getting about the same battery life as before, 50 minutes.

Any other fixes?

Thanks again.

---

### Post by mozillar on 2007-10-21
D'oh, my bad. The command should have read "governor" as in
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
On battery, we want that to return "powersave". 

------------------------------------

As for the eth1 power, when on battery,  "/sbin/iwpriv eth1 get_power" should return
"eth1      get_power:Power save level: 5 (Timeout 25ms, Period 1000ms)"

What happens if you run this command:

```
sudo /sbin/iwpriv eth1 set_power 5
```

Does " /sbin/iwpriv eth1 get_power" now return level 5?

------------------------------------

The "cat /proc/sys/vm/laptop_mode" returned 2, thats good. Anything but 0 means its active.

------------------------------------

Even without all these tweaks, your battery life should be better than 50 minutes. These tweaks can help extend it further. But it sounds like there still is some bigger issue that's draining the battery or problem with the battery.

Curious what does powertop report for top causes of wakeups? 
Did powertop suggest any additional changes to make?

---

### Post by deez on 2007-10-21
This: cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor (in the terminal the space is not there, not sure why it's here now)

gives me: no such file or directory

*****

sudo /sbin/iwpriv eth1 set_power 5

Level 6

*****

As for PowerTop...

Top causes for wake-up:

Top causes for wakeups:
  39.8% (165.2)       <interrupt> : ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3,
  28.9% (119.7)       firefox-bin : schedule_timeout (process_timeout) 
   9.3% ( 38.4)              Xorg : do_setitimer (it_real_fn) 
   7.6% ( 31.7)            python : schedule_timeout (process_timeout) 
   6.0% ( 25.0)       firefox-bin : futex_wait (hrtimer_wakeup) 
   3.3% ( 13.7)       compiz.real : schedule_timeout (process_timeout) 

It suggests:
USB autosuspend
enable AC9something-or-other powersave

and that's all. 

Any ideas what could the big problem be?  The battery itself?

Cheers

---

### Post by mozillar on 2007-10-21
Given the no such file or directory, it makes me think CPUFREQ is not enabled in your kernel, as noted here: [http://www.lesswatts.org/tips/cpu.php](http://www.lesswatts.org/tips/cpu.php)
I would search for CPUFREQ posts to see how to enable it. I bet your cpu is going full speed 100% of the time.

Assuming eth1 is your wifi card, I'm stumped as to why it doesn't take the set power 5.
Which wifi card do you have? 
If not a ipw2200 or ipw3945, you would use the 
"iwconfig ethX power" command to enable power saving as noted here: [http://linuxpowertop.org/known.php#ipw3945](http://linuxpowertop.org/known.php#ipw3945)
You'll have to research the best options to use in that case.

Other potential savings:
LessWatts also had a tip on disabling bluetooth if not used [http://www.lesswatts.org/tips/wireless.php](http://www.lesswatts.org/tips/wireless.php)

Powertop suggests NoDRI option for video, which helped me
[http://linuxpowertop.org/faq.php](http://linuxpowertop.org/faq.php)

I still need to figure out how to disable USB in grub, disabling thru powertop reduced wakeups for me.

Curious, did this battery issue start after installing Gutsy?

Hope some(or all) of these tips yield some noticeable savings for you.

---

