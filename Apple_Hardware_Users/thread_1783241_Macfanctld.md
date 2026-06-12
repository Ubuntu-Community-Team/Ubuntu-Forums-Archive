---
title: "Macfanctld?"
date: 2011-06-15
forum: Apple Hardware Users
---

### Post by parananon on 2011-06-15
Does anyone know how to install macfanctld as mentioned in the Macbook Air Ubuntu guide? I can't seem to find it even after adding the Mactel repository.

Thanks in advance!

---

### Post by mbarvian on 2011-06-15
It's not available for Natty, which sucks. :(

---

### Post by SwedishWings on 2011-08-17
> **mbarvian said:**
> It's not available for Natty, which sucks. :(

Sorry for the delay of a Natty release. I have made one which, if the build goes well, should be available in a few hours via mactel PPA.

/Mike

---

### Post by dejlig on 2011-08-27
Hi, new to linux and have installed Macfanctld...thanks by the way.  I saw that the software center mentioned this should be run in the terminal.  I opened the terminal and typed macfanctld and hit enter.  Nothing happened except a new command line popped up.  Is there something else I need to do?  Thank you.

left in the first couple lines so you could see my build #.

steve@steve-MacBook:~$ sudo dmidecode -s system-product-name
[sudo] password for steve: 
MacBook4,1
steve@steve-MacBook:~$ alsamixer
steve@steve-MacBook:~$ sudo alsactl store
[sudo] password for steve: 
steve@steve-MacBook:~$ macfanctld
steve@steve-MacBook:~$ macfanctld
steve@steve-MacBook:~$

---

### Post by SwedishWings on 2011-08-28
> **dejlig said:**
> Hi, new to linux and have installed Macfanctld...thanks by the way.  I saw that the software center mentioned this should be run in the terminal.  I opened the terminal and typed macfanctld and hit enter.  Nothing happened except a new command line popped up.  Is there something else I need to do?  Thank you.

No, once installed it will start at boot an runs in the background.

If your MacBook feels too hot after installation, check the man page for macfanctld. 

I have no idea why it say so in Software Center.

/Mike

---

### Post by dejlig on 2011-08-28
Thanks Mike!  And I might owe you and your friends a special thanks.  Been trying to install Ubuntu on my Macbook since Hardy Heron but kept running into too many issues. I imagine the work your PPA has done has made 11.04 run smoothly on my mac.  

The fan seems to be working much better now!

tack så mycket! 
Steve

---

### Post by SwedishWings on 2011-09-01
> **dejlig said:**
> Thanks Mike!  And I might owe you and your friends a special thanks.  Been trying to install Ubuntu on my Macbook since Hardy Heron but kept running into too many issues. I imagine the work your PPA has done has made 11.04 run smoothly on my mac.  

The fan seems to be working much better now!

tack så mycket! 
Steve

Kul att det funkar =)

---

### Post by oscarmax on 2011-09-07
Installed the Macfanctld on my macbook air 3.2 with the PPA for narwal. After that the fan started spinn up and down in a loop.
From lowest rpm to highest, it sounded like.

How can I fix this?

---

### Post by SwedishWings on 2011-09-15
> **oscarmax said:**
> Installed the Macfanctld on my macbook air 3.2 with the PPA for narwal. After that the fan started spinn up and down in a loop.
From lowest rpm to highest, it sounded like.

How can I fix this?

Have not seen that before. Can you provide a detailed log?

Edit /etc/macfanctl.conf and change to

```
log_level: 2
```

let it run for a while and post (in an attachment preferably) the log in /var/log/macfanctl.log

Please also attach /etc/macfanctl.conf

/Mike

---

### Post by dfacto on 2011-09-18
Running powertop I see macfanctld has about twice as much power consumption as other daemons.  I saw the sleep is hardcoded as 5sec in macfanctl.c.  It might be nice to have that be a parameter in the etc conf.

More generally, is there a way to make the daemon more energy efficient?  I am not sure what tricks work best.  Perhaps not explicitly calling fflush and things like that...

---

### Post by SwedishWings on 2011-09-18
> **dfacto said:**
> Running powertop I see macfanctld has about twice as much power consumption as other daemons.  I saw the sleep is hardcoded as 5sec in macfanctl.c.  It might be nice to have that be a parameter in the etc conf.

More generally, is there a way to make the daemon more energy efficient?  I am not sure what tricks work best.  Perhaps not explicitly calling fflush and things like that...

That is not the case on my machine:

```
Top causes for wakeups:
  31.1% (104.9)   [extra timer interrupt]
  27.9% ( 94.0)   [ohci_hcd:usb4, nvidia] <interrupt>
  10.0% ( 33.6)   USB device  4-2 : PS/2+USB Mouse (A4Tech)
   8.6% ( 28.9)   [acpi] <interrupt>
   5.2% ( 17.7)   kworker/0:0
   3.4% ( 11.3)   [kernel scheduler] Load balancing tick
   3.0% ( 10.2)   [ahci] <interrupt>
   2.9% (  9.9)   compiz
   2.9% (  9.9)   ubuntuone-syncd
   1.5% (  5.0)   syndaemon
   0.6% (  1.9)   gnome-terminal
   0.3% (  1.1)   [Rescheduling interrupts] <kernel IPI>
   0.3% (  1.0)   [kernel core] nv_kern_rc_timer (nv_kern_rc_timer)
   0.2% (  0.8)   [kernel core] hrtimer_start (tick_sched_timer)
   0.2% (  0.8)   upowerd
   0.2% (  0.8)   hald
   0.2% (  0.7)   [eth0] <interrupt>
   0.1% (  0.5)   udisks-daemon
   0.1% (  0.5)   hald-addon-stor
   0.1% (  0.4)   rtkit-daemon
   0.1% (  0.3)   [TLB shootdowns] <kernel IPI>
   0.1% (  0.3)   gnome-settings-
   0.1% (  0.3)   gpg-agent
   0.1% (  0.2)   [Function call interrupts] <kernel IPI>
   0.1% (  0.2)   kworker/0:2
   0.1% (  0.2)   unity-panel-ser
   0.1% (  0.2)   update-notifier
   0.1% (  0.2)   unity-applicati
   0.1% (  0.2)   [kernel core] dev_watchdog (dev_watchdog)
   **0.1% (  0.2)   macfanctld**
   0.0% (  0.1)   irqbalance
   0.0% (  0.1)   cron
   0.0% (  0.1)   [kernel core] cfq_arm_slice_timer (cfq_idle_slice_timer)
   0.0% (  0.1)   gnome-power-man
   0.0% (  0.1)   Xorg
   0.0% (  0.1)   nautilus
   0.0% (  0.1)   rsyslogd
   0.0% (  0.1)   ssh-agent
   0.0% (  0.1)   flush-8:0
   0.0% (  0.1)   USB device  3-6 : Apple Internal Keyboard / Trackpad (Apple, Inc.)


```

I think there has to be another reason why it eats power for you. Have you checked the log?

Regards,
Mike

---

### Post by dfacto on 2011-09-19
Meh, it is on mine.  Its always in the top 10.  Given what it does, this is way too high.  What version of powertop is that from?  Mine is 1.97 (on the new mac book air).

```


Power est.      Usage       Events/s    Category       Description
  1.84 W    100.0%                      Device         USB device: FaceTime Camera (Built-in) (Apple Inc.)
  1.05 W     40.0%                      Device         Display backlight
  756 mW     22.4 ms/s       0.0        Process        compiz --replace
  695 mW    530.6 pkts/s                Device         Network interface: wlan0 (brcmsmac)
  497 mW    100.0%                      Device         Radio device: brcmsmac
  450 mW     13.3 ms/s       0.0        Process        /usr/lib/unity/unity-panel-service
  442 mW     13.1 ms/s       0.0        Process        //bin/dbus-daemon --fork --print-pid 8 --print-address 10 --session
  331 mW     40.0%                      Device         Display backlight
  214 mW      6.4 ms/s       0.0        Process        /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
  179 mW      5.3 ms/s       0.0        Process        /usr/sbin/macfanctld
  101 mW      3.0 ms/s       0.0        Process        /usr/bin/python /usr/bin/gm-notify
 81.3 mW      2.4 ms/s       0.0        Process        /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
 67.1 mW      2.0 ms/s       0.0        Process        /usr/bin/dispad
 61.1 mW      1.8 ms/s       0.0        Timer          hrtimer_wakeup
 54.3 mW      1.6 ms/s       0.0        Process        /usr/bin/python /usr/bin/gwibber-service
 41.0 mW      1.2 ms/s       0.0        Interrupt      [46] i915
 38.9 mW      1.2 ms/s       0.0        Timer          tick_sched_timer
 35.4 mW      1.1 ms/s       0.0        Timer          delayed_work_timer_fn
 33.1 mW      1.0 ms/s       0.0        Process        gnome-terminal
 30.5 mW      0.9 ms/s       0.0        Interrupt      [6] tasklet(softirq)
 26.4 mW      0.8 ms/s       0.0        kWork          do_dbs_timer
 19.8 mW    587.6 µs/s       0.0        Interrupt      [7] sched(softirq)
 17.3 mW    513.8 µs/s       0.0        Process        [kworker/1:0]
 15.9 mW    472.5 µs/s       0.0        Process        [kworker/3:1]
 14.1 mW    419.0 µs/s       0.0        Interrupt      [1] timer(softirq)
 13.4 mW    396.7 µs/s       0.0        Process        powertop -?
 12.7 mW    376.9 µs/s       0.0        Process        [kworker/0:1]
 12.6 mW    374.8 µs/s       0.0        Process        /usr/bin/python /usr/share/system-config-printer/applet.py
 7.87 mW    233.4 µs/s       0.0        Interrupt      [9] RCU(softirq)
 7.75 mW    229.9 µs/s       0.0        Process        [kworker/u:1]
 7.72 mW    229.1 µs/s       0.0        Process        [kworker/2:1]
 7.69 mW    228.2 µs/s       0.0        Interrupt      [17] brcmsmac
 6.90 mW    204.7 µs/s       0.0        Process        /usr/sbin/irqbalance
 5.93 mW    176.0 µs/s       0.0        Interrupt      [22] ehci_hcd:usb2
 5.39 mW    159.9 µs/s       0.0        Process        /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 5.26 mW    156.2 µs/s       0.0        Timer          wl_timer
 4.95 mW    146.9 µs/s       0.0        kWork          ieee80211_iface_work
 4.41 mW    130.8 µs/s       0.0        Process        /usr/bin/python /usr/bin/indicator-weather
 3.33 mW     98.8 µs/s       0.0        Process        [usb-storage]
 3.32 mW     98.5 µs/s       0.0        Process        udisks-daemon: polling /dev/sdb

```

---

### Post by SwedishWings on 2011-09-19
> **dfacto said:**
> Meh, it is on mine.  Its always in the top 10.  Given what it does, this is way too high.  What version of powertop is that from?  Mine is 1.97 (on the new mac book air).

I run Ubuntu 11.04 (32bit) and have PowertTOP version 1.13 from the Ubuntu repos. Were did you get that version?

I'm not sure why it shows up so high on your list. Have you checked the log (/var/log/macfanctl.log) for errors?

---

### Post by dfacto on 2011-09-19
oops sorry  forgot to say: yes the log was the first thing i checked. :)  im on oneiric with kernel 3.0.0-11. PowerTOP 1.97 beta 1 is from the repos.

here is the log
```

Using parameters:
    temp_avg_floor: 45
    temp_avg_ceiling: 55
    temp_TC0P_floor: 50
    temp_TC0P_ceiling: 58
    temp_TG0P_floor: 50
    temp_TG0P_ceiling: 58
    fan_min: 2000
    exclude: temp13_input temp14_input temp15_input
    log_level: 0
Found 1 fan.
Found 25 sensors:
     1: TB0T - Battery TS_MAX Temp
     2: TB1T - Battery TS1 Temp
     3: TB2T - Battery TS2 Temp
     4: TC0C - ?
     5: TC0D - CPU 0 Die Temp
     6: TC0E - ?
     7: TC0F - ?
     8: TC0P - CPU 0 Proximity Temp
     9: TC1C - ?
    10: TC2C - ?
    11: TCGC - ?
    12: TCSA - ?
    13: TH0F - ?    ***EXCLUDED***
    14: TH0J - ?    ***EXCLUDED***
    15: TH0O - ?    ***EXCLUDED***
    16: TH0o - ?
    17: THSP - ?
    18: TM0P - ?
    19: TPCD - ?
    20: Ta0P - ?
    21: Th1H - ?
    22: Tm0P - Battery Charger Proximity Temp
    23: Tm1P - ?
    24: Ts0P - Palm Rest Temp
    25: Ts0S - ?
Error: Can't read  /sys/devices/platform/applesmc.768/temp22_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp11_input

```

Since there is no recurring error, I interpret the two errors as being a one time read issue.  Here is the output from sensors:
```

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +50.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +49.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +47.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   2005 RPM  (min = 2000 RPM)
TB0T:         +19.5°C  
TB1T:         +19.2°C  
TB2T:         +19.5°C  
TC0C:         +48.8°C  
TC0D:         +42.2°C  
TC0E:         +48.5°C  
TC0F:         +49.5°C  
TC0P:         +39.0°C  
TC1C:         +49.0°C  
TC2C:         +47.0°C  
TCGC:         +48.0°C  
TCSA:         +45.0°C  
TH0F:        +249.2°C  
TH0J:        +249.0°C  
TH0O:        +249.0°C  
TH0o:         +28.0°C  
THSP:         +27.2°C  
TM0P:         +34.2°C  
TPCD:         +44.0°C  
Ta0P:         +34.5°C  
Th1H:         +23.8°C  
Tm0P:         +28.0°C  
Tm1P:         +32.8°C  
Ts0P:         +21.0°C  

```

and ls of sys:

```

jvdillon@gerty:/sys/devices/platform/applesmc.768$ ll
total 0
lrwxrwxrwx 1 root root    0 2011-09-18 11:53 driver -> ../../../bus/platform/drivers/applesmc
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 fan1_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 fan1_label
-rw-r--r-- 1 root root 4.0K 2011-09-19 07:56 fan1_manual
-r--r--r-- 1 root root 4.0K 2011-09-19 07:56 fan1_max
-rw-r--r-- 1 root root 4.0K 2011-09-19 07:56 fan1_min
-rw-r--r-- 1 root root 4.0K 2011-09-19 07:56 fan1_output
-r--r--r-- 1 root root 4.0K 2011-09-19 07:56 fan1_safe
drwxr-xr-x 3 root root    0 2011-09-18 11:53 hwmon
-rw-r--r-- 1 root root 4.0K 2011-09-19 07:56 key_at_index
-r--r--r-- 1 root root 4.0K 2011-09-19 07:56 key_at_index_data
-r--r--r-- 1 root root 4.0K 2011-09-19 07:56 key_at_index_data_length
-r--r--r-- 1 root root 4.0K 2011-09-19 07:56 key_at_index_name
-r--r--r-- 1 root root 4.0K 2011-09-19 07:56 key_at_index_type
-r--r--r-- 1 root root 4.0K 2011-09-19 07:56 key_count
drwxr-xr-x 3 root root    0 2011-09-18 11:53 leds
-r--r--r-- 1 root root 4.0K 2011-09-19 07:56 light
-r--r--r-- 1 root root 4.0K 2011-09-19 07:56 modalias
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 name
drwxr-xr-x 2 root root    0 2011-09-18 12:54 power
lrwxrwxrwx 1 root root    0 2011-09-18 11:53 subsystem -> ../../../bus/platform
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp10_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp10_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp11_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp11_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp12_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp12_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp13_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp13_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp14_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp14_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp15_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp15_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp16_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp16_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp17_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp17_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp18_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp18_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp19_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp19_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp1_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp1_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp20_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp20_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp21_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp21_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp22_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp22_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp23_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp23_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp24_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp24_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp25_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp25_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp2_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp2_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp3_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp3_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp4_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp4_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp5_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp5_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp6_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp6_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp7_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp7_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp8_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp8_label
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp9_input
-r--r--r-- 1 root root 4.0K 2011-09-18 11:53 temp9_label
-rw-r--r-- 1 root root 4.0K 2011-09-18 11:53 uevent

```

and also
```


jvdillon@gerty:/sys/devices/platform/applesmc.768$ for l in *_label;do printf "%s\t%s\n" $l `cat $l`;done|sort -n
fan1_label	Exhaust
temp10_label	TC2C
temp11_label	TCGC
temp12_label	TCSA
temp13_label	TH0F
temp14_label	TH0J
temp15_label	TH0O
temp16_label	TH0o
temp17_label	THSP
temp18_label	TM0P
temp19_label	TPCD
temp1_label	TB0T
temp20_label	Ta0P
temp21_label	Th1H
temp22_label	Tm0P
temp23_label	Tm1P
temp24_label	Ts0P
temp25_label	Ts0S
temp2_label	TB1T
temp3_label	TB2T
temp4_label	TC0C
temp5_label	TC0D
temp6_label	TC0E
temp7_label	TC0F
temp8_label	TC0P
temp9_label	TC1C

```

---

### Post by SwedishWings on 2011-09-19
Thanks for your input. 

I have really no idea why macfanctld behaves like that on Oneiric. I had no time to install Oneiric as of yet, but will to get macfanctld in the mactel repo on time. 

Until then, i'm afraid you have to live with it :(

---

### Post by dfacto on 2011-09-19
No worries--thanks for taking the time to write this program and look into the potential issue.  *Much* appreciated! :-D  I'd like to keep using your code--I think its high quality and can run native.

Yeah--these are always the worst kind of bugs to track down.  For all we know the scheduler is to blame. :-/

---

### Post by rsulli55 on 2011-10-01
I know this isn't an answer to your problem, but I was wondering where you got the macfanctld package for oneiric?  I just installed beta 2 and I can't find it anywhere.

Thanks!

---

