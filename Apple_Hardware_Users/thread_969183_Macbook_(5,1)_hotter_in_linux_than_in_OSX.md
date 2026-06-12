---
title: "Macbook (5,1) hotter in linux than in OSX"
date: 2008-11-03
forum: Apple Hardware Users
---

### Post by druggo on 2008-11-03
Hi

I was noticing that when in linux, my system runs way much hotter than in OSX. 

It may be related to this bug? [#262550]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550") 

After some investigation, i noticed that my fans RPM didn't change during high load, it always stayed at 2000RPM, So i managed to change that to 3000RPM by using 

```
# echo 3000 > /sys/devices/platform/applesmc.768/fan1_output
```

have anyone else run into the same problem??

---

### Post by lynks on 2008-11-03
I have the same problem :(

> 
root@macbook:/home/lynks# echo 3000 > /sys/devices/platform/applesmc.768/fan1_output 
root@macbook:/home/lynks# cat /sys/devices/platform/applesmc.768/fan1_output
2000


---

### Post by kosumi68 on 2008-11-03
druggo, lynks,

those two lines explain a lot of problems. Do you have the applesmc-dkms package installed? Please start from there, and if the problem exists, I will help you solve this.

---

### Post by lynks on 2008-11-03
I have installed this packages from ppa mactel support:

> 
lynks@macbook:~$ dpkg -l | grep gnome-power
ii  gnome-power-manager                       2.24.0-1mactel3                       frontend for gnome-powermanager
lynks@macbook:~$ dpkg -l | grep dkms
ii  applesmc-dkms                             0.12.1                                Supplementary applesmc support
ii  bcm5974-dkms                              1.1.0                                 Apple USB BCM5974 Multitouch trackpad suppor
ii  dkms                                      2.0.20.4-0ubuntu2                     Dynamic Kernel Module Support Framework
ii  hid-dkms                                  0.10.2                                Supplementary hid support
ii  usbhid-dkms                               0.10.1                                Supplementary usbhid support



thanks for all :p

---

### Post by kosumi68 on 2008-11-03
Great, then we know what we're looking at. As I understand it, it does not work to set the fan speed manually. Is it always in conjunction with this operation that you get the applesmc error in dmesg?

---

### Post by druggo on 2008-11-03
i managed to change my fan speed manually now, by just echoing the desired RPM to fan1_min, **not fan1_output** sorry, my bad!, i am using running the latest applesmc-dkms.

the problem as I see it is that the kernel doesn't adjust the fan when the load increase..

when i changed to fan speed and then spammed sensors i got this in dmesg it only happens when i get a read error from a temp monitor (it's not frequent):

```
[ 9793.138289] applesmc: wait status failed: 5 != 11

```

---

### Post by kosumi68 on 2008-11-03
OK, not frequent here is nothing to worry about.

Regarding the fans, I realized the fan1_output glitch, but here is another thing:
```

intrepid>echo 1 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_manual
1
intrepid>echo 3000 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
3000
intrepid>cat /sys/devices/platform/applesmc.768/fan1_output 
2500

```
whereas
```

intrepid>echo 0 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_manual
0
intrepid>echo 3000 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
3000
intrepid>cat /sys/devices/platform/applesmc.768/fan1_output 
3000

```

With no software fan control, I get the feeling one wants that manual value set to zero. What do you think? Any correlation to what you are experiencing?

---

### Post by druggo on 2008-11-03
and for reference heres my output from the same commands as lynks posted.

> 
root@toben:~# dpkg -l | grep gnome-power

ii  gnome-power-manager                       2.24.0-1mactel3                       frontend for gnome-powermanager


root@toben:~# dpkg -l | grep dkms
ii  applesmc-dkms                             0.12.1                                Supplementary applesmc support
ii  bcm5974-dkms                              1.1.0                                 Apple USB BCM5974 Multitouch trackpad suppor
ii  dkms                                      2.0.20.4-0ubuntu2                     Dynamic Kernel Module Support Framework
ii  usbhid-dkms                               0.10.1                                Supplementary usbhid support



---

### Post by druggo on 2008-11-03
yeah to be able to change the fan speed, one must set the manual value to 0 (which is the default one set) when setting manual to 1, the fan don't change RPM when setting the min value.

is it the kernel that should handle the throttling of the fan ? Or is there another process in intrepid that handles this by default? 

having the fan running at the default's value of 2000 is not enough when having some
system load...

---

### Post by kosumi68 on 2008-11-03
I just ran a little experiment on my MBA.

With fan1_manual set to zero, I put the CPU governor to full throttle, then start a kernel compilation. Checking with sensors, the CPU temp quite quickly reaches 80 degC. At this point, the fan speed starts to increase, and after a while reaches the peak 6200 rpms. The CPU temp stays around 80 degC. Now, I stop the compilation, turn the CPU governor to power save, and watch the sensors. The CPU temp very quickly drops to 60 degC. After a couple of minutes, the fan speed slowly drops back to its idling value of 2500 rpms, leaving the CPU at 50 degC.

Now I switch the fan1_manual to one and repeat the process. The temperature reaches 80 degC, but the fan speed stays at 2500 rpms. I watch the temperature reach 85 degC, then I switch fan1_manual back to zero, and abort the experiment. The fan immediately runs up to 6200 rpms, and then slowly returns as the CPU gets cooler.

So, for those that have reported high temperatures due to low fan speeds: check the value of
```

cat /sys/devices/platform/applesmc.768/fan1_manual

```

With no software control of the fans, which is the case with the macbooks (fancontrol and pwmconfig does not work), the fan speed seems to be controlled automatically by the SMC without issues - but only if fan1_manual is zero.

Maybe the problem occurs when moving between OSX and Ubuntu via a reboot, which does not clear the NVRAM registers, but this is just a guess.

---

### Post by druggo on 2008-11-04
Interesting experiment, i never had the guts to allow my cpu to get 80 degress, i thought the SMC would kick in earlier though, instead of by just going full speed it would take use of the variable RPM and maybe increase it incrementally...

I will repeat your test during the day, and see when/if the fan change RPM...

Regards,

---

### Post by druggo on 2008-11-04
I did quick test, by compressing a large archive, and my fan seemed to kick in when the CPU reached 85 degress. (if temp5 is my cpu) so it does exactly as you say.

Back to square 1 i suppose. :/

> 
tobbe@toben:~$ sensors
applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :  3366 RPM  (min = 2000 RPM)
temp1:       +30.0°C                                    
temp2:       +30.0°C                                    
temp3:       +28.5°C                                    
temp4:       +30.0°C                                    
temp5:       +86.2°C                                    
temp6:       +69.2°C                                    
temp7:       +77.2°C                                    
temp8:       +58.8°C                                    
temp9:       +65.0°C                                    
temp10:      +77.2°C                                    
temp11:      +65.2°C                                    
temp12:      +58.5°C                                    
temp13:      +28.2°C                                    
temp14:      +42.0°C                                    


---

### Post by kosumi68 on 2008-11-05
During extensive load, with the fans a full speed, the CPU temp seems to land at 75 degC, not more as I indicated before. I believe this is quite acceptable. I notice you have no acpi entries at all in your sensors list. I believe there should be, so I am assuming the ACPI support is lacking somewhat, too.

---

### Post by Nikos.Alexandris on 2008-11-05
The maximum I got yesterday was ~82 (a bit more/a bit less) while compiling several stuff and running lots of applications intentionally at the same time. The fan(s) started to run like crazy (is it the GPU cooler or the processor's cooler) and the temp went after some minutes below 80. It should be ok. Afterall the command sensors gives some "critical temp limit" (see below).

(Now running normal)

```
$ sensors
applesmc-isa-0300
Adapter: ISA adapter
Left side  :3807 RPM  (min = 2000 RPM)
Right side :3804 RPM  (min = 2000 RPM)
temp1:       +39.5°C                                    
temp2:       +39.5°C                                    
temp3:       +38.2°C                                    
temp4:       +39.8°C                                    
temp5:       +70.8°C                                    
temp6:       +64.2°C                                    
temp7:       +64.8°C                                    
temp8:       +70.0°C                                    
temp9:       +61.2°C                                    
temp10:      +55.2°C                                    
temp11:      +61.5°C                                    
temp12:      +66.5°C                                    
temp13:      +66.8°C                                    
temp14:      +69.0°C                                    
temp15:      +66.0°C                                    
temp16:      +55.2°C                                    
temp17:      +62.2°C                                    
temp18:      +58.5°C                                    
temp19:      +33.8°C                                    
temp20:      +48.8°C                                    

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +57.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +58.0°C  (high = +100.0°C, crit = +100.0°C)
```

P.S. Am I right thinking that the "temp5" is the GPU's sensor indication and not the CPU as I read in some post (don't remember which post was that)?

---

### Post by druggo on 2008-11-05
> **kosumi68 said:**
> I notice you have no acpi entries at all in your sensors list. I believe there should be, so I am assuming the ACPI support is lacking somewhat, too.

any steps I can do to narrow down why i don't have acpi listed?

```
tobbe@toben:~$ lsmod | grep acpi
acpi_cpufreq           16400  1 
freq_table             13568  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pata_acpi              13568  0 
libata                200160  3 ahci,pata_acpi,ata_generic
processor              47800  4 acpi_cpufreq,thermal

```
```
tobbe@toben:~$ dmesg | grep acpi
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    3.809342] pata_acpi 0000:00:0b.0: PCI INT A -> Link[LSI0] -> GSI 17 (level, low) -> IRQ 17
[    3.809369] pata_acpi 0000:00:0b.0: setting latency timer to 64
[    3.809383] pata_acpi 0000:00:0b.0: PCI INT A disabled

```

Regards,

---

### Post by druggo on 2008-11-05
> **Nikos.Alexandris said:**
> 
P.S. Am I right thinking that the "temp5" is the GPU's sensor indication and not the CPU as I read in some post (don't remember which post was that)?

you can get the GPU Core temp by invoking:
```

$ nvidia-settings -q all | grep GPUCoreTemp

```

my temp5 are off by ~ 2 degress compared to nvidia-settings report.

---

### Post by Nikos.Alexandris on 2008-11-05
> **druggo said:**
> you can get the GPU Core temp by invoking:
```

$ nvidia-settings -q all | grep GPUCoreTemp

```

my temp5 are off by ~ 2 degress compared to nvidia-settings report.

Thanks. The sensors applet works (at least for the GPU) nice.

---

### Post by kosumi68 on 2008-11-05
> **Nikos.Alexandris said:**
> 
P.S. Am I right thinking that the "temp5" is the GPU's sensor indication and not the CPU as I read in some post (don't remember which post was that)?

On the MacBookPro5, temp 5-7 seems to be CPU and 8-13 seems to be GPU. There is no correlation between numbers and sensors on different models - you have to look it up in the source (/usr/src/applesmc-*/applesmc.c). Some of the sensors names are understood, but far from all ([http://www.mactel-linux.org/wiki/AppleSMC](http://www.mactel-linux.org/wiki/AppleSMC))

---

### Post by druggo on 2008-11-06
Some new thoughts...

after spending some time in OS X, and keeping an eye on the systemload / cpu freq (using sysctl -a | grep cpu) I noticed that OS X seems to scale the cpu down to between 1000Mhz <-> 1500MHz, could this have anything to do with it? I tried changing my governor to powersave in ubuntu using the gnome applet, but on my 2.4GHz cpu i could not get it to run at anything less than 1.6GHz. Anyone got some light to shed on OS X's cpu freq scaling? or is this irrelevant...

the reason why i want to get the cpu freq down (and hopefully the heat), is to get the battery life up, 2 hours under linux honestly sucks (much depending on that we can't change background since nvidia don't support RandR yet, right?)

Regards,

---

### Post by kosumi68 on 2008-11-06
> **druggo said:**
> [...] I noticed that OS X seems to scale the cpu down to between 1000Mhz <-> 1500MHz, could this have anything to do with it? I tried changing my governor to powersave in ubuntu using the gnome applet, but on my 2.4GHz cpu i could not get it to run at anything less than 1.6GHz.

Now that is interesting.
```

dmesg | grep ACPI | grep CPU

```
```

sudo powertop

```
ought to give you an idea of the power states of the CPU.

---

### Post by druggo on 2008-11-06
```
tobbe@toben:~$ dmesg | grep ACPI | grep CPU
[    2.159752] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.159831] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.191389] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.191465] ACPI: Processor [CPU1] (supports 8 throttling states)

```

will look into powertop and the tip it suggests...

---

### Post by kosumi68 on 2008-11-06
> **druggo said:**
> 

the reason why i want to get the cpu freq down (and hopefully the heat), is to get the battery life up, 2 hours under linux honestly sucks (much depending on that we can't change background since nvidia don't support RandR yet, right?)


Do you by any chance have the kernel module mbp_nvidia_bl installed, and a device called /sys/class/backlight/mbp_backlight/brightness? If so, what happens if you do
```

echo 5 | sudo tee -a /sys/class/backlight/mbp_backlight/brightness

```

---

### Post by Nikos.Alexandris on 2008-11-06
(testing on MBP 5,1)

I have installed and ran powertop. Some of the suggestions that I (think) implemented are:

* set VM writeback to 1500

* enable USB Suspend (this comes several times for several hardware -- e.g. for keyboard, mouse, broadcom and even the ir port)

* $ sudo hal-disable-polling --device /dev/cdrom
[sudo] password for nik: 
Following symlink from /dev/cdrom to /dev/scd0.
Polling for drive /dev/cdrom have been disabled. The fdi file written was
  /etc/hal/fdi/information/media-check-disable-storage_model_DVD_R___UJ_868.fdi

* I also turned off wifi and bluetooth.

I have the impression that the battery gets eaten up a bit slower!


> Do you by any chance have the kernel module mbp_nvidia_bl installed, and a device called /sys/class/backlight/mbp_backlight/brightness? If so, what happens if you do
```
echo 5 | sudo tee -a /sys/class/backlight/mbp_backlight/brightness
```

kosumi68, where can I find this module?
The command "sudo apt-cache search mbp_nvidia" does not return something.

---

### Post by Nikos.Alexandris on 2008-11-06
> **Nikos.Alexandris said:**
> (testing on MBP 5,1)

[...]

kosumi68, where can I find this module?
The command "sudo apt-cache search mbp_nvidia" does not return something.

Sorry, thought it was a package. I have tried to load but...
```
sudo modprobe mbp_nvidia_bl

FATAL: Error inserting mbp_nvidia_bl (/lib/modules/2.6.27-7-generic/kernel/drivers/video/backlight/mbp_nvidia_bl.ko): No such device

```

---

### Post by kosumi68 on 2008-11-06
> **Nikos.Alexandris said:**
> 
I have the impression that the battery gets eaten up a bit slower!


kosumi68, where can I find this module?
The command "sudo apt-cache search mbp_nvidia" does not return something.

Good good.
```

sudo modprobe mbp_nvidia_bl

```
(its a kernel module)

---

### Post by Nikos.Alexandris on 2008-11-06
I have added it in /etc/modules (as you suggested in another thread). I am rebooting now and see what happens :-?

Thanks kosumi68 for all of your efforts. I think I am going to keep this machine. It's worth the effort to make it run Ubuntu :-)

---

### Post by Nikos.Alexandris on 2008-11-06
OK, I experienced another boot-up hang (not freeze). Boot process got stuck at:
* Saving VESA states...

I waited for a minute or so. The green led on the Caps-Lock key worked so I've just pressed Fn+ctrl+alt+Backspace and the restart process froze at the very end (Now restarting or something).

Anyway, I booted up again without any problem but the **mbp_nvidia_bl** modules is not loaded although present in **/etc/modules** 

```
lsmod | grep nvidia

nvidia               7804864  28 
i2c_core               36128  1 nvidia
```

And now?

---

### Post by kosumi68 on 2008-11-06
Do you get an error message on screen or in dmesg when loading the module with
```

sudo modprobe mbp_nvidia_bl

```
(there is no immediate need to reboot in order to get the device going).

---

### Post by Nikos.Alexandris on 2008-11-06
> **kosumi68 said:**
> Do you get an error message on screen or in dmesg when loading the module with
```

sudo modprobe mbp_nvidia_bl

```
(there is no immediate need to reboot in order to get the device going).

Yes, the same error message as in (my) post #24

---

### Post by kosumi68 on 2008-11-06
Ah, the forum seems to be lagging - i missed your comment. Thanks for testing, I got the answer I suspected. The new graphics card is simply not supported at any level at this stage. We'll keep our eyes open. Cheers!

---

### Post by Nikos.Alexandris on 2008-11-07
> **Nikos.Alexandris said:**
> (testing on MBP 5,1)

I have installed and ran powertop. Some of the suggestions that I (think) implemented are:

* set VM writeback to 1500

* enable USB Suspend (this comes several times for several hardware -- e.g. for keyboard, mouse, broadcom and even the ir port)

* $ sudo hal-disable-polling --device /dev/cdrom
[sudo] password for nik: 
Following symlink from /dev/cdrom to /dev/scd0.
Polling for drive /dev/cdrom have been disabled. The fdi file written was
  /etc/hal/fdi/information/media-check-disable-storage_model_DVD_R___UJ_868.fdi

* I also turned off wifi and bluetooth.

I have the impression that the battery gets eaten up a bit slower!


The above mentioned "changes" are not permanent/not saved. Why? How can they be forced?

Today the laptop didn't make it over 1 and a half hour :-(

This is pretty serious. What should one do to protect the battery from being damaged?

---

### Post by Nikos.Alexandris on 2008-11-08
> **Nikos.Alexandris said:**
> The above mentioned "changes" are not permanent/not saved. Why? How can they be forced?

Today the laptop didn't make it over 1 and a half hour :-(

This is pretty serious. What should one do to protect the battery from being damaged?

I did a test and wrote down some stuff...


**MBP 5,1 - Battery duration on Ubuntu Intrepid Ibex**

* 100% charged on OSX reports [COLOR="Blue"]5:30[/COLOR] time remaining

* On Ubuntu Intrepid Ibex working only with battery and with some power-saving settings [1]:

Booting at 18:39 CET

96% > 1h 45m
82% > 1h 25m [at 19:05]
69% > 1h 10m [at 19:20]
60% > 1h		[at 19:32]
42% > 0h 45m [at 19:50]
29% > 0h 30m [at 20:06]
20% > 0h 20m [at 20:15]
4%   > 0h 05m [at 20:32]
3%   > 0h 04m [at 20:33]

Automatic shut-down at 20:35 CET

Total battery duration [COLOR="Blue"]01h 56m[/COLOR]

----

The 5 hours reported in OSX make the "less than 2 hours" in Ubuntu look really bad. Probably there are more things to play with. Hopefully someone has the experience so we can set some "default" settings for the MBP 5,1.

But I am really curious to know why there is this huge difference? Is power management on Ubuntu (linux in general) so bad?

Kind regards, Nikos

----

[1] Settings introduced in a script [2] which 

  # Set "aggressive" power savings which then was installed in the directories /etc/pm/power.d and /etc/pm/sleep.d as suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)
  
  ```
# Enable laptop mode disk optimization
  echo 5 > /proc/sys/vm/laptop_mode

  # Set kernel dirty page value back to default Reduce disk activity
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 10 > /proc/sys/vm/dirty_background_ratio

  # Set SATA to minimum power
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
 
  # Wakeup every 15 seconds to check if dirty pages writing necessary
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

  # Set powersave cpu frequency scaling governor
  echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
[2] The whole script look like that:

```
#!/bin/bash
if on_ac_power; then

  # Set "normal" settings

  # Disable laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Wakeup every 5 seconds to check if dirty pages writing necessary
  ## Maybe test 10 seconds and compare against 5?
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs

  # Set the SATA to max performance
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy

  # Set ondemand cpu frequency scaling governor
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

else

  # Set "aggressive" power savings
  
  # Enable laptop mode disk optimization
  echo 5 > /proc/sys/vm/laptop_mode

  # Set kernel dirty page value back to default Reduce disk activity
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 10 > /proc/sys/vm/dirty_background_ratio

  # Set SATA to minimum power
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
 
  # Wakeup every 15 seconds to check if dirty pages writing necessary
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

  # Set powersave cpu frequency scaling governor
  echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

fi
```

---

### Post by kosumi68 on 2008-11-08
> **Nikos.Alexandris said:**
> 

But I am really curious to know why there is this huge difference? Is power management on Ubuntu (linux in general) so bad?



You might want to install laptop-mode. I run with battery life between 3 and 4 hours on my MBA; see the power management section of [https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid](https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid). With powertop tweaks, low brightness and text mode screen, I can get as low as 8 watts, with a projected battery life of 6 hours.

---

### Post by Nikos.Alexandris on 2008-11-08
> **kosumi68 said:**
> You might want to install laptop-mode. I run with battery life between 3 and 4 hours on my MBA [...]

kosumi68,

thank you for your reply. That is encouraging :-). I just had a bad experience with the laptop mode in the past (a year ago): the system's overall responsiveness was just not acceptable. 

Also, do we have to worry about the hard disk load cycles issue? What is the difference between 5400 rpm and 7200 rpm disk with respect to load cycles?

Regards, Nikos

---

### Post by druggo on 2008-11-10
kosumi: I think if we (on the new Unibody and GF 9400M) will be able to change backlight on our displays, we can expect much longer uptimes, don't you think? It's such a power drainer..

Nikos: can you change you backlight??, when using maximal power savings, how many Watts do powertop report?

---

### Post by kosumi68 on 2008-11-10
> **druggo said:**
> kosumi: I think if we (on the new Unibody and GF 9400M) will be able to change backlight on our displays, we can expect much longer uptimes, don't you think? It's such a power drainer..

Nikos: can you change you backlight??, when using maximal power savings, how many Watts do powertop report?

Yes. Trying out _mario_'s effort might be a good thing: [http://ubuntuforums.org/showthread.php?t=977558](http://ubuntuforums.org/showthread.php?t=977558)

---

### Post by Nikos.Alexandris on 2008-11-11
> **druggo said:**
> kosumi: I think if we (on the new Unibody and GF 9400M) will be able to change backlight on our displays, we can expect much longer uptimes, don't you think? It's such a power drainer..

Nikos: can you change you backlight??, when using maximal power savings, how many Watts do powertop report?

druggo,

I'll have a look at it later. I was quite busy yesterday / I am today. Cheers, Nikos

edit: No, I can't change the brightness! I boot in OSX, adjust it and reboot :D

---

### Post by druggo on 2008-11-11
Ahh boot into OSX and change it, i never even though of that, thanks! :)

kosumi68: thanks for the heads up on mario's patch, i tried it though, and it didn't help.

Cheers

---

### Post by ercoppa on 2008-11-12
> I boot in OSX, adjust it and reboot
> Ahh boot into OSX and change it, i never even though of that, thanks
:( For me not works

Do you have MacBook or MacBook Pro? Do you have refit installed?

---

### Post by Nikos.Alexandris on 2008-11-12
> **ercoppa said:**
> :( For me not works

Do you have MacBook or MacBook Pro? Do you have refit installed?

MBP with rEFIt.

---

### Post by Nikos.Alexandris on 2008-11-21
> **kosumi68 said:**
> I just ran a little experiment on my MBA.

With fan1_manual set to zero, I put the CPU governor to full throttle, then start a kernel compilation. Checking with sensors, the CPU temp quite quickly reaches 80 degC. At this point, the fan speed starts to increase, and after a while reaches the peak 6200 rpms. The CPU temp stays around 80 degC. Now, I stop the compilation, turn the CPU governor to power save, and watch the sensors. The CPU temp very quickly drops to 60 degC. After a couple of minutes, the fan speed slowly drops back to its idling value of 2500 rpms, leaving the CPU at 50 degC.

Now I switch the fan1_manual to one and repeat the process. The temperature reaches 80 degC, but the fan speed stays at 2500 rpms. I watch the temperature reach 85 degC, then I switch fan1_manual back to zero, and abort the experiment. The fan immediately runs up to 6200 rpms, and then slowly returns as the CPU gets cooler.

So, for those that have reported high temperatures due to low fan speeds: check the value of
```

cat /sys/devices/platform/applesmc.768/fan1_manual

```

With no software control of the fans, which is the case with the macbooks (fancontrol and pwmconfig does not work), the fan speed seems to be controlled automatically by the SMC without issues - but only if fan1_manual is zero.

Maybe the problem occurs when moving between OSX and Ubuntu via a reboot, which does not clear the NVRAM registers, but this is just a guess.

I've tried the FanControl[1] (free and open source) program for OSX. The fans's RPM's adjust dynamically non-stop between 2000 and 2200 when not doing anything heavy. Under linux it seems they are constantly around 2000 RPM.

Could the FanControl program be of any use for you developers?

Regards, Nikos

[1] [http://www.lobotomo.com/products/FanControl/](http://www.lobotomo.com/products/FanControl/)

---

### Post by druggo on 2008-11-23
thanks for the input nikos!

I believe that the real problem is that OSX scales the CPU different than the linux kernel, this causes it to reduce less heat and longer battery life. It might also be possible that nvidia gpu scaling doesen't work as it should, since our gpu's not supported by the nvidia driver yet...

I tried to monitor the frequency of the CPU in OSX when doing different tasks, and they scaled the CPU downto 800MHz most of the idle time... compared to 1,6GHz in linux.

Lets hope some CPU scaling guru can shed some light on this issue? =)

---

### Post by Nikos.Alexandris on 2008-11-23
> **druggo said:**
> thanks for the input nikos!

I believe that the real problem is that OSX scales the CPU different than the linux kernel, this causes it to reduce less heat and longer battery life. It might also be possible that nvidia gpu scaling doesen't work as it should, since our gpu's not supported by the nvidia driver yet...

I tried to monitor the frequency of the CPU in OSX when doing different tasks, and they scaled the CPU downto 800MHz most of the idle time... compared to 1,6GHz in linux.

Lets hope some CPU scaling guru can shed some light on this issue? =)

Hi druggo!

Thank you for your clarifications. Yet, while your comments upon CPU-scaling are clear, I don't understand the "our gpu's not supported by the nvidia driver yet...".

The nvidia driver is a binary driver provided by NVidia. How come that they don't support their GPU's? Sorry if I misunderstand.

Thanks, Nikos

---

### Post by druggo on 2008-11-23
> **Nikos.Alexandris said:**
> Hi druggo!

Thank you for your clarifications. Yet, while your comments upon CPU-scaling are clear, I don't understand the "our gpu's not supported by the nvidia driver yet...".

The nvidia driver is a binary driver provided by NVidia. How come the they don't support their GPU's? Sorry if I misunderstand.

Thanks, Nikos
If you look in the list of supported devices for the proprietary nvidia driver you'll see that the 9400M card is not included. That's what i meant...
im running nvidia 108.08 beta and though it gets detected OK, it's not "officially" supported, from what i can understand, anyone please correct me if i'm wrong.

Regards,

---

### Post by Nikos.Alexandris on 2008-11-23
> **druggo said:**
> If you look in the list of supported devices for the proprietary nvidia driver you'll see that the 9400M card is not included. That's what i meant...
im running nvidia 108.08 beta and though it gets detected OK, it's not "officially" supported, from what i can understand, anyone please correct me if i'm wrong.

Regards,

druggo,

that's a bit strange. I have 177.80 on mystem, installed from the repositories and the correct GPU is fully recognised (that is GeForce 9600M GT).

How come you are stuck in 108.08 beta version?

What does the tab *GPU0* in *NVidia-Settings* (under System > Admnistration) say?

---

### Post by bsolar on 2008-11-25
in Intrepid cpufreq-info shows as hardware limits 1.60 GHz - 2.53 GHz. Is this correct or there are missing frequency steps? I am unsure how to check the available steps in OSX.

---

### Post by druggo on 2008-11-25
> **Nikos.Alexandris said:**
> druggo,

that's a bit strange. I have 177.80 on mystem, installed from the repositories and the correct GPU is fully recognised (that is GeForce 9600M GT).

How come you are stuck in 108.08 beta version?

What does the tab *GPU0* in *NVidia-Settings* (under System > Admnistration) say?

It reports 9400M, however, just because it get _detected_ doesen't meen that it's _supported_ by the nvidia driver. If you check the list included with their proprietary drivers you'll notice that the 9400 is not listed :) 

im not stuck in beta, i just installed it to see if it made any difference, snappier screen refresh is one thing i notice with the new driver.

Cheers

---

### Post by bsolar on 2008-11-25
I tought these were the frequency steps but they seem to be a different thing:

```
$ cat /proc/acpi/processor/CPU0/throttling 
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

```

Anybody knows what it means?

BTW cpufreq shows only 5 steps: I expected 1.2GHz and 800MHz to be present too:

```
$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1.60 GHz - 2.53 GHz
  available frequency steps: 2.53 GHz, 2.39 GHz, 2.13 GHz, 1.86 GHz, 1.60 GHz
  available cpufreq governors: userspace, ondemand, conservative, performance
  current policy: frequency should be within 1.60 GHz and 2.53 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1.60 GHz - 2.53 GHz
  available frequency steps: 2.53 GHz, 2.39 GHz, 2.13 GHz, 1.86 GHz, 1.60 GHz
  available cpufreq governors: userspace, ondemand, conservative, performance
  current policy: frequency should be within 1.60 GHz and 2.53 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.

```

Ideas? If not I'll open a bugreport.

---

### Post by Nikos.Alexandris on 2008-11-25
> **bsolar said:**
> I tought these were the frequency steps but they seem to be a different thing:

```
$ cat /proc/acpi/processor/CPU0/throttling 
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

```

Anybody knows what it means?

BTW cpufreq shows only 5 steps: I expected 1.2GHz and 800MHz to be present too:

```
$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1.60 GHz - 2.53 GHz
  available frequency steps: 2.53 GHz, 2.39 GHz, 2.13 GHz, 1.86 GHz, 1.60 GHz
  available cpufreq governors: userspace, ondemand, conservative, performance
  current policy: frequency should be within 1.60 GHz and 2.53 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1.60 GHz - 2.53 GHz
  available frequency steps: 2.53 GHz, 2.39 GHz, 2.13 GHz, 1.86 GHz, 1.60 GHz
  available cpufreq governors: userspace, ondemand, conservative, performance
  current policy: frequency should be within 1.60 GHz and 2.53 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.

```

Ideas? If not I'll open a bugreport.

bsolar,
that might be great news! (...or not?). If speed-step technology is there and works below 1.6GHz on OSX, why not on linux?

Someone with deep knowledge is required to explain the situation or digging on the net and reading stuff :-)

With 800Hz when the system doesn't really do anything heavy, low brightness values, get rid of all non-relevant modules, improving the "laptop_mode" (incorporating many powertop-suggestions / perhaps designing a generic macbook-linux power management specification), then we will see mb(p)s flying with ubuntu for above 3 hours.

Regards

---

### Post by bsolar on 2008-11-25
Well going to 800MHz is possible with 2.4 GHz core 2 duo CPUs as far as I have read. I am trying to find a way to monitor the CPU speed in OSX but without luck so far.

---

### Post by Nikos.Alexandris on 2008-11-25
> **bsolar said:**
> Well going to 800MHz is possible with 2.4 GHz core 2 duo CPUs as far as I have read. I am trying to find a way to monitor the CPU speed in OSX but without luck so far.

There are external utilities for that. Search for "OSX cpu frequency" and you'll find plenty of references and tools.

Regards

---

### Post by bsolar on 2008-11-25
> **Nikos.Alexandris said:**
> There are external utilities for that. Search for "OSX cpu frequency" and you'll find plenty of references and tools.

Regards

I tried with some tools but they don't work, e.g: CoreDuoTemp.

I tried with sysctl too but it shows strange results:

```
$ sysctl -a | grep cpufrequency
kern.exec: unknown type returned
hw.cpufrequency = 2530000000
hw.cpufrequency_max: 2530000000
hw.cpufrequency_min: 2530000000
hw.cpufrequency: 2530000000

```

---

### Post by Nikos.Alexandris on 2008-11-25
> **bsolar said:**
> I tried with some tools but they don't work, e.g: CoreDuoTemp.

I tried with sysctl too but it shows strange results:

```
$ sysctl -a | grep cpufrequency
kern.exec: unknown type returned
hw.cpufrequency = 2530000000
hw.cpufrequency_max: 2530000000
hw.cpufrequency_min: 2530000000
hw.cpufrequency: 2530000000

```

I'll have to try this out. In the following days I'll have a look. Sorry for not being able to try it quickly.

Regards

---

### Post by druggo on 2008-11-26
I managed to get the 800 MHz info using sysctl -a, then its located at the top, not sure of the name of the variable. 
Don't have the time right now to reboot to isx to look, it's there, and depending on load, it changes its value.

---

### Post by druggo on 2008-11-26
> **bsolar said:**
> 

Ideas? If not I'll open a bugreport.

Open a bugreport please, please send me a link to the bugreport, and i can fill in info if needed. I want T6 & T7 states!!

---

### Post by bsolar on 2008-11-26
> **druggo said:**
> Open a bugreport please, please send me a link to the bugreport, and i can fill in info if needed. I want T6 & T7 states!!

T6 and T7 are a different thing, it'a feature allowing the CPU to run "idle" sacrificing performance doing nothing. E.g with 50% throttling the CPU would still run at the normal speed but would do nothing half the time.

Want I think it's missing are P-states below 1.6GHz but I am not still 100% sure the CPU allows them...

My theory is that OSX is able to use lower frequencies but I was unable to confirm this. I'd like to have this confirmed before opening a bugreport. Can you please provide where you spotted the 800MHz figure? Hoping it actually refers the CPU frequency available.

---

### Post by druggo on 2008-11-26
> **bsolar said:**
> T6 and T7 are a different thing, it'a feature allowing the CPU to run "idle" sacrificing performance doing nothing. E.g with 50% throttling the CPU would still run at the normal speed but would do nothing half the time.

Want I think it's missing are P-states below 1.6GHz but I am not still 100% sure the CPU allows them...

My theory is that OSX is able to use lower frequencies but I was unable to confirm this. I'd like to have this confirmed before opening a bugreport. Can you please provide where you spotted the 800MHz figure? Hoping it actually refers the CPU frequency available.

i think i spotted it with 
```
sysctl -a | grep kern.cpu_currentfreq
```

however, if i check now, i can see that the cpu is working between 1000 to 1500, weird, even on AC i can never get it to go up to 2400 which should be my max :confused:

```
kern.cpu_currentfreq: 1166
kern.cpu_log: 0
kern.cpu_minfreq: 1000
kern.cpu_maxfreq: 1500
```

---

### Post by bsolar on 2008-11-26
> **druggo said:**
> i think i spotted it with 
```
sysctl -a | grep kern.cpu_currentfreq
```

however, if i check now, i can see that the cpu is working between 1000 to 1500, weird, even on AC i can never get it to go up to 2400 which should be my max :confused:

```
kern.cpu_currentfreq: 1166
kern.cpu_log: 0
kern.cpu_minfreq: 1000
kern.cpu_maxfreq: 1500
```

That command returns nothing here, only the kern.exec error...

---

### Post by bsolar on 2008-11-26
From what I read the command should be:

```
sysctl kern.cputhrottle_freqs
```

Here it returns nothing...

---

### Post by bsolar on 2008-11-26
aww, forget, the last command is if you load some strange extension.

Why it's so hard to get this information out of leopard?:confused:

---

### Post by bsolar on 2008-11-27
I'm wondering if this "Dynamic FSB Frequency Switching" matters in this issue:

> Dynamic FSB Frequency Switching
Dynamic FSB frequency switching effectively reduces the internal bus clock frequency
in half to further decrease the minimum processor operating frequency from the
Enhanced Intel SpeedStep Technology performance states and achieve the Super Low
Frequency Mode (Super LFM).

---

### Post by bsolar on 2008-11-27
I replied to this bugreport which is somewhat related:

[https://bugs.launchpad.net/bugs/262550](https://bugs.launchpad.net/bugs/262550)

If prompted to do so I'll file a new one...

---

### Post by J33nx on 2008-11-29
I have been reading through this thread for a bit now. Trying different commands, settings, throttles, etc. From looking at that can be done in just an xterm window, I think it would be possible to write a script that automates everything here. Throttling depending on CPU usage, PROPER fan speed control based on temperature and accurate temp reporting for CPU and GPU. I am looking into making something like Core2DueTemp (OSX) for Linux. Seems it would be a viable option at this point. What do you guys think?

---

### Post by Nikos.Alexandris on 2008-11-29
> **J33nx said:**
> I have been reading through this thread for a bit now. Trying different commands, settings, throttles, etc. From looking at that can be done in just an xterm window, I think it would be possible to write a script that automates everything here. Throttling depending on CPU usage, PROPER fan speed control based on temperature and accurate temp reporting for CPU and GPU. I am looking into making something like Core2DueTemp (OSX) for Linux. Seems it would be a viable option at this point. What do you guys think?

Hi J33nx!

I also thought of scripting some of the stuff you mention. But the question I have is "how efficient is a script in this situations?". It would be much more efficient to code this stuff properly. Wouldn't it?

Unfortunately my programming skills are limited and my free-time restricted as well.

Cheers

---

### Post by J33nx on 2008-11-29
I am in the process of learning Python. I have dived very deep into it so far and I am hoping I can use my newly learned "skill" to make something worth using for the Linux community. I am also wanting to help address the many issues the MacBook (Pro) Aluminum (5,1) face with Ubuntu. After about a week of work, I was able to install Ubuntu onto my 5,1 with the only issue left being that I cannot shut down properly. If people want it, I will make a tutorial on what I did and links that I used to make it all work!

---

### Post by Nikos.Alexandris on 2008-11-29
> **bsolar said:**
> I tried with some tools but they don't work, e.g: CoreDuoTemp.

I tried with sysctl too but it shows strange results:

```
$ sysctl -a | grep cpufrequency
kern.exec: unknown type returned
hw.cpufrequency = 2530000000
hw.cpufrequency_max: 2530000000
hw.cpufrequency_min: 2530000000
hw.cpufrequency: 2530000000

```

I get a "strange" output!

```
sysctl -a | grep cpufrequency
error: permission denied on key 'kernel.cad_pid'
error: permission denied on key 'fs.binfmt_misc.register'
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
```

---

### Post by Nikos.Alexandris on 2008-11-29
> **bsolar said:**
> I replied to this bugreport which is somewhat related:

[https://bugs.launchpad.net/bugs/262550](https://bugs.launchpad.net/bugs/262550)

If prompted to do so I'll file a new one...

I've just posted something as well.

---

### Post by Nikos.Alexandris on 2008-11-29
> **J33nx said:**
> I am in the process of learning Python. I have dived very deep into it so far and I am hoping I can use my newly learned "skill" to make something worth using for the Linux community. I am also wanting to help address the many issues the MacBook (Pro) Aluminum (5,1) face with Ubuntu. After about a week of work, I was able to install Ubuntu onto my 5,1 with the only issue left being that I cannot shut down properly. If people want it, I will make a tutorial on what I did and links that I used to make it all work!

You should contact the people here. have a look also here:

[https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)
[http://ubuntuforums.org/showthread.php?t=969360](http://ubuntuforums.org/showthread.php?t=969360)
[http://ubuntuforums.org/group.php?groupid=352](http://ubuntuforums.org/group.php?groupid=352)

And have a look at the current wiki (for mb and mbp one page currently):
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) Aluminum

Maybe you can correct/improve it.

Regards

---

### Post by hawkwing3141 on 2008-11-30
In regards to battery life, has anyone else noticed that the optical out is always on in (K)ubuntu but not OSX (Macbook 5,1)?  It's a red light coming out of the headphone jack even when no sound is playing.  Getting this turned off might help with battery life, if anyone knows how?

---

### Post by Nikos.Alexandris on 2008-12-03
Folks,

perhaps interesting to all MBP5,1 owners & Ubuntu(linux)friends: a report installing Gentoo on the MBP5,1 here:

[http://www.spicious.com/blog/2008/11/gentoo-on-the-macbook-pro/#comment-6](http://www.spicious.com/blog/2008/11/gentoo-on-the-macbook-pro/#comment-6)

Gentoo seems to perform better (battery life) and doesn't get hot(ter!?).

Regards, Nikos

---

### Post by bsolar on 2008-12-18
In the community documentation this comment has been added: 

> PowerTOP reports that the module for the 10/100/1000 interface wakes the processor 100+x/sec, accounting for >50% of wakeups on an idle system. This dramatically shortens battery life. One potential solution is to unload this module if you only use wireless.

There is anyone willing to quantify the improvement in battery life with the module unloaded? At the moment I cannot test it myself.

---

### Post by ercoppa on 2008-12-18
With brightness == 1 && wireless active && bluetooth module unloaded && ethernet module unloaded, I have 2,5-2,7 hour (by powertop).

---

### Post by mrneil on 2008-12-31
Im running Debian Lenny on the MacBook Pro 5,1, and it is too hot and thus has a low battery life.

I've been following this thread and have implemented the really helpful suggestions. I've got the latest mactel modules (including applesmc) installed. I've disabled bluetooth and hal cdrom polling. I've got the sound card powering down after a few seconds. I've got the SATA link_power_management_policy set at minimum. I've got VM dirty_writeback_centisecs set to 15s. I've got the on-demand scaling governor running (so both processors are at 1.6 GHz). (See powertop program recommendations and [http://www.lesswatts.org](http://www.lesswatts.org) for details on these.) In summary, I've done everything I can Google to save power.

Even with no load, the MacBook Pro is much hotter than in OS X, almost uncomfortably so. And, presumably as a direct consequence, the battery life is poor (much less than 2 hours). (All the heat energy must be coming from somewhere.) Running the fan at a higher speed cools the system, but we still haven't identified what the cause of the extra heat was in the first place and running the fan doesn't make the battery last longer!

So there is still something that OS X can do that Debian and Ubuntu are not doing to save power. I've got two outstanding clues so far:

1. Druggo's post #19 refers to the possibility that the Intel Core 2 Duos can run under 1.6 GHz. The implicit suggestion is that the cpufreq modules have got only a partial table of available frequencies. But I've not been able to find an Intel specification for the T9400 processors in the MacBook Pro 5,1. And software in OSX side doesn't report less than 1.6 GHz for me.

2. The hottest part of the case is on the left, just about the F1-F5 keys. The right-hand side is cooler. Perhaps this might help someone with knowledge of the internals work out what is causing all of the heat.

Has anyone using Ubuntu been able to make any progress on the cause of all the heat?

---

### Post by cyberdork33 on 2008-12-31
> **mrneil said:**
> 2. The hottest part of the case is on the left, just about the F1-F5 keys. The right-hand side is cooler. Perhaps this might help someone with knowledge of the internals work out what is causing all of the heat.

Looking [here]("http://www.ifixit.com/Guide/First-Look/Mac/MacBook-Pro-Unibody/Page-7#top"), that seems to be the location of one of the fans. The other would be under the other half... Can you verify that both fans are actually running?

---

### Post by stream303 on 2008-12-31
Up front let me state I'm out of my league since I don't own an Intel mac, however I have come across some issues that might be worth it from an experimental aspect regarding cpufreq problems.

On my AMD64 box that was running OpenSuse, they rely solely upon cpufreq, and it wouldn't scale, even though cpufreq-utils shows that all the states of conservative, powersave, performance, and userspace was available.

What was happening was that the latency when switching was too large using anything that scaled, such as conservative or userspace, and cpufreq would just default back to performance.  I could control it manually by using either powersave or performance, but I wanted automatic scaling.  This affected not only cpufreqd, but also powernowd as well.

Turns out that **cpudyn** worked just fine by merely installing it from the repos.  It only has two states, and the latency problem was cured when switching.  I don't know what's in that guy's code but it seems to deal with the switching latency issues better.

Problem is, cpudyn is not ideal for smp.  That is, the scaling works in tandem on the cores - thus if cpu0 is told to scale, it does so for cpu1 as well.  This *might* be a temporary cure even if not ideal for smp where you need both cores to run at different speeds at different times.

Perhaps give cpudyn a shot anyway - both cores will just scale in tandem, but it might give some temporary relief.

I didn't have to remove cpufreqd - all I had to do was apt-get or synaptic install cpudyn.  (Actually in OpenSuse I had to compile it since it wasn't in their repos)

This issue drove me crazy until I caught the latency switching errors when I had an error-console up.

---

### Post by cyberdork33 on 2008-12-31
worth a try, can't hurt anything.

---

### Post by mrneil on 2008-12-31
Cyberdork33, yes both fans are running. If I hold the laptop to my ear I can hear and feel air going through both of them. I can control the speeds separately for each fan with, for example,

echo "3000" > /sys/devices/platform/applesmc.768/fan1_min
echo "3000" > /sys/devices/platform/applesmc.768/fan2_min

Even at 3000 on fan1 and 2000 on fan2, the left hand side is still hotter.

---

### Post by mrneil on 2008-12-31
Steam303, I can confirm that cpufreq scaling does work on the MacBook Pro 5,1. If I compile a kernel, both processors go up to 2.53 GHz and then drop back to 1.60 GHz afterwards.

---

### Post by mrneil on 2008-12-31
I had assumed that there was a CPU under each fan, but I'm guessing now that that's wrong and that the GPU is under one fan and the CPU (with 2 cores) is under the other fan. Does anyone know whether this is true and which side is which? That would narrow the problem down rather well.

---

### Post by cyberdork33 on 2009-01-02
> **mrneil said:**
> I had assumed that there was a CPU under each fan, but I'm guessing now that that's wrong and that the GPU is under one fan and the CPU (with 2 cores) is under the other fan. Does anyone know whether this is true and which side is which? That would narrow the problem down rather well.

looking at the pictures in what I posted earlier it looks like each fan has a heat pipe that runs across both the cpu and the gpu (and the chipset), This is why I thought maybe one was not running.

[IMG]http://static2.ifixit.com/igi/XNtRlNUt2sh2sKnA.large[/IMG]

In OSX on my MacBookPro4,1 the left side is hotter, but I use smcFanControl to run the left fan a little faster than the right side. I'd still suggest trying out the other cpu freq scaling daemon as suggested by stream303

---

### Post by mrneil on 2009-01-02
I've looked more closely at the link cyberdork33 posted. The fans are not separate, with one for the CPU and one for the GPU. Instead, there is a pair of heat pipes that run across both GPUs and the CPU and then split left and right for each fan. Steps 20 and 21 show this most closely

[http://www.ifixit.com/Guide/First-Look/Mac/MacBook-Pro-Unibody/Page-7]("http://www.ifixit.com/Guide/First-Look/Mac/MacBook-Pro-Unibody/Page-7")

So I'm abandoning the asymmetry hypothesis. My explanation about one side being hotter because it's over the CPU rather than the GPU (or vice versa) is wrong.

But seeing inside it is obvious that the left hand side is hotter than the right hand side because both fans vent on the left hand side. The CD is under the right hand side (about as far in as the F8 key). 

So something (either the CPU or one of the GPUs) is too hot under Ubuntu and Debian compared to MAC OS and, so far, we don't know how to make it run cooler.

---

### Post by cyberdork33 on 2009-01-02
Something else to consider is the fact that the actual chips on the logic board are not symmetrical within the housing. In fact, from the reading with the linked guide, it appears the offset chip is one of the GPUs. That said, more heat is likely being generated on the warm side of the board and results in that side feeling hotter. Maybe our focus is out of place... What about scaling on the GPU? Is that working?

---

### Post by mrneil on 2009-01-02
Sorry for the crossing postings earlier on the heat pipe layout.

I'm running the 9600M GT processor (rather than the 9400) in both Debian and in OS X. I'm using the proprietary NVIDIA driver from the non-free Debian repository (version 173.14.09). 

The nvidia-settings program has a section called "thermal monitor" which reports a temperature of 63 degrees C. When pushed with some graphics (e.g., glxgears) the temperature rises to 71 C. (I tested this with the fan speed for both fans set to 2000.)

The section "powermizer" shows that adaptive clocking is enabled and that I'm running on performance level 0 (169 MHz) unless I push it with glxgears (or some other graphics), in which case it jumps up to 500 MHz and then gradually ramps down over 30s or so.

So it looks like power management is enabled for the GPU. I wonder how different the OSX and linux NVIDIA drivers are?

---

### Post by cyberdork33 on 2009-01-03
63 C is quite hot... not too hot that your computer won't operate, but hot none-the-less

---

### Post by ercoppa on 2009-01-03
Same with Nvidia 9400M (last beta drivers) and glxgear: in 5 minutes I have a temperature of 70-75 degrees C. This is a very bad news.

Greets, ercoppa.

---

### Post by pragmatine on 2009-01-04
I recently got myself a new MacBook Pro 5,1 and installed Intrepid on it and have been following this thread with some interest as it seemed my MBP was running a little warm (idle temp roughly 53C from coretemp module).

So for the last couple days I've been planning to implement a version of [smcFanControl]("http://homepage.mac.com/holtmann/eidac/software/smcfancontrol2/index.html") for linux  so you can set the min fan speed using a nice graphical tool from your GNOME panel as a normal user rather than having to do a 
```
echo 3000 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
```
from the terminal.

Eventually I may extend it to automatically control the min fan speed based on current cpu temperature and power state etc. Let me know what you think and I will post a version of it once I start getting somewhere - should be in a day or two, should take too long as it is pretty similar to as lot of the stuff I've already done with [GNOME Sensors Applet]("http://packages.ubuntu.com/sensors-applet").

---

### Post by mrneil on 2009-01-04
I certainly agree that running the fan will cool down the machine. My goal is to try to avoid generating the heat in the first place---because this is what is hurting the battery life so badly compared to Mac OS X. I'm very happy to test out any suggestions!

---

### Post by cyberdork33 on 2009-01-05
> **pragmatine said:**
> I recently got myself a new MacBook Pro 5,1 and installed Intrepid on it and have been following this thread with some interest as it seemed my MBP was running a little warm (idle temp roughly 53C from coretemp module).

So for the last couple days I've been planning to implement a version of [smcFanControl]("http://homepage.mac.com/holtmann/eidac/software/smcfancontrol2/index.html") for linux  so you can set the min fan speed using a nice graphical tool from your GNOME panel as a normal user rather than having to do a 
```
echo 3000 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
```from the terminal.

Eventually I may extend it to automatically control the min fan speed based on current cpu temperature and power state etc. Let me know what you think and I will post a version of it once I start getting somewhere - should be in a day or two, should take too long as it is pretty similar to as lot of the stuff I've already done with [GNOME Sensors Applet]("http://packages.ubuntu.com/sensors-applet").
I believe there is a switch to just control the fans manually too if you want to implement that as well.

---

### Post by pragmatine on 2009-01-05
> **cyberdork33 said:**
> I believe there is a switch to just control the fans manually too if you want to implement that as well.

By leaving the fans in automatic mode and only setting the min value, we get the best of both worlds - the SMC chip can still increase the fan speed if the temperature gets too high (like over 80C), but by setting the min value the user can tell the SMC chip that it wants the fans no lower than that value, and in general the fans will stay at the value the user sets (assuming the temp does not rise too high) and will definitely not go under that value.

In general I think it is **really unsafe** to disable automatic fan control, since then the SMC chip will not automatically increase the fan speed if the temp gets too high, and this could lead to damage of the machine, and besides as explained above, we don't need to set manual control to actually be able to control the general speed of the fans.

As an aside, I've got most of the basic infrasturcture code in place - since only root can actually set the values we need to split the app into 2 parts which talk over DBus - one which runs as root and just simply controls the hardware (mechanism), and one which runs as the user to provide nice GUI etc and to do stuff like invoke different profiles based on whether on battery or A/C or whatever (policy) - so it should be another day or two and I should have something which others can have a play with - is taking a little longer than I thought as $DAYJOB is taking up most of my time.

---

### Post by mrneil on 2009-01-18
Can anyone help me understand the output from sensors:

$ sensors
applesmc-isa-0300
Adapter: ISA adapter
Left side  :2999 RPM  (min = 3000 RPM)
Right side :2999 RPM  (min = 3000 RPM)
temp1:       +32.0 C                                    
temp2:       +32.0 C                                    
temp3:       +31.8 C                                    
temp4:       +32.2 C                                    
temp5:       +61.5 C                                    
temp6:       +54.0 C                                    
temp7:       +54.2 C                                    
temp8:       +59.5 C                                    
temp9:       +54.5 C                                    
temp10:      +46.8 C                                    
temp11:      +54.0 C                                    
temp12:      +56.5 C                                    
temp13:      +56.8 C                                    
temp14:      +58.5 C                                    
temp15:      +55.8 C                                    
temp16:      +65.0 C                                    
temp17:      +52.5 C                                    
temp18:      +52.0 C                                    
temp19:      +30.5 C                                    
temp20:      +42.5 C                                    

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0 C  (high = +100.0 C, crit = +100.0 C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0 C  (high = +100.0 C, crit = +100.0 C)  

I'm pretty sure temp5 is a processor temperature because it gets much hotter during a kernel compile. I can report that the coretemp-isa values track the temp5 value very closely (I recorded temperatures every 10 seconds while running and cooling down from a kernel compile and examined the correlation), but the coretemp-isa values are typically 15-16 degrees C lower.

I've been using iStatPro [http://www.islayer.com/apps/istatpro/](http://www.islayer.com/apps/istatpro/) to record idle temperatures in Mac OS X. The highest temperature it reports is 46 degrees C. But it is hard to map the names of components onto the temp1-temp20 sensors produces under linux. Which of temp1 to temp20 corresponds to iStatPro's "CPU A" temperature, for example?

Can anyone help here?

---

### Post by cyberdork33 on 2009-01-18
[http://www.mactel-linux.org/wiki/AppleSMC](http://www.mactel-linux.org/wiki/AppleSMC)

EDIT: Sorry that was the wrong link... Though there is useful info there...

kosumi had posted a link to this awhile back, but I didn't find it.

---

### Post by Entwicklung Medizinproduk on 2009-01-18
Try using fan on its back it could help..

---

### Post by joka. on 2009-01-19
I was wondering if someone can update me with what's going on so far in this thread instead of me reading through pages and pages? I got the general idea that Linux is running hot on the MB/MBP's and in return can damage the machine and lower battery life by a lot and people are trying to fix it right now. Are there any improvements? Does this happen to all MB/MBP's or just here and there? I was about to get my MBP the other week, but decided not to because I thought this was a major problem and I'm really interested in installing Linux on the machine.

---

### Post by drunkndog5 on 2009-01-19
I have also been looking into buying a unibody macbook, but am worried about the temperatures, I did some searching and ran across a post which might be of some help, on a Mac website: [http://forums.macrumors.com/showpost.php?p=6907879&postcount=13](http://forums.macrumors.com/showpost.php?p=6907879&postcount=13)  They seem to be claiming that the machine running at 70C CPU and 82C GPU are normal for their machines.  There were several other posts also discussing the new machines running at high temps, are these higher than what people are seeing with Linux?

---

### Post by joka. on 2009-01-19
> **drunkndog5 said:**
> I have also been looking into buying a unibody macbook, but am worried about the temperatures, I did some searching and ran across a post which might be of some help, on a Mac website: [http://forums.macrumors.com/showpost.php?p=6907879&postcount=13](http://forums.macrumors.com/showpost.php?p=6907879&postcount=13)  They seem to be claiming that the machine running at 70C CPU and 82C GPU are normal for their machines.  There were several other posts also discussing the new machines running at high temps, are these higher than what people are seeing with Linux?

That person from the link you listed is ignorant. Her comp is going to break faster than others. An acceptable comp temp [IMO] is under 50-60C. Anything above 60/65C [IMO] is on the warm side... esp when you're not playing any games, video/audio editing, multitasking, etc. Max comp temps for most processors are around 85-95C on average. So about 70-82C listed by that person without doing anything is def running hot. How I see it is that the lower your comp temp, the better it is. I think a lot of people would agree with what I just said.

Also, if you're running Vista which uses more resources... I would understand if it runs a little warmer, but not by much. Linux uses very little resources and should run parallel or close to exact temperatures as OS X.

---

### Post by alexmurray on 2009-01-19
Linux does not necessarily use very little resources - and in general it has a lot worse power management than OSX - I get only about 2 hours battery life in Linux compared to nearly 4 hours with OSX, so I would not say that Linux uses little resources - you could argue it uses twice as much as OSX and hence uses the battery twice as quick. So blanket statements like that are a little misleading.

Also you may notice lower temps in OSX for a number of reasons:

1. In the MBP 5,1 which has both an integrated NVidia 9400M plus a 9600M GT, you can choose to use the 9400M (which is enabled by default) under OSX which runs quite a bit cooler, whereas under Linux you can only use the 9600GT which runs hotter.

2. As noticed earlier the coretemp module reports different temps than the applesmc module for the CPU, so its hard to compare temps if you don't know which sensor is being used under OSX - under linux its easy to know which, but the programs for OSX dont generally say which sensor they are using.

3. As mentioned above OSX seems better at power management and so is probably better tuned overall for using less power and hence generating less heat.

Just some stuff to consider.

---

### Post by joka. on 2009-01-20
> **alexmurray said:**
> Linux does not necessarily use very little resources - and in general it has a lot worse power management than OSX - I get only about 2 hours battery life in Linux compared to nearly 4 hours with OSX, so I would not say that Linux uses little resources - you could argue it uses twice as much as OSX and hence uses the battery twice as quick. So blanket statements like that are a little misleading.

I think you misunderstood the point of this thread though. People are trying to get Linux to run cooler so therefore it would have longer batter life and not just saying it's fine to be running it this warm [60-70C+]. If you haven't noticed the massive amounts of issues from running Linux on any Mac... you need to tweak it a lot in order to get a lot of things running smoothly in Linux. This is 1 of the problem and everyone is arguing that Linux shouldn't be running this hot. Just because Linux "uses twice as much resources" [IMO that statement doesn't seem right...] doesn't mean it would be twice it's temp or half it's battery life.

---

### Post by npfthunfan on 2009-01-20
I have just tried to compare temperatures between OSX and Intrepid... (as mentioned above direct comparison is probably not very precise)... but in general terms...

My GPU is idling at around 70C in Ubuntu whilst in OSX I can't get it to rise above 40C whilst being reasonably intensive.

> 1. In the MBP 5,1 which has both an integrated NVidia 9400M plus a 9600M GT, you can choose to use the 9400M (which is enabled by default) under OSX which runs quite a bit cooler, whereas under Linux you can only use the 9600GT which runs hotter.

This might be true, though I am not certain what my settings are in both OS.

In terms of CPU the idling temperatures are around the same though the temperature in Ubuntu rises very quickly from a couple of minutes gaming (TrackMania through WINE)... after 5mins running that I get to GPU 90C, CPU 80C (which drops to 65C in 10 seconds after closing).

From what I can tell (I havent been able to get a fan monitor) the fan doesn't work harder in OSX, so that would suggest that the problem is in the generation of heat not the controling of it.

---

### Post by cyberdork33 on 2009-01-20
> **npfthunfan said:**
> From what I can tell (I havent been able to get a fan monitor) the fan doesn't work harder in OSX, so that would suggest that the problem is in the generation of heat not the controling of it.
That would be the gist of this thread so far. The driver is scaling the GPU properly so we do not know why it is generating more heat.

---

### Post by npfthunfan on 2009-01-20
What alexmurray said about the difference in graphics Chips appears to be true... Mac OS X has the 9400 enabled while Ubuntu appears to have the 9600M GT enabled... though I am doubtful that it is just this causing a 25C shift in idle temp (now idling - pretty much - at 55C)

---

### Post by joka. on 2009-01-21
I know on my friend's comp he dual boots with XP and Ubuntu with a low end core 2 processor and his average temp is 40C so it can't be Linux's fault and I think it's just the machine itself or needs certain updates.

I'm not sure if this can be useful or related but for my comp that I'm currently using [under Windows XP], if I go onto a certain website [and only that 1 website] where it streams videos using Firefox, my kernel memory and page file usage goes up [monitoring from the windows task manager]. After the page file usage goes above 1gb, my comp is basically frozen and either I have to end the Firefox process to restore it back to normal or if it's gone too far I have to shut down. If I use Internet Explorer to go onto that same website, everything is normal. So I believe this heat problem in Linux is kinda like the same thing. You might need to figure out a way to rewrite a certain part of Linux or the Mac in order to make it work normally.

---

### Post by alexmurray on 2009-01-21
> **joka. said:**
> I know on my friend's comp he dual boots with XP and Ubuntu with a low end core 2 processor and his average temp is 40C so it can't be Linux's fault and I think it's just the machine itself or needs certain updates.

I'm not sure if this can be useful or related but for my comp that I'm currently using [under Windows XP], if I go onto a certain website [and only that 1 website] where it streams videos using Firefox, my kernel memory and page file usage goes up [monitoring from the windows task manager]. After the page file usage goes above 1gb, my comp is basically frozen and either I have to end the Firefox process to restore it back to normal or if it's gone too far I have to shut down. If I use Internet Explorer to go onto that same website, everything is normal. So I believe this heat problem in Linux is kinda like the same thing. You might need to figure out a way to rewrite a certain part of Linux or the Mac in order to make it work normally.
Firstly its well known that the adobe flash plugin for linux is a massive cpu and gpu hog so this is most likely the culprit in this case - and unfortunatlely since it is closed source you cant't really fix it.

Secondly its hard to compare windows xp with OSX since from what I have seen OSX is just better at keeping lower temperatures overall compared to both linux and Windows XP - the question is why? and can we somehow learn from this to make things cooler under Linux

---

### Post by joka. on 2009-01-21
> **alexmurray said:**
> Firstly its well known that the adobe flash plugin for linux is a massive cpu and gpu hog so this is most likely the culprit in this case - and unfortunatlely since it is closed source you cant't really fix it.

I'm not too sure about not being able to fix it. My comp is completely FUBAR and there are certain things I can't do with it, but once in a while I'll use the backup disc to wipe my main hard drive slate clean and reinstall everything including updates. After cleaning it out, I can do those certain things I can't before. I don't really know how to explain my comp to you, but it's really weird. What I've learned is that there's always a way to fix a problem when it comes to computers... or at least a way around it.

---

### Post by cyberdork33 on 2009-01-22
> **joka. said:**
> I'm not too sure about not being able to fix it. My comp is completely FUBAR and there are certain things I can't do with it, but once in a while I'll use the backup disc to wipe my main hard drive slate clean and reinstall everything including updates. After cleaning it out, I can do those certain things I can't before. I don't really know how to explain my comp to you, but it's really weird. What I've learned is that there's always a way to fix a problem when it comes to computers... or at least a way around it.
What he means is that you cannot edit the source to fix the problem in flash.

---

### Post by mrneil on 2009-01-22
A lengthy post, but I think I have made some progress in narrowing down candidate causes for the heat and thus the short battery life:

**Heat difference is not caused by using different graphics cards under Mac OS X and Linux**

I'm using the 9600M GT in both Linux and Mac OS X. My MacBook Pro is much hotter when in Linux than when in Mac OS X. Because I'm using the same graphics chip under both operating systems, we know that Mac OS X is not cooler because it is using a different chip. 

It could be that the Linux 9600M GT driver uses more power then the Mac OS X 9600M GT driver. It could be that under Linux the 9400M chip is running in parallel when under Mac OS X the 9400M is disabled.

**Too hot when idling**

The increased heat happens even with no programs running, and so it is nothing to do with Adobe Flash or any other program. 

I've got CPU and GPU scaling running in Linux well as every other power saving tip I can find.

**In fact, Linux is too hot even when virtually nothing is running**

I ran some tests earlier this evening. I booted up in single user mode. I stopped as many processes as possible (see output of ps ax at end of post). I removed as many kernel modules as possible (see output of lsmod at end of post). top reveals that there is virtually no CPU usage. The Macbook Pro is no cooler under these conditions (see sensors output at end of post). What can we conclude? 

First, the heat is not caused by anything to do with X. X wasn't running. Similarly Gnome, Firefox or Iceweasel, or any other user program you care to choose is not the cause.

Second, the heat is not caused by the NVIDIA kernel module, as the module was not loaded. (Though it remains possible that the hardware defaults to high power consumption and that the Mac OS X driver is sucessfully changing this default but the Linux module is not.)

**Power consumption, not cooling, is the problem**

The problem is about power consumption and not cooling. When the Macbook gets too hot in Linux (e.g., in a kernel compile), the fan speed increases and cools the system, so we know that there is no cooling problem. The problem is that a lot of heat is being generated in the first place. This heat energy must be coming from somewhere, and the only source is the battery. Until we can identify which component the heat is coming from and which bit of source code is causing the component to heat up, we can't fix the problem.

**lsmod, ps ax, top, and sensors output**

$ ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 init [S]
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00 [migration/0]
    4 ?        S<     0:00 [ksoftirqd/0]
    5 ?        S<     0:00 [watchdog/0]
    6 ?        S<     0:00 [migration/1]
    7 ?        S<     0:00 [ksoftirqd/1]
    8 ?        S<     0:00 [watchdog/1]
    9 ?        S<     0:00 [events/0]
   10 ?        S<     0:00 [events/1]
   11 ?        S<     0:00 [khelper]
   46 ?        S<     0:00 [kblockd/0]
   47 ?        S<     0:00 [kblockd/1]
   49 ?        S<     0:00 [kacpid]
   50 ?        S<     0:00 [kacpi_notify]
  170 ?        S<     0:00 [ksuspend_usbd]
  176 ?        S<     0:00 [khubd]
  179 ?        S<     0:00 [kseriod]
  224 ?        S      0:00 [pdflush]
  225 ?        S      0:00 [pdflush]
  226 ?        S<     0:00 [kswapd0]
  227 ?        S<     0:00 [aio/0]
  228 ?        S<     0:00 [aio/1]
  799 ?        S<     0:00 [ata/0]
  802 ?        S<     0:00 [ata/1]
  804 ?        S<     0:00 [ata_aux]
  843 ?        S<     0:00 [khpsbpkt]
  941 ?        S<     0:00 [knodemgrd_0]
  960 ?        S<     0:00 [scsi_eh_0]
  961 ?        S<     0:00 [scsi_eh_1]
  962 ?        S<     0:00 [scsi_eh_2]
  963 ?        S<     0:00 [scsi_eh_3]
  964 ?        S<     0:00 [scsi_eh_4]
  965 ?        S<     0:00 [scsi_eh_5]
 1176 ?        S<     0:00 [kjournald]
 1915 ?        S<     0:00 [btaddconn]
 1916 ?        S<     0:00 [btdelconn]
 2340 ?        S<     0:00 [applesmc-led]
 2716 tty1     Ss     0:00 init [S]
 2719 tty1     S      0:00 bash
 3017 tty1     R+     0:00 ps ax

$lsmod

Module                  Size  Used by
xt_tcpudp               7680  3
iptable_filter          7424  1
ip_tables              21520  1 iptable_filter
x_tables               25224  2 xt_tcpudp,ip_tables
fuse                   53184  1
coretemp               11008  0
applesmc               31940  0
led_class               8968  1 applesmc
input_polldev           8720  1 applesmc
acpi_cpufreq           11792  1
freq_table              9344  1 acpi_cpufreq
loop                   19468  0
hci_usb                18460  0
bluetooth              57124  1 hci_usb
ext3                  125072  1
jbd                    51240  1 ext3
mbcache                12804  1 ext3
sd_mod                 29376  3
ide_pci_generic         9220  0 [permanent]
ide_core              128284  1 ide_pci_generic
usbhid                 45664  0
hid                    42304  1 usbhid
ff_memless              9224  1 usbhid
ahci                   33036  2
ohci1394               32564  0
ieee1394               93816  1 ohci1394
libata                165472  1 ahci
scsi_mod              160760  2 sd_mod,libata
dock                   14112  1 libata
ohci_hcd               25092  0
thermal                22688  0
processor              42304  4 acpi_cpufreq,thermal
fan                     9352  0
thermal_sys            17728  3 thermal,processor,fan

$sensors

applesmc-isa-0300
Adapter: ISA adapter
Left side  :1999 RPM  (min = 2000 RPM)
Right side :2001 RPM  (min = 2000 RPM)
temp1:       +32.0 C
temp2:       +32.0 C
temp3:       +31.2 C
temp4:       +32.2 C
temp5:       +71.2 C
temp6:       +62.2 C
temp7:       +63.2 C
temp8:       +69.5 C
temp9:       +61.8 C
temp10:      +53.0 C
temp11:      +62.2 C
temp12:      +67.0 C
temp13:      +66.2 C
temp14:      +68.2 C
temp15:      +64.2 C
temp16:      +65.0 C
temp17:      +61.2 C
temp18:      +59.5 C
temp19:      +29.2 C
temp20:      +46.0 C

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +59.0 C  (high = +100.0 C, crit = +100.0 C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +58.0 C  (high = +100.0 C, crit = +100.0 C)

---

### Post by joka. on 2009-01-23
> **cyberdork33 said:**
> What he means is that you cannot edit the source to fix the problem in flash.

err I meant maybe there's a way to go around it... not necessarily edit/change it.

Nice detailed post mrneil. You're right... it has to do with power consumption and not cooling... also you gotta figure out where the heat is coming from in the first place in order to fix it.

Another idea I have is that it might be the hardware/wiring. I've noticed how a lot of people said the new MBP 5,1 are different from the old ones in a lot of ways so maybe the wiring is also different. The new MBP could be using more or less energy to power up certain things and Linux on the other hand [I don't think] has changed that much so when installed, it [the script/programing of Linux] could be in need or using more energy than needed and therefore causing this heat? If someone can figure out the energy consumption of the old MBP vs. MBP 5,1 and/or old and new versions of Linux you might? see a difference. If that is the case maybe you can re-route the energy and/or change it. Just throwing it out there and thinking outside the box. Everyone has been so focused on 1 or 2 aspects that no one has really looked elsewhere.

---

### Post by cyberdork33 on 2009-01-23
> **joka. said:**
> Another idea I have is that it might be the hardware/wiring. I've noticed how a lot of people said the new MBP 5,1 are different from the old ones in a lot of ways so maybe the wiring is also different. The new MBP could be using more or less energy to power up certain things and Linux on the other hand [I don't think] has changed that much so when installed, it [the script/programing of Linux] could be in need or using more energy than needed and therefore causing this heat? If someone can figure out the energy consumption of the old MBP vs. MBP 5,1 and/or old and new versions of Linux you might? see a difference. If that is the case maybe you can re-route the energy and/or change it. Just throwing it out there and thinking outside the box. Everyone has been so focused on 1 or 2 aspects that no one has really looked elsewhere.
The problem with that is that people have been complaining about how the MacBook (Pro) is hotter in Linux than in OSX since I have been in this forum... This is not a new development on the 5,1 revision.

---

### Post by npfthunfan on 2009-01-23
erm... it terms of the battery causing heat... the only time I've known batteries to get hot is when they are short circuited... so a battery producing heat would be a hardware fault and as this does not happen in OS X then why in Linux?

As an aside I can't seem to get applesmc to work... i downloaded the package etc... there's probs something I've missed out...

---

### Post by mrneil on 2009-01-24
npfthunfan, I'm not arguing that the battery itself is malfunctioning under Linux and causing heat. Certainly the battery is not at all hot on my MacBook Pro 5,1. So I completely agree with you that the battery is not the cause of our problems.

I'm arguing that some unknown component (perhaps the CPU) is malfunctioning under Linux and producing too much heat. Physics tells us that the heat energy must be coming from somewhere, and the only place is the energy can come from is the battery. Thus, some currently unknown component produces too much heat under Linux, drawing more energy from the battery than under Mac OS X. So, under Linux, the MacBook is too hot and has terrible battery life.

I'm off to run some more tests...

---

### Post by mrneil on 2009-01-24
I wanted to check that CPU frequency scaling is indeed working. My concern is that although /sys interface reports that scaling is working, that the processor is always at full power. It turns out that this concern is wrong.

With /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor set to powersave, /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq reports a frequency of 1596000 Hz. With sys/devices/system/cpu/cpu0/cpufreq/scaling_governor set to performance, /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq reports a frequency of 2527000. This means that code should run 2527000/1596000 = 1.58 times faster with performance compared to powersave.

To test this I wrote a short c program that promotes itself to FIFO (so it is not interupted) and locks itself in memory (so it is not swapped to disk). The program uses the gettimeofday() system call. In short, the program is measuring timings accurately. By comparing the time to complete 1,000,000 integer increments with the time taken to complete 100,000,000 integer increments, I was able to work out the time taken for a single increment. I did this under each CPU frequency.

I found that it takes 0.0043 microseconds to run an increment at 
1596000 Hz and 0.0027 microseconds to run an increment at 2527000 Hz. Thus, performance is indeed 1.58 times faster under performance compared to powersave.

To conclude, CPU frequency scaling is working correctly. I'm off to find out whether the 2.53GHz Intel Core 2 Duo has any other power saving features...

---

### Post by joka. on 2009-01-24
> **mrneil said:**
> npfthunfan, I'm not arguing that the battery itself is malfunctioning under Linux and causing heat. Certainly the battery is not at all hot on my MacBook Pro 5,1. So I completely agree with you that the battery is not the cause of our problems.

I'm arguing that some unknown component (perhaps the CPU) is malfunctioning under Linux and producing too much heat. Physics tells us that the heat energy must be coming from somewhere, and the only place is the energy can come from is the battery. Thus, some currently unknown component produces too much heat under Linux, drawing more energy from the battery than under Mac OS X. So, under Linux, the MacBook is too hot and has terrible battery life.

I'm off to run some more tests...

That was what I was trying to say in my other post. I'm bad at wording things.

---

### Post by alexmurray on 2009-01-24
> **mrneil said:**
> I wanted to check that CPU frequency scaling is indeed working.....

To conclude, CPU frequency scaling is working correctly. I'm off to find out whether the 2.53GHz Intel Core 2 Duo has any other power saving features...
It would be interesting to see if under OSX you got similar results since at least one person seems to [believe]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550/comments/53") that the CPU is actually scaled down to 800Mhz in OSX - if you could prove whether this was the case or not that might indeed be the culprit.

Also I've been wondering if perhaps the  Nvidia drivers for OSX are more aggressive in their power saving - I've noticed in nvidia-settings that if you enable overclocking you can actually drop the clock rate of the GPU from 160Mhz all the way back to 42Mhz, although I have not tried as I don't really want to void my warranty, but this could also really help.

In conclusion I doubt any specific component is malfunctioning under Linux, its just that OSX has most likely been developed to take advantage of all the different power saving features of the hardware (since Apple designs the hardware build and writes the software for it they can probably optimise a lot of things) but since Linux is much more generic and can run on all kinds of hardware, from embedded processors all the way to clustered super-computers it is just not so optimised for power saving.

---

### Post by ercoppa on 2009-01-24
Under OSX I launch some apps that shows CPU status and the only steps are:
- 2.00 GHz
- 1.86 GHz
- 1.60 GHz
So I don't think that exists a 800 MHz step. 

Greets, ercoppa.

---

### Post by Nikos.Alexandris on 2009-01-24
@mrneil: excellent work! Thanks for the tests you have ran.

Kind regards, Nikos

---

### Post by Nikos.Alexandris on 2009-01-24
> The problem is about power consumption and not cooling. When the Macbook gets too hot in Linux (e.g., in a kernel compile), the fan speed increases and cools the system, so we know that there is no cooling problem. The problem is that a lot of heat is being generated in the first place. This heat energy must be coming from somewhere, and the only source is the battery. Until we can identify which component the heat is coming from and which bit of source code is causing the component to heat up, we can't fix the problem.

FWIW, I use my MBP5,1 without the battery. And I still find it's hot(ter than when booting on OSX once and a while to check for updates).

---

### Post by cyberdork33 on 2009-01-24
> **Nikos.Alexandris said:**
> FWIW, I use my MBP5,1 without the battery. And I still find it's hot(ter than when booting on OSX once and a while to check for updates).
I think they whole point is that more power is being used, thus there is more heat dissapation required, the source of the power isn't relevant.

This, of course, completely make sense if you also consider the fact that the battery life is poorer under Ubuntu than in OSX.

---

### Post by joka. on 2009-01-25
This shows that the problem has to do with Linux and not the MBP or OS X. You just have to find out which part of the comp is using more power, which people seem to have a problem to identifying it. Most likely, if someone can identify the part that's using more energy, you can fix it by possibly editing some code? Using the sensors seem to be the best bet, but that's also another problem where people can't identify which sensor is for what.

---

### Post by mrneil on 2009-01-26
I've been over to the MacOS X side and repeated my speed tests. It seems that the test runs just slightly faster than on Linux, and thus that MacOS X is running the processor no slower than in Linux. 

I used the same version of gcc and no optimization, as under Linux. I couldn't make the scheduling and memory lock work so I ran the tests without them. I found a time of 0.0034 microseconds per loop. <a href="http://www.coolbook.se/CoolBook.html">CoolBook</a> reported a processor frequency of 1602 MHz. 

0.0034 microseconds per loop in MacOS X compares with 0.0043 microsecond per loop at 1.6 GHz in Linux. The fact that MacOS X is slightly faster means that MacOS X is not idling the processor at a lower frequency.

CoolBook also revealed 1869, 2136, 2403, and 2536 MHz as available frequencies. This matches the contents of /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies under Linux. This agrees with above reports that frequencies below 1.6 GHz are not happening either on Linux or MacOS X.

In summary, I'd conclude that MacOS X is scaling the CPU frequency in the same way as Linux. I think we need to look elsewhere for the solution. 

I'll start some tests on the NVIDIA drivers as I see the latest driver supports the 9400M. I'll also look at front side bus frequencies (though this seems unlikely as the processor frequency would be reduced if the FSB frequency were lower). If anyone has 
tips for accessing or controlling FSB frequency under Linux that would be useful. My gooling has not brought anything up.

---

### Post by Nikos.Alexandris on 2009-01-26
> **mrneil said:**
> 
[...]
In summary, I'd conclude that MacOS X is scaling the CPU frequency in the same way as Linux. I think we need to look elsewhere for the solution. 

I'll start some tests on the NVIDIA drivers as I see the latest driver supports the 9400M. I'll also look at front side bus frequencies (though this seems unlikely as the processor frequency would be reduced if the FSB frequency were lower). If anyone has 
tips for accessing or controlling FSB frequency under Linux that would be useful. My gooling has not brought anything up.

FWIW, I never really believed it's the processor. I am no engineer, nor a professional hardware hacker. But just by looking what is there where it's so hot (left side) I thought it has to do with the graphic card(s).

Also (a silly thought perhaps but...) on the left are all "connections" located (power supply, usb's, etc.). There must be something software-driven piece which Linux "ignores"(?).

Nikos

---

### Post by alexmurray on 2009-01-26
As a professional software engineer who works daily with power management in portable devices running Linux, I'd say the first place to look is at the GPU (and also as others have mentioned it appears to be the biggest source of heat in the machine) - I expect that it could be some of the following:

OSX does better power management of the GPU an in general it uses less power (since they build the machine I'd say this is likely the case) - as I mentioned in an earlier post perhaps the GPU is underclocked in OSX when idle?

Under Linux only the 9600M GT is detected, whereas OSX knows about the 9400M as well - perhaps both the 9600M GT and 9400M are powered up under linux so the 9400M is always on drawing some power even if its not being used.

There could be many other things with the GPU but since it and its driver are proprietary there is not a whole lot which can probably be done to fix / change things.

---

### Post by Nikos.Alexandris on 2009-01-26
> **alexmurray said:**
> As a professional software engineer who works daily with power management in portable devices running Linux, I'd say the first place to look is at the GPU (and also as others have mentioned it appears to be the biggest source of heat in the machine) - I expect that it could be some of the following:

OSX does better power management of the GPU an in general it uses less power (since they build the machine I'd say this is likely the case) - as I mentioned in an earlier post perhaps the GPU is underclocked in OSX when idle?

Under Linux only the 9600M GT is detected, whereas OSX knows about the 9400M as well - perhaps both the 9600M GT and 9400M are powered up under linux so the 9400M is always on drawing some power even if its not being used.

There could be many other things with the GPU but since it and its driver are proprietary there is not a whole lot which can probably be done to fix / change things.

If there are other machines with the same GPU's on-board, perhaps it would make sense to check/compare their performance and why not send a request to NVidia asking about the performance of the linux-driver?

It's more than nothing to know at least that this is the problem.

Cheers, Nikos

---

### Post by joka. on 2009-01-26
I was reading some of the comments and an idea came up. Maybe while running OS X, everything is running... BUT when running Linux, something isn't running [either a script of some sort or hardware]. Something that isn't running can definitely throw off a lot of things and possibly cause the heat.

---

### Post by alexmurray on 2009-01-26
After looking around a bit more it seems that this is not specific to Linux - many people running Windows on their MacBook (Pro) 's seem to have the same sorts of temperature problems:

[http://www.macwindows.com/keep_vista_cool_bootcamp.html](http://www.macwindows.com/keep_vista_cool_bootcamp.html)
[http://discussions.apple.com/thread.jspa?messageID=8512850](http://discussions.apple.com/thread.jspa?messageID=8512850)
[http://discussions.apple.com/thread.jspa?threadID=1837836&tstart=0](http://discussions.apple.com/thread.jspa?threadID=1837836&tstart=0)
[http://discussions.apple.com/thread.jspa?messageID=8744562](http://discussions.apple.com/thread.jspa?messageID=8744562)
[http://forums.macrumors.com/showthread.php?t=596992](http://forums.macrumors.com/showthread.php?t=596992)

At least one thing that is common is that for both Linux and Windows, neither can see the 9400M, only the 9600M GT - so to me this tends to make me think that perhaps the 9400M is still on, generating heat but not being actively used, in both Linux and Windows.

---

### Post by alexmurray on 2009-01-26
Also looks unlikely that we'll ever be able to just use the 9400M instead of the 9600M GT:

[http://support.apple.com/kb/TS2457](http://support.apple.com/kb/TS2457)
[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=2243&p_created=1224019013&p_sid=SxxZcpjj&p_accessibility=0&p_redirect=&p_lva=2243&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSwxJnBfcHJvZHM9MCZwX2NhdHM9MCZwX3B2PSZwX2N2PSZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9bWFjYm9vaw**&p_li=&p_topview=1](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=2243&p_created=1224019013&p_sid=SxxZcpjj&p_accessibility=0&p_redirect=&p_lva=2243&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSwxJnBfcHJvZHM9MCZwX2NhdHM9MCZwX3B2PSZwX2N2PSZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9bWFjYm9vaw**&p_li=&p_topview=1)

---

### Post by joka. on 2009-01-27
I was so close to getting the new MBP 5,1. All the bugs were getting fixed for Linux and looked like it got all it's ducks in a row, but now this heat problem is a huge deal for me because I don't plan on using OS X at all. It doesn't look very appetizing at this point. I'm going have to re-evaluate everything. **Epic Fail** for Apple as always. Expect the customers to pay the premium and they get only mid-grade quality in return.

---

### Post by joka. on 2009-01-27
Is the temp at/around 70C when you're doing nothing or is that when you're using programs and such? Is the battery life the same for Windows as it is for Linux [2 hours from what I heard compared to OS X which is around 5]? If you cool the comp [using an external laptop fan/pad or putting it in a very cold room] does it still have short battery life?

---

### Post by alexmurray on 2009-01-27
> **joka. said:**
> Is the temp at/around 70C when you're doing nothing or is that when you're using programs and such? Is the battery life the same for Windows as it is for Linux [2 hours from what I heard compared to OS X which is around 5]? If you cool the comp [using an external laptop fan/pad or putting it in a very cold room] does it still have short battery life?
I have the 2.4Ghz Macbook Pro 5,1 and my cpu temp is at 55C when idle, and the GPU temp is usually around 72C. Whilst the GPU temp is higher than OSX, the CPU temp is roughly the same, and I am still quite happy with these temps - I'd prefer slightly cooler but its not a deal breaker for me.

Battery life is same as Windows - 2 hours. External cooling doesn't change the power consumption of the machine and hence won't have any effect on battery life, it should just make it slightly cooler to use.

---

### Post by drunkndog5 on 2009-01-27
> **alexmurray said:**
> 
At least one thing that is common is that for both Linux and Windows, neither can see the 9400M, only the 9600M GT - so to me this tends to make me think that perhaps the 9400M is still on, generating heat but not being actively used, in both Linux and Windows.

If it were the case of both GPUs running wouldn't that mean that the macbook, which only has one GPU, would not be having these heating problems?  At least in my reading through this thread I was under the impression that both the macbook and macbook pro have this overheating problem, is that correct?

I ask as I am interested in purchasing a macbook, but the heating & short battery life in Linux has me leaning other ways.

Thanks,
Neil

---

### Post by ercoppa on 2009-01-27
> If it were the case of both GPUs running wouldn't that mean that the macbook, which only has one GPU, would not be having these heating problems? At least in my reading through this thread I was under the impression that both the macbook and macbook pro have this overheating problem, is that correct?
Yes, you say right. The MacBook is hot (in OS X never hot) in the left-side, but I think less that MBP. 

Battery life (with wireless, no bluetooth, medium brightness):
- Mac OS X --> 5,5 hour
- Ubuntu -> 2-2,5

So I think that for MPB the double GPU it's not the _main_ cause of worse battery life under GNU/Linux.

Greets, ercoppa.

---

### Post by alexmurray on 2009-01-27
Hmm thats a good point. So odds-on with the MBP the 9400M is disabled then and hopefully not drawing power.

---

### Post by Nikos.Alexandris on 2009-01-27
> **alexmurray said:**
> Hmm thats a good point. So odds-on with the MBP the 9400M is disabled then and hopefully not drawing power.

So it seems that the problem is not the 9400 GPU since it's not even recognized by linux. Still there is a 2hours gap between OSX [*] and Linux.

What on the earth can be the powerdrainer? Can somebody provide some advanced steps to just disable every little thing that is working on linux and keep only the processor, the GPU, the display at minimum... ? No wireless, no bluetooth, no IR, no ethernet wake-ups, nothing else than just the *very* basic.

Step-By-Step trying to identify the "leak". Or isn't this the way to go?

Bad Apple... ;-) Maybe they "instructed", hard-locked some code, to power-drain the machine when working with winboxes or else. Who knows... ?

Cheers, Nikos
---
[*] OSX achieves ~4hours when working with the 9600GPU.

---

### Post by cyberdork33 on 2009-01-27
> **joka. said:**
> ...this heat problem is a huge deal for me because I don't plan on using OS X at all.
Then why not buy a computer that was designed with Linux (even Ubuntu) in mind?

---

### Post by joka. on 2009-01-27
> **cyberdork33 said:**
> Then why not buy a computer that was designed with Linux (even Ubuntu) in mind?

Oh come on now I'm sure you've seen some of the laptops out right now. Either they have uber bobo shapes or they have crap specs in the case. Laptops with pretty nice specs [not top of the line performance but at least on an enthusiastic level] just cost way too much. I was also looking at Alienware and was able to get pretty nice specs. The Only problem is shipping + tax which boost it up another $250+. I'm a college student [aka I'm broke :cry:] so Apple gives me 8% off their laptops but adding tax back on it's basically I get tax off from the comps I buy... still pretty good. I'm not in a huge hurry to get a new comp even tho my current comp is 7 years old :evil::shock:. I can manage and wait a couple of months to see what happens.

On the side note... just looked at Apple's website and they're now selling the new 17" MBP 5,1. Add $300 for better resolution 1920x1200, 2.66GHz, 1 more USB port, 2" to your screen, and 8 hours for battery life... but the battery is not removable? "Built-in 95-watt-hour lithium-polymer battery" compared to the 15"... "Removable 50-watt-hour lithium-polymer battery"

Other options:
2.93GHz Intel Core 2 Duo [Add $300.00]... and yet it's still not a Core 2 Extreme... Apple fails.
8GB 1066MHz DDR3 SDRAM - 2X4GB **[Add $1,200.00]**... wahaha are you serious? $1200???
MacBook Pro 17-inch Hi-Resolution **Antiglare** Widescreen Display [Add $50.00]... felt this should of been a free preference option

---

### Post by cyberdork33 on 2009-01-27
> **joka. said:**
> Oh come on now I'm sure you've seen some of the laptops out right now. Either they have uber bobo shapes or they have crap specs in the case. Laptops with pretty nice specs [not top of the line performance but at least on an enthusiastic level] just cost way too much. I was also looking at Alienware and was able to get pretty nice specs. The Only problem is shipping + tax which boost it up another $250+. I'm a college student [aka I'm broke :cry:] so Apple gives me 8% off their laptops but adding tax back on it's basically I get tax off from the comps I buy... still pretty good. I'm not in a huge hurry to get a new comp even tho my current comp is 7 years old :evil::shock:. I can manage and wait a couple of months to see what happens.
Doesn't sound like you are broke if you are trying to get a high-performance laptop like Alienware...

Either way, there are several vendors that offer Linux compatible systems. You should check them out. System76 has a large range of machines, and of course Dell has some offerings now among others.

---

### Post by joka. on 2009-01-28
> **cyberdork33 said:**
> Doesn't sound like you are broke if you are trying to get a high-performance laptop like Alienware...

Limit is about $2500... yea a little more than what the average laptop cost, but [sounding like a spoiled child] parents are helping me pay for **some** of it and I'm paying for the rest. I figured that I haven't got a new comp since 6-7 years ago and I won't be getting another 1 for a long time so might as well step it up a little.

Just curious tho... I've heard many different answers for this question: if you leave your laptop plugged in or if you keep charging the battery does it mess up the battery life faster?

Also if anyone can tell me how their experience is with using Windows and playing games? How hot does it run and does the heat affect anything? I intend on playing games a little and doing video/audio editing once in a while along with using Adobe programs like Photoshop. Also with windows, does it have the multi-touch?

---

### Post by mrneil on 2009-01-28
My goal is to use the 9400M instead of the 9600M GT NVIDIA card under linux to improve battery life. The latest stable NVIDIA Linux driver now supports the 9400M. 

[http://www.nvidia.com/object/linux_display_amd64_180.22.html](http://www.nvidia.com/object/linux_display_amd64_180.22.html)

But lspci only lists the 9600M GT.

lspci
...
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
...

The suggestion is that, for Linux and Windows, EFI (the replacement for BIOS) is turning the 9400 M off at boot. So two questions:

1. Does anyone have a MacBook Pro 5,1 and is running Linux without using BootCamp and instead using an EFI boot loader? Perhaps EFI is not disabling the 9400 M at boot on these machines? If you did this, perhaps you could post the output of lspci for us please.

2. Does anyone know how to alter EFI behaviour, either at boot or run time, so that we can enable the 9400 M.

---

### Post by cyberdork33 on 2009-01-28
> **mrneil said:**
> The suggestion is that, for Linux and Windows, EFI (the replacement for BIOS) is turning the 9400 M off at boot. So two questions:

1. Does anyone have a MacBook Pro 5,1 and is running Linux without using BootCamp and instead using an EFI boot loader? Perhaps EFI is not disabling the 9400 M at boot on these machines? If you did this, perhaps you could post the output of lspci for us please.

2. Does anyone know how to alter EFI behaviour, either at boot or run time, so that we can enable the 9400 M.

Here is my recommendation... If someone tried this and I missed it, sorry.

Boot OSX and change the video device to the 9400M (however you do that). Once it is done, reboot (do not shutdown!) into Ubuntu and see if the same hardware is active. 

Also, information on starting via EFI is here:
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

Note that 3D acceleration does not work when booting via EFI into Linux on older machines, so we know there are some graphics initialization issues that EFI-booting does not do for us. That is likely unfortunate for this experiment...

---

### Post by mrneil on 2009-01-28
Good idea cyberdork33. I've just booted into MacOS X, where I am running the 9400M. I then rebooted without shutting the MacBook Pro down and started Linux. Unfortunately lspci only reports the 9600M GT. I did lspci both before the nvidia module was loaded and after the module was loaded, and so we know that the nvidia module is not responsible for masking the 9400M.

I also experimented with the EFI shell option in rEFIt. This is available from the rEFIt boot menu before either MacOS X or Linux start. The pci command lists pci devices. Both after a cold start and after rebooting from MacOS X, these two entries appear (and fortunately they appear at the end of the list, as I can't work out how to scroll back in the EFI shell):

pci 
00 02 00 00 => Display Controller - VGA 8514 controller
   Vendor 1ODE Device 0647 Prog Interface 0

00 03 00 00 => Display Controller - VGA 8514 controller
   Vendor 1ODE Device 0863 Prog Interface 0

(Note, you can see other EFI shell commands here [http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/))

It looks like the first entry refers to the 9600M GT as it seems to match the output of lspci in Linux.

lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)

The second entry is presumably the 9400M. What to conclude? Well I guess at boot both the 9600M GT and the 9400M are available, either after a cold start or after a reboot from MacOS X. Then something happens in the hand over between rEFIt and Grub when booting Linux, such that the 9400M no longer appears. Presumably there is a problem in simulating the BIOS. If anyone has any more ideas, they'd be really welcome!

---

### Post by mrneil on 2009-01-28
Reading the rEFIt documentation here [http://refit.sourceforge.net/myths/]("http://refit.sourceforge.net/myths/"), it seems the cause is likely to be the Apple firmware. The Apple firmware seems to be responsible for BIOS compatibility mode. I'm off to learn more about this...

---

### Post by cyberdork33 on 2009-01-28
> **mrneil said:**
> (Note, you can see other EFI shell commands here [http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/))Just a note that the Intel specs are not fully compatible. You can type 'help' in the shell to get a list of commands though. Theoretically, you can mount a filesystem there and everything, but I haven't figured that one out yet. There is also a way to change the console resolution which escapes me at the moment... I think it might be the 'mode' command.

> **mrneil said:**
> The second entry is presumably the 9400M. What to conclude? Well I guess at boot both the 9600M GT and the 9400M are available, either after a cold start or after a reboot from MacOS X. Then something happens in the hand over between rEFIt and Grub when booting Linux, such that the 9400M no longer appears. Presumably there is a problem in simulating the BIOS. If anyone has any more ideas, they'd be really welcome!Too bad... 

> **mrneil said:**
> Reading the rEFIt documentation here [http://refit.sourceforge.net/myths/](http://refit.sourceforge.net/myths/), it seems the cause is likely to be the Apple firmware. The Apple firmware seems to be responsible for BIOS compatibility mode. I'm off to learn more about this...
yes. So I am guessing that you cannot use the other gpu in windows either since it also boots from the BIOS emulator...

That being said, it can likely only be enabled when booting via an EFI bootloader, but we would still need to find out what efi variable or whatever is the switch to change between the two.

---

### Post by joka. on 2009-01-29
Hey anyone mind telling me what the temp is when you're actually using the comp [CPU and GPU]? either for video/audio editing or playing games? I can probably find it somewhere in this thread but too much info to sort through.

and I know this isn't related in this post but does the multi-touch work in Windows?

---

### Post by alexmurray on 2009-01-29
Under OSX the 9400M is listed as a PCI device, whereas the 9600M GT is listed as PCI-Express, so perhaps when booting the PCI bus is simply disabled somehow?? Will keep investigating.

---

### Post by della on 2009-01-29
I managed to get the temperature of the GPU perceptibly lower (down to 63-64°C doing non-intensive stuff) by forcing its clock at the lowest speed. Looks like the nVidia driver is too aggressive when scaling up the clock frequency, at least under normal Compiz operation.

To force the graphic device at the lowest speed when on battery, you can add the line

```
Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3"
```

in the "Device" section of /etc/X11/xorg.conf . To force lowest speed always, use instead

```
Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x3"
```

Of course, this comes at the expense of lower graphic performance.

---

### Post by drunkndog5 on 2009-01-30
> **della said:**
> I managed to get the temperature of the GPU perceptibly lower (down to 63-64°C doing non-intensive stuff) by forcing its clock at the lowest speed. Looks like the nVidia driver is too aggressive when scaling up the clock frequency, at least under normal Compiz operation.


Does this help with battery life as well?

---

### Post by paoletto on 2009-01-31
Here another user who would like to get a macbook, but who will wait until this problem of battery life and pm is fixed ;)

I'll stay with my vaio for the moment.
Apple, if you are tuned, please consider to fix this little issue.. You will never gain market share if your notebooks work poorly on windows and linux. Many people just cant use only osX ;)

---

### Post by della on 2009-02-02
> **drunkndog5 said:**
> Does this help with battery life as well?

It has to, since less power is channeled through the graphic card. However, I'm still around two hours...

---

### Post by alexmurray on 2009-02-02
> **paoletto said:**
> Here another user who would like to get a macbook, but who will wait until this problem of battery life and pm is fixed ;)

I'll stay with my vaio for the moment.
Apple, if you are tuned, please consider to fix this little issue.. You will never gain market share if your notebooks work poorly on windows and linux. Many people just cant use only osX ;)
Sorry but do you really think Apple care? They WANT people to ONLY use OSX, that way they can sell you their software for OSX and your ipod for OSX etc etc and make more money from you - they don't want you to use Ubuntu or any other OS for that matter (not even Windows really).

Also I doubt they read these forums :)

However, while my MBP 5,1 runs slightly hotter in Ubuntu than OSX I don't consider this a real problem. Overall I am quite happy with how Ubuntu runs on it.

---

### Post by della on 2009-02-03
> **alexmurray said:**
> Sorry but do you really think Apple care? They WANT people to ONLY use OSX, that way they can sell you their software for OSX and your ipod for OSX etc etc and make more money from you - they don't want you to use Ubuntu or any other OS for that matter (not even Windows really).


Actually, why shouldn't they worry? They make most of their money from hardware anyway, and the fact that Intel Macs also run Windows (either with dual-boot or with virtual machines) is a major motivation for many people to switch to Mac, and that helps them sell lots more. Of course, free software users like us are a much smaller part of their market share, so they care much less about us. This is one of the few cases where the presence of Windows (and the fact that it actually has the same problem) helps us :)

---

### Post by panosher on 2009-02-05
Any news about the "heat Prob" ???

---

### Post by sharon.gmc on 2009-02-06
to me my macbook runs hotter than any pc laptop ive used... and i've used dell, ibm, hp, and acer.

---

### Post by della on 2009-02-07
> **sharon.gmc said:**
> to me my macbook runs hotter than any pc laptop ive used... and i've used dell, ibm, hp, and acer.

Take into account that aluminium feels hotter than plastic even when the temperature is the same.

---

### Post by cyberdork33 on 2009-02-07
> **della said:**
> Take into account that aluminium feels hotter than plastic even when the temperature is the same.
darn heat transfer coefficients

---

### Post by evilidler on 2009-02-07
I just tried installing on my Macbook, and the temperatures were dangerously hot. I know how hot it gets when working intensely under OS X, and this is far worse.

When rebooting back into OS X, CPU A and heatsink A were 65 degrees, according to iStat Menus. That's after shutting down (Ubuntu couldn't reboot on its own) and restarting, so it took a while. I dare not abuse my laptop this way, so Ubuntu stays in a VM for now.

---

### Post by Nikos.Alexandris on 2009-02-07
I experience the same high(er) temperatures like we all do. But I don't think they are too high and put in danger the machine. In fact, since some update a month or more ago, it feels more "stable". I really enjoy working on this machine (=MBP5,1) with Ubuntu.

Nikos

---

### Post by alexmurray on 2009-02-08
I agree - is a bit hotter in Ubuntu but is still a great OS.

---

### Post by buntuLo on 2009-02-08
hey people, nobody speeding up the fans in here? with min speed 3500 the brick is definitely cooler. and i prefer risking to burn a fan after one year (hopefully able to replace it myself..), then having to replace cpu or graphic card.
what are your settings for the fans and eventually which other tricks suggested by PowerTop did you use? cheers, Lo.

---

### Post by Nikos.Alexandris on 2009-02-08
Another important thing to note is the underlying surface (material of your desk!). Usually I work upon an a wooden table covered with some synthetic layer. When I lift up the laptop (BTW: the table feels like you could boil water on it ;-)) the fans spin smoothly down. When I let the machine work intensive stuff I usually place it upon some "holders". It really makes a difference. It does NOT feel too hot like when it's sitting on the table.

I am considering to obtain some "airy" laptop holder. But then there is the wrist-position issue (ergonomy, health, etc.) when typing for a long time.

Nikos

---

### Post by buntuLo on 2009-02-08
> **Nikos.Alexandris said:**
> When I let the machine work intensive stuff I usually place it upon some "holders". It really makes a difference. Nikos
my old laptop used to sit on two rubber feet, with an external psu-fan powered by usb, running slowly and silently with 5v instead of 12v. just perfect.
> **Nikos.Alexandris said:**
> I am considering to obtain some "airy" laptop holder. But then there is the wrist-position issue (ergonomy, health, etc.) when typing for a long time.
the new MBPro is instead sitting on an aluminium stand, no need for ext fans, i got it with the laptop at the online apple store, have a look [here]("http://store.apple.com/us/product/TK789ZM/A?fnode=MTY1NDA2OA&mco=MjQzNDcyMQ"). it is expensive, but very well made. and when you remove the front pillow, it lift up the touchpad no more than 1cm. i can definitely recommend it, Nikos. Lo.

---

### Post by Nikos.Alexandris on 2009-02-08
> **buntuLo said:**
> 
the new MBPro is instead sitting on an aluminium stand, no need for ext fans, i got it with the laptop at the online apple store, have a look [here]("http://store.apple.com/us/product/TK789ZM/A?fnode=MTY1NDA2OA&mco=MjQzNDcyMQ"). it is expensive, but very well made. and when you remove the front pillow, it lift up the touchpad no more than 1cm. i can definitely recommend it, Nikos. Lo.

Well, this is exactly what I was thinking about... But indeed it's expensive. EU80.- in Germany!

Nikos

---

### Post by kenn413 on 2009-02-24
Anyone knows if Apple is working on the Heat Problem and Battery life on the MacBook 5.1 running linux and windows? The high temperatures (as compared to running Mac OS) cannot possibly be healthy for the hardware. For those of us with MacBook 5.1's who are forced to run several operating systems the heat problem/battery life is fatal and disqualifies the MacBook 5.1 as a multi-OS platform. Come on Apple. It would be nice to see you fix.

---

### Post by cyberdork33 on 2009-02-24
> **kenn413 said:**
> Anyone knows if Apple is working on the Heat Problem and Battery life on the MacBook 5.1 running linux and windows? The high temperatures (as compared to running Mac OS) cannot possibly be healthy for the hardware. For those of us with MacBook 5.1's who are forced to run several operating systems the heat problem/battery life is fatal and disqualifies the MacBook 5.1 as a multi-OS platform. Come on Apple. It would be nice to see you fix.
Well, asking here isn't going to help.

---

### Post by kenn413 on 2009-02-25
> **cyberdork33 said:**
> Well, asking here isn't going to help.

The hope was that someone with knowledge about the inner workings of the MacBook 5.1 would start cranking on the problem. Or perhaps if someone had contacts. I must say that this heat problem (as I've seen it) is some of the worst I've ever experienced. You can go to the local supermarked and by a 300$ computer that handles multiple OSs better. I don't buy the stuff about Apple wanting to force people to buy Mac OS X. Apple has a genuine interest in getting the MacBook to run multiple OSs IMO. As one can see from some posts in this thread it is a turn-off for potential Mac buyers that it heats up. Having said all this, the magnitude of the temperature differences puzzles me.

---

### Post by cyberdork33 on 2009-02-25
> **kenn413 said:**
> The hope was that someone with knowledge about the inner workings of the MacBook 5.1 would start cranking on the problem. Or perhaps if someone had contacts. I must say that this heat problem (as I've seen it) is some of the worst I've ever experienced. You can go to the local supermarked and by a 300$ computer that handles multiple OSs better. I don't buy the stuff about Apple wanting to force people to buy Mac OS X. Apple has a genuine interest in getting the MacBook to run multiple OSs IMO. As one can see from some posts in this thread it is a turn-off for potential Mac buyers that it heats up. Having said all this, the magnitude of the temperature differences puzzles me.and since the problem affects windows as well, which is actually supported by Apple, then a good place to complain about the problem is to Apple...

---

### Post by kenn413 on 2009-02-26
Anyone with actual sensor temperature read outs under Windows and/or Linux? Like to see some hard evidence showing the true temperature differences. CLearly the high alu heat conductivity may be misleading.

---

### Post by philcolbourn on 2009-03-16
Power management details can be found here:
[http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/]("http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/")

Add the options to /etc/X11/xorg.conf and reboot. Check settings with nvidia-settings.

> **della said:**
> I managed to get the temperature of the GPU perceptibly lower (down to 63-64°C doing non-intensive stuff) by forcing its clock at the lowest speed. Looks like the nVidia driver is too aggressive when scaling up the clock frequency, at least under normal Compiz operation.

To force the graphic device at the lowest speed when on battery, you can add the line

```
Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3"
```

in the "Device" section of /etc/X11/xorg.conf . To force lowest speed always, use instead

```
Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x3"
```

Of course, this comes at the expense of lower graphic performance.

---

### Post by Andy on 2009-03-16
This issue is killing me,

I had to reinstall osx and buy vmware fusion just so I could run my free operating system with longer battery.

also, anyone else have insanely slow compiz under ubuntu ? even with the nvidia drivers installed?

---

### Post by philcolbourn on 2009-03-17
> **Andy said:**
> This issue is killing me,

I had to reinstall osx and buy vmware fusion just so I could run my free operating system with longer battery.

also, anyone else have insanely slow compiz under ubuntu ? even with the nvidia drivers installed?

This is what I have done:

1. Turned off compiz
2. I went through laptop-mode and enabled many controls
3. In laptop-mode i set the cpu to minimum on battery
4. Removed some applets that monitor cpu etc. I still have the sensor applet running to see if the macbook gets cooler.
5. set Nvidia driver to lowest speed setting.

I have been using the laptop for 70 minutes so far. The Battery is at 73% and it thinks I have another 2 hours 10 minutes to go. I notice that it always says 2 hours and something where as powertop gives higher figures. So if this is linear (and accurate) then could I run for 4.3 hours - that would be close to OS-X. 

The battery applet reports that I am consuming between 13 and 15W.

Also, on my MacBook Pro4,1 temp4 tracks the GPUCoreTemp and temp2 seems to be the CPU.

My GPU runs at say 50oC and the CPU at 40oC when doing not much (browsing, rhythmbox) and fans set to about 3300 RPM.

I hope that helps

---

### Post by davibe on 2009-03-19
well, if you're using 13-15 W there's still something wrong.
Osx idles at 8 - 9 W.

---

### Post by philcolbourn on 2009-03-19
> **davibe said:**
> well, if you're using 13-15 W there's still something wrong.
Osx idles at 8 - 9 W.

What Model is yours?

How do you measure it in OS-X?

---

### Post by philcolbourn on 2009-03-20
> **davibe said:**
> well, if you're using 13-15 W there's still something wrong.
Osx idles at 8 - 9 W.

On my macBookPro4,1 OS-X runs at 12-13W (using system profiler Power = Voltage/1000 * I/1000) on battery with screen on lowest setting and only firefox running.

I think 13-15 is not too far off the mark.

The Battery meter says I have between 4.5 hours to go (depending on what I was doing in the last few seconds)

---

### Post by CraigWatson on 2009-03-22
> **Andy said:**
> I had to reinstall osx and **buy vmware fusion**...

Slightly O/T, but why buy VMware Fusion when you can download [VirtualBox](http://www.virtualbox.org) for free? In many ways it's better than VMware, a lot more user-friendly. I run VBox on my MacBook and it runs perfectly.

On the subject of Ubuntu on the October '08 MBs, I've installed both Ubuntu 8.10 and Fedora 10 on mine and both have the same heat/battery life problem, so it's not localised to Ubuntu.

---

### Post by cyberdork33 on 2009-03-22
> **craigwatson said:**
> slightly o/t, but why buy vmware fusion when you can download [virtualbox]("http://www.virtualbox.org") for free? In many ways it's better than vmware, a lot more user-friendly. I run vbox on my macbook and it runs perfectly.+1

---

### Post by Nikos.Alexandris on 2009-03-24
Not sure about posting this here or in another thread... Anyhow, battery life using the 9600M graphic card isn't much better under OSX. So, we worry too much I think.

The following is copy-pasted from [1]

> In a simple "battery drain" test while paying a "ripped" DVD from the hard drive, the reliable MacWorld reported:

    Using the 9600M GT graphics card, the 2.53 GHz MacBook Pro lasted 2 hours, 12 minutes, while the 2.4 GHz MacBook Pro lasted 2 hours, 18 minutes. You’ll barely be able to watch an entire movie in that amount of time. . . 

    Unfortunately, when using the 9400M, the battery life for either MacBook Pro model did not improve significantly. The 2.53 GHz MacBook Pro gained 17 minutes, while the 2.4 GHz MacBook Pro lasted 13 minutes longer. Interestingly, the 9400M times between the MacBook Pro models and the MacBooks are similar.

    Comparing the MacBook Pro’s 9400M battery life with the previous MacBook Pro ["Core 2 Duo" 2.4 15" (Early 2008/Penryn], and the older MacBook Pro comes out ahead by 15 percent -- the older MacBook Pro's battery lasted close to 3 hours.

If someone can (h)ac(k)tivate the 9400M chip, we would be happy Ubuntu users :-D

I read a thread the other day about some serious attempt to activate the 9400M chip but I can't find it anymore.

Cheers, Nikos
---

[1] [http://www.everymac.com/systems/apple/macbook_pro/macbook-pro-unibody-faq/macbook-pro-unibody-battery-life-graphics-difference.html]("http://www.everymac.com/systems/apple/macbook_pro/macbook-pro-unibody-faq/macbook-pro-unibody-battery-life-graphics-difference.html")

---

### Post by davibe on 2009-03-26
> **philcolbourn said:**
> On my macBookPro4,1 OS-X runs at 12-13W (using system profiler Power = Voltage/1000 * I/1000) on battery with screen on lowest setting and only firefox running.

I think 13-15 is not too far off the mark.

The Battery meter says I have between 4.5 hours to go (depending on what I was doing in the last few seconds)

I have macbook 5,1. new machines have smaller battery 'cause they can idle at lower power rate (8/9 W using osx)

---

### Post by Andy on 2009-03-26
anyone else have compiz roast your 5,1 ?

I cant seem to get it running smoothly

---

### Post by brujoand on 2009-04-19
Any luck on getting the 9400 card working under Ubuntu?
I guess I'll have to try to boot "native-efi" using grub2 to get it up and running.. which.. ruins 3d acceleration :/

---

### Post by Engine_number_9 on 2009-05-14
Hi,

I'm considering installing Ubuntu 9.04 on my MacBook 5,1. I've read about the problem with MacBooks getting to hot in this thread and in Launchpad. In Launchpad the status of the thread has been changed to fixed as 2009-04-21.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550)

So my question is does the MacBook 5,1 still get too hot?

---

### Post by cyberdork33 on 2009-05-14
> **Engine_number_9 said:**
> Hi,

I'm considering installing Ubuntu 9.04 on my MacBook 5,1. I've read about the problem with MacBooks getting to hot in this thread and in Launchpad. In Launchpad the status of the thread has been changed to fixed as 2009-04-21.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550)

So my question is does the MacBook 5,1 still get too hot?
if you want more control of the fans, you can checkout this script:
[http://ubuntuforums.org/showthread.php?t=1102465](http://ubuntuforums.org/showthread.php?t=1102465)

---

### Post by Andy on 2009-05-15
my mac isnt hot running ubuntu native anymore.   but if i dare run compiz it will periodically kernel panic (or put X into a state where i cant kill X or change gettys

---

### Post by gotgenes on 2009-05-15
> **Andy said:**
> anyone else have compiz roast your 5,1 ?

I cant seem to get it running smoothly
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/332549](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/332549)

It's a bug in the NVIDIA driver that shipped with Jaunty. You might be able to update to the latest and get rid of it. I haven't tried it yet, myself.

---

### Post by Engine_number_9 on 2009-05-17
> **gotgenes said:**
> [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/332549](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/332549)

It's a bug in the NVIDIA driver that shipped with Jaunty. You might be able to update to the latest and get rid of it. I haven't tried it yet, myself.

If you upgrade to the new driver I'd be very happy to hear about your experiences with it.

I guess the NVIDIA driver will be fixed in time for 9.10, so I might just wait until it arrives.

---

### Post by Aybara on 2009-06-17
Anyone with a fully updated system with the latest nvidia drivers that can tell me if the MBP runs nice and cool now?

---

### Post by Aybara on 2009-06-24
* bump *

Also, how do I check the temperature readings from the sensors?

EDIT: what I wonder is where you get your "sensors"-call from.

---

### Post by Aybara on 2009-06-24
lm-sensors it was. I am now running the 185.something drivers from nvidia on a fully updated system, and in idle with Compiz running I get the following readings:

anders@anr-ubuntu:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +49.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +49.0°C  (high = +100.0°C, crit = +100.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
Left side  :3453 RPM  (min = 2000 RPM)
Right side :3447 RPM  (min = 2000 RPM)
temp1:       +38.0°C                                    
temp2:       +38.0°C                                    
temp3:       +37.5°C                                    
temp4:       +38.2°C                                    
temp5:       +62.0°C                                    
temp6:       +58.0°C                                    
temp7:       +57.0°C                                    
temp8:       +62.5°C                                    
temp9:       +60.2°C                                    
temp10:      +51.5°C                                    
temp11:      +59.8°C                                    
temp12:      +60.8°C                                    
temp13:      +59.2°C                                    
temp14:      +60.5°C                                    
temp15:      +58.2°C                                    
temp16:      +51.8°C                                    
temp17:      +55.8°C                                    
temp18:      +58.0°C                                    
temp19:      +36.5°C                                    
temp20:      +48.0°C 

This does not look to bad, does it? I think it is 8-10 degrees cooler than before.

---

### Post by buntuLo on 2009-06-24
i understand you have a Macbook Pro 5,1. i run Intrepid on it, with nvidia 180.11. these are my idle values, even though heat dissipation strongly depends on the room temperature:

lo@malamela:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +100.0°C, crit = +100.0°C)
coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (high = +100.0°C, crit = +100.0°C)
applesmc-isa-0300
Adapter: ISA adapter
Left side  :2803 RPM  (min = 2800 RPM)
Right side :2802 RPM  (min = 2800 RPM)
temp1:       +32.2°C
temp2:       +32.2°C
temp3:       +31.5°C
temp4:       +32.8°C
temp5:       +58.8°C
temp6:       +52.5°C
temp7:       +52.5°C
temp8:       +61.0°C
temp9:       +52.8°C
temp10:      +45.8°C
temp11:      +52.5°C
temp12:      +54.2°C
temp13:      +55.8°C
temp14:      +58.2°C
temp15:      +54.8°C
temp16:      +65.0°C
temp17:      +51.5°C
temp18:      +51.8°C
temp19:      +31.8°C
temp20:      +42.2°C

---

### Post by Aybara on 2009-07-10
I see that [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty) is upgraded with a fix to make use of Nvidia 9400, and I quote:

"Batterylife seems to improve from 1:40 to 3:20 and the laptop is 10° cooler."

Anyone tried this?

In the bottom it says "Drawbacks: cpufreq renders system instable.". Can someone spell out for me what that means?

---

### Post by niyam on 2009-07-11
i try to set the mac fan speed to 3500 for fan1 and fan2 to get its temperature down. here's another tip: i use a laptop stand with built-in fans to further cool the macbook pro externally. it powers through the usb port of the macbookpro.

regards
niyam

---

### Post by Aybara on 2009-07-16
*bump*

Has anyone tried the stuff mentioned in the setup guide to make the laptop cooler?

---

### Post by alexmurray on 2009-07-16
> **Aybara said:**
> *bump*

Has anyone tried the stuff mentioned in the setup guide to make the laptop cooler?

Well considering I recently added the stuff about using grub2 to do efi boot and hence use the 9400M to make my MBP5,1 cooler, I would say that 'yes, I have tried it' and it worked - the fact that it is written there means someone has tried it and it worked for them, so it may also work for you too.

---

### Post by Aybara on 2009-07-16
Ah. I hadn't checked back for that.

I followed the guide until that last point on EFI, and had to pause a bit there, since I have no idea what it is I will be modifying :). 

I have already installed refit, and I'll try the rest of the guide this afternoon. This has no impact on my OS X install at all, right?

Is it a problem that cpufreq renders the system instable? Is that one used on an out-of-the-box Ubuntu install?

Thanks for the great guide, by the way.

---

### Post by Aybara on 2009-07-16
Is the solution with grub2 better than the one with elilo, since it doesn't say anything about cpufreq causing an unstable system, or doesn't it matter which one I go for?

---

### Post by alexmurray on 2009-07-16
I never tried elilo so I can't compare - you're best off following the efi thread for more info - see my posts [#863]("http://ubuntuforums.org/showpost.php?p=7618851&postcount=863") and [#866]("http://ubuntuforums.org/showpost.php?p=7624817&postcount=866") for more info and some of the issues I've come across

---

### Post by Nikos.Alexandris on 2009-08-01
> **alexmurray said:**
> I never tried elilo so I can't compare - you're best off following the efi thread for more info - see my posts [#863]("http://ubuntuforums.org/showpost.php?p=7618851&postcount=863") and [#866]("http://ubuntuforums.org/showpost.php?p=7624817&postcount=866") for more info and some of the issues I've come across

[s]alexmurray,

with what kernel do you run your box, (wrt to elilo)?[/s] Sorry, wrong question. Another question then: how long did your box run when boot with grub-efi?

---

### Post by alexmurray on 2009-08-03
not much longer with grub-efi than with grub-pc (legacy boot). I'd get at most about 1 hr 45 minutes with legacy boot and maybe 2 hours 15 minutes with efi boot - unfortunately there's no way to adjust the LCD brightness with efi boot so if that were possible it would probably help to get a bit longer...

---

### Post by ryanczak on 2009-08-04
Here's a python daemon I wrote to monitor the temperature of my unibody macbook and set the fan speed accordingly. While this is targetted at the macbook it would be easy to modify it for the macbook pro. This script requires that you have the applesmc kernel model loaded. I'm currently using this script with Karmic Alpha 3 but it should work with any Linux disro that has python and the applesmc module. 

The following should be copied to '/usr/local/sbin/mb-fancontrol'

```

#!/usr/bin/python
# This program is public domain - Use at your own risk :)
# Copyright 2009 by Matt Ryanczak
#
# I wrote this script for my macbook because I could not find anything else that worked very well.
# The algorithm used to control the fan speed was inspired by a shell script written by Nick Barcet
# His script (for the macbook pro) can be found here: https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl

import sys, os
import time
import os
import syslog

# Tweak these numbers to adjust the sensitivity of the fans
MaxTemp = 59
MinTemp = 47

# These number are tweakable as well but note that 6500 is the highest setting for the fan.
MaxFanSpeed = 6500
# I add 100 to this value before setting the fan speed in the code below. This works better IMHO
MinFanSpeed = 1500

# Set to 1 for logging to syslog. Set to 0 for none (fatal errors still get logged)
# At least on my system (Karmic Alpha 3) you must enable UDP logging in /etc/rsyslog.conf
# to see log messages from this program. Other distro's python may log to /dev/log.
# A better way to see what is going on with your tempurature and fans is to install lm-sensors
# then you can run 'watch sensors' to see temps and fan speed
DebugLogging = 0

# Daemon spawning function from python cookbook
def daemonize (stdin='/dev/null', stdout='/dev/null', stderr='/dev/null'):
    # Perform first fork.
    try:
        pid = os.fork( )
        if pid > 0:
            sys.exit(0) # Exit first parent.
    except OSError, e:
        sys.stderr.write("fork #1 failed: (%d) %sn" % (e.errno, e.strerror))
        sys.exit(1)
    # Decouple from parent environment.
    os.chdir("/")
    os.umask(0)
    os.setsid( )
    # Perform second fork.
    try:
        pid = os.fork( )
        if pid > 0:
            sys.exit(0) # Exit second parent.
    except OSError, e:
        sys.stderr.write("fork #2 failed: (%d) %sn" % (e.errno, e.strerror))
        sys.exit(1)
    # The process is now daemonized, redirect standard file descriptors.
    for f in sys.stdout, sys.stderr: f.flush( )
    si = file(stdin, 'r')
    so = file(stdout, 'a+')
    se = file(stderr, 'a+', 0)
    os.dup2(si.fileno( ), sys.stdin.fileno( ))
    os.dup2(so.fileno( ), sys.stdout.fileno( ))
    os.dup2(se.fileno( ), sys.stderr.fileno( ))

# Check to make sure the applesmc module is loaded 
if (os.path.exists("/sys/devices/platform/applesmc.768") == 0):
   sys.stderr.write("Fatal Error: /sys/devices/platform/applesmc.768 does not exist!\nIs the applesmc module loaded?\n")
   sys.exit()

syslog.openlog("mb-fancontrol")

# Function to set the fan speed
def SetFanSpeed (FanSpeed, MinFanSpeed):
    try:
        if (FanSpeed < MinFanSpeed):
           FanSpeed = MinFanSpeed
        FanSpeedSysFn = '/sys/devices/platform/applesmc.768/fan1_min'
        FanSpeedSys = open(FanSpeedSysFn, 'w+')
        if (DebugLogging == 1):
            syslog.syslog(syslog.LOG_NOTICE,'Setting fan speed to: %s' % (FanSpeed))
        FanSpeedSys.write(FanSpeed) 
        FanSpeedSys.close()
    except IOError:
        syslog.syslog(syslog.LOG_ERR,'Fatal Error: Cannot open: /sys/devices/platform/applesmc.768/fan1_min. Is the applesmc module loaded?')
    return 1

# Set the initial fan speed to MinFanSpeed
SetFanSpeed(str(MinFanSpeed), str(MinFanSpeed))

# Fork the daemon process
daemonize()

Temp5InputFn = '/sys/devices/platform/applesmc.768/temp5_input'
Temp8InputFn = '/sys/devices/platform/applesmc.768/temp8_input'
Temp10InputFn = '/sys/devices/platform/applesmc.768/temp10_input'
Temp11InputFn = '/sys/devices/platform/applesmc.768/temp11_input'

syslog.syslog(syslog.LOG_NOTICE,'Starting')

while True:
    try:
        Temp5Input = open(Temp5InputFn)
        Temp5 = int(Temp5Input.read())
        Temp5Input.close()
        Temp8Input = open(Temp8InputFn)
        Temp8 = int(Temp8Input.read())
        Temp8Input.close() 
        Temp10Input = open(Temp10InputFn)
        Temp10 = int(Temp10Input.read())
        Temp10Input.close()
        Temp11Input = open(Temp11InputFn)
        Temp11 = int(Temp11Input.read())
        Temp11Input.close()
    except IOError:
        syslog.syslog(syslog.LOG_ERR,'Error opening temperature sensors. Is the applesmc module loaded?')
        continue
    AverageTemp = ((Temp5 + Temp8 + Temp10 + Temp11)/4)
    if (DebugLogging == 1):
        syslog.syslog(syslog.LOG_NOTICE,'Average Temperature: %s' % (float(AverageTemp)/1000))
    if (AverageTemp > (MaxTemp * 1000)):
        SetFanSpeed(str(MaxFanSpeed), str(MinFanSpeed))
        syslog.syslog(syslog.LOG_NOTICE,'Getting too hot! Setting fan speed to: %s' % (MaxFanSpeed))
    else:
        FanSpeed = (((AverageTemp - (MinTemp * 1000)) * (6000 / (MaxTemp - MinTemp)) / 1000))
        SetFanSpeed(str(FanSpeed), str(MinFanSpeed))
    time.sleep(5)

```Here's an init script. This should be copied to '/etc/init.d/fancontrol' and then your should run:
'update-rc.d mb-fancontrol defaults'

```

#! /bin/bash
### BEGIN INIT INFO
# Provides:          mb-fancontrol
# Required-Start:    $local_fs
# Required-Stop:     $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: mb-fancontrol
# Description:       macbook fan speed regulator
### END INIT INFO

. /lib/lsb/init-functions

[ -f /etc/default/rcS ] && . /etc/default/rcS
PATH=/bin:/usr/bin:/sbin:/usr/sbin
DAEMON=/usr/local/sbin/mb-fancontrol
DESC="fan speed regulator for the macbook"
NAME="mb-fancontrol"

test -x $DAEMON || exit 0

case "$1" in
  start)
    /usr/local/sbin/mb-fancontrol
    ;;
  stop)
    killall mb-fancontrol
    ;;
  restart)
        killall mb-fancontrol; sleep 2; /usr/local/sbin/mb-fancontrol
    ;;
  *)
    log_success_msg "Usage: /etc/init.d/mb-fancontrol {start|stop|restart}"
    exit 1
    ;;
esac

exit 0

```

I'll try to answer any questions and I'd love to see any improvements!

---

### Post by swarup on 2009-08-05
@ryanczak: 
1. Did the above solve your temperature problem? That is, does your computer now run as cool in Linux as it does in OSX? If so, that is incredible news.

2. And if did solve the problem, then what would it take to get this implemented for the MBP?

---

### Post by Nikos.Alexandris on 2009-08-06
> **swarup said:**
> @ryanczak: 
1. Did the above solve your temperature problem? That is, does your computer now run as cool in Linux as it does in OSX? If so, that is incredible news.

2. And if did solve the problem, then what would it take to get this implemented for the MBP?

The script is tested in a MacBook not a MacBook Pro. The difference is that the Pro has the hungry NVIDIA 9600. I don't think that the script will do much in a Pro.

---

### Post by swarup on 2009-08-06
I see, ok, we'll scrap that idea then.
But what about alexmurray's grub2 idea? He I guess is the one who posted the grub2 option on the wiki, and he says it solved the problem for him. Am I to understand by this that he has got the solution, and we should all install grub2?

Nikos, what setup are you using currently? Did you try the grub2 arrangement yet? By the way that alexmurray has written, it sounds like his heat problem is completely solved by this grub2. Although one question: he writes that "there's no way to adjust the LCD brightness with efi boot"-- does that mean that under grub2, the manual screen brightness adjustment (F1/F2 keys) does not work?

---

### Post by Nikos.Alexandris on 2009-08-06
> **swarup said:**
> I see, ok, we'll scrap that idea then.
But what about alexmurray's grub2 idea? He I guess is the one who posted the grub2 option on the wiki, and he says it solved the problem for him. Am I to understand by this that he has got the solution, and we should all install grub2?

Nikos, what setup are you using currently? Did you try the grub2 arrangement yet? By the way that alexmurray has written, it sounds like his heat problem is completely solved by this grub2. Although one question: he writes that "there's no way to adjust the LCD brightness with efi boot"-- does that mean that under grub2, the manual screen brightness adjustment (F1/F2 keys) does not work?

With grub2 (grub2 is just the newer version of grub) you can boot in (a) bios-mode, (b) efi-mode. I use the (standard) bios-mode because I can adjust display/keyboard brightness. With (b) you can use the Nvidia9400 on-board graphics card but (still) can't load the proper modules to play with display/keyboard brightness.

Elilo is (just) another boot-loader like grub2.

Regards

---

### Post by swarup on 2009-08-06
> **Nikos.Alexandris said:**
> With grub2 (grub2 is just the newer version of grub) you can boot in (a) bios-mode, (b) efi-mode. I use the (standard) bios-mode because I can adjust display/keyboard brightness. With (b) you can use the Nvidia9400 on-board graphics card but (still) can't load the proper modules to play with display/keyboard brightness.


1. With (b), is the heat problem solved?

2. With (b), does the display/keyboard default to the brightest setting?

---

### Post by Nikos.Alexandris on 2009-08-06
> **swarup said:**
> 1. With (b), is the heat problem solved?

2. With (b), does the display/keyboard default to the brightest setting?

Booting with grub-efi will give...

heat problem: more or less solved. The temperature is lower because of the use of the Nvidia9400 chip which is on-board (not like the discrete grapchic's chip Nvidia9600, if I am not wrong). It's just a less power-hungry chip (lower performance of course).

display brightness: I think it's lower than the highest possible level.

keyboard backlight: don't remember... :-p Have to (re-)check it.

---

### Post by swarup on 2009-08-06
> **Nikos.Alexandris said:**
> Booting with grub-efi will give...

heat problem: more or less solved. The temperature is lower because of the use of the Nvidia9400 chip which is on-board (not like the discrete graphic's chip Nvidia9600, if I am not wrong). It's just a less power-hungry chip (lower performance of course).

display brightness: I think it's lower than the highest possible level.

keyboard backlight: don't remember... :-p Have to (re-)check it.


I see. So let me see if I understand correctly-- when one does a dual boot install in the default manner using rEFIt and the Jaunty liveCD, then the install uses "grub1". Correct? And then, in accordance with the [wiki]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#EFI"), one can switch that Ubuntu boot process over to EFI/elilo or EFI/grub2, either of which should help effectively with heat control. But since in the EFI/elilo option, the "cpufreq renders system instable", the EFI-grub2 option is preferable. Now, in this EFI-grub2 setup, heat control is achieved by downgrading to the onboard Nvidia9400 chip, rather than the discrete Nvidia9600 graphics chip. But, and I want to confirm here, the cpu usage remains unchanged, right? So the computer will function just as fast as it used to, just there will be a theoretical decrease in graphics functionality (I would never see the difference, since my work is 99.9% text based.)

This is all very important for me, as in the next four days I have to decide whether to keep this computer, or to return it (I can return it to Apple with no restocking fee in the first two weeks.) I will be using the computer pretty much exclusively for Ubuntu, and am choosing between this computer (17" MBP 5,2), and the Dell Precision M6400. This is the top of the line Dell Business laptop, 17" matte RGBLED screen, 128 GB SSD (both same as on my MBP). Financially, the Dell is a better deal-- $400 less, with a faster CPU (Intel Core 2 Duo T9800, 2.93GHz vs MBP 2.8GHz), better graphics card (512MB NVIDIA Quadro FX 2700M vs MBP NVIDIA GeForce 9400M), included esata port, and 3 yr on-site warrantee (vs MBP 1 yr). But I have tried both computers, and (1) I like the keyboard better on the apple, plus (2) the apple doesn't make a sound, while the Dell's fan when it comes on, is somewhat (albeit not very) noisy. Because for me the work environment is more important than the extra power, I felt the apple may better suit my needs. The keyboard is nicer, and it is quieter. 

But this heat management matter is very important for me as well. If there isn't hope of a good, solid solution in the time to come i.e. if we cannot expect that the Ubuntu side will run as cool as the OSX side (which it should if it has the right command over the hardware), then I may have to consider returning the MBP and getting the Dell Precision instead (which is also an excellent computer in its own right).

---

### Post by Nikos.Alexandris on 2009-08-06
> **swarup said:**
> I see. So let me see if I understand correctly-- when one does a dual boot install in the default manner using rEFIt and the Jaunty liveCD, then the install uses "grub1". Correct? And then, in accordance with the [wiki]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#EFI"), one can switch that Ubuntu boot process over to EFI/elilo or EFI/grub2, either of which should help effectively with heat control. But since in the EFI/elilo option, the "cpufreq renders system instable", the EFI-grub2 option is preferable. Now, in this EFI-grub2 setup, heat control is achieved by downgrading to the onboard Nvidia9400 chip, rather than the discrete Nvidia9600 graphics chip. But, and I want to confirm here, the cpu usage remains unchanged, right? So the computer will function just as fast as it used to, just there will be a theoretical decrease in graphics functionality (I would never see the difference, since my work is 99.9% text based.)

This is all very important for me, as in the next four days I have to decide whether to keep this computer, or to return it (I can return it to Apple with no restocking fee in the first two weeks.) I will be using the computer pretty much exclusively for Ubuntu, and am choosing between this computer (17" MBP 5,2), and the Dell Precision M6400. This is the top of the line Dell Business laptop, 17" matte RGBLED screen, 128 GB SSD (both same as on my MBP). Financially, the Dell is a better deal-- $400 less, with a faster CPU (Intel Core 2 Duo T9800, 2.93GHz vs MBP 2.8GHz), better graphics card (512MB NVIDIA Quadro FX 2700M vs MBP NVIDIA GeForce 9400M), included esata port, and 3 yr on-site warrantee (vs MBP 1 yr). But I have tried both computers, and (1) I like the keyboard better on the apple, plus (2) the apple doesn't make a sound, while the Dell's fan when it comes on, is somewhat (albeit not very) noisy. Because for me the work environment is more important than the extra power, I felt the apple may better suit my needs. The keyboard is nicer, and it is quieter. 

But this heat management matter is very important for me as well. If there isn't hope of a good, solid solution in the time to come i.e. if we cannot expect that the Ubuntu side will run as cool as the OSX side (which it should if it has the right command over the hardware), then I may have to consider returning the MBP and getting the Dell Precision instead (which is also an excellent computer in its own right).

swarup,

sorry but I don't have the time to read all the details of your long post.

About grub, grub2 and efi please have a look in the web (...in general grub will be replaced by grub2, e.g. Karmic Koala will use grub2 by default). There is plenty of info to make it all easy to understand.

About the machine I can tell you from my experience that there were some problems working with Ubuntu but I consider them as minor. Heat and battery life is almost the same under Mac OS-X if you use the Nvidia9600 card.

I kept the machine (I bought it in November2008 and had the same questions as you) and I am happy. Don't worry. There is not a single report that a Mac was burned using Ubuntu ;-)

Things are improving more and more. I think that it can be summarized like that: it's just a matter of time, of good skilled developer's who like Ubuntu and believe in FOSS as a software development model and of users who test to support bug-fixing.

Greets, Nikos
 
P.S. You will appreciate that the Mac's are quite, comfortable to work with under most light conditions. That's, IMHO, an issue highly related with Health.

---

### Post by ryanczak on 2009-08-06
> **swarup said:**
> @ryanczak: 
1. Did the above solve your temperature problem? That is, does your computer now run as cool in Linux as it does in OSX? If so, that is incredible news.

2. And if did solve the problem, then what would it take to get this implemented for the MBP?

To answer the first question. Yes. This solved my heat problem. My macbook actually runs cooler in Linux than it does in OSX (by about 2 degrees C). It never gets as hot under load in Linux as it does in OSX. 

It would not be hard to implement in a pro. The MBP has two fans which need to be controlled and the sensors to be monitored in order to find a good mean to use for adjusting fan speed would have to be changed. None of this is difficult but I do not have ready access to a MBP to test on. Perhaps someone else can tweak this script, the changes would not be that difficult.

---

### Post by ryanczak on 2009-08-06
> **Nikos.Alexandris said:**
> The script is tested in a MacBook not a MacBook Pro. The difference is that the Pro has the hungry NVIDIA 9600. I don't think that the script will do much in a Pro.

I suspect very strongly that this script could be adapted to work with a mbp. Even with it's hotter 9600 chip the fans can be made to blow enough air through the chasis to keep it cool. If the mbp has fans similar to the mbp they spin up to 6500 rpm which is capable of pushing a lot of air over the hots bits. Good fan control coupled with enabling power management on the 9600 (i.e. lowering chip mhz) would do a long way toward keeping the mbp from running to hot. 

None of this is going to help your battery performance very much though.

---

### Post by Nikos.Alexandris on 2009-08-06
> **ryanczak said:**
> ...
None of this is going to help your battery performance very much though.


Exactly that is the point. The GPU (Nvidia9600 in the MBP5,1) is currently "stable" with temperatures that vary between 70 and (max.) 75 Celsius degrees (at least for me). The critical temperature is 105 Celsius degrees. The same is more or less for the processors... they play between 55 and 6-something. The critical limit is, again, ~100 Cls degrees.

**NOTE: the above temperature values are when the machine is active ( _not_ very heavy image processing _but_ downloading per script from an ftp continuously, surfing, e-mailing, running other applications, etc.).**

The question is: *is it really worthy to make the machine sound like an airplane while there is no battery saving?* Check also the thread [http://ubuntuforums.org/showthread.php?t=1215928](http://ubuntuforums.org/showthread.php?t=1215928) ( i.e. my posts # 7 and # 10 and # 12 ).

What we need is to be able to work with the 9400 when we don't need power for graphics processing and, thus, battery life. That's all. Please correct me if I am wrong, but (as I wrote in a previous post) the temperatures are almost the same when working under OS-X with the driscrete GPU (Nvidia9600).

Kindest regards

---

### Post by ryanczak on 2009-08-06
[quote=Nikos.Alexandris;7743968] The same is more or less for the processors... they play between 55 and 6-something. The critical limit is, again, ~100 Cls degrees.

In my shop we have seen quite a lot of failures on macs that sustain CPU temps of 75+ C. We're a software engineering shop so lengthy compiles are quite common. I prefer to keep my cpu in the 60s. The script I wrote accomplishes this nicely without sounding like an airplane. 

I would prefer to see the built in fancontrol work as it should. I would also like to see the power management issues addressed. But this is far more than just the ability to use embedded vs. discrete graphics. There are many issues with drivers generating spurious interuptsl. The keyboard/touchpad is horrible in this regard. There is a lot of room for improvement in several areas imho. 

With all that said I am quite happy with the Linux on this mb. I get 3.5 hours on battery which is quite acceptable.

---

### Post by Nikos.Alexandris on 2009-08-06
> **ryanczak said:**
> In my shop we have seen quite a lot of failures on macs that sustain CPU temps of 75+ C. We're a software engineering shop so lengthy compiles are quite common. I prefer to keep my cpu in the 60s. The script I wrote accomplishes this nicely without sounding like an airplane. 

I would prefer to see the built in fancontrol work as it should. I would also like to see the power management issues addressed. But this is far more than just the ability to use embedded vs. discrete graphics. There are many issues with drivers generating spurious interuptsl. The keyboard/touchpad is horrible in this regard. There is a lot of room for improvement in several areas imho. 

With all that said I am quite happy with the Linux on this mb. I get 3.5 hours on battery which is quite acceptable.

Thanks for your reply ryanczak. Note, however, that my 75 degrees refer to the GPU not the CPU. The CPU's are always lower :-)

Cheers

---

### Post by swarup on 2009-08-12
Do people think this issue of excessive heat is really just a matter of getting the fans to be controlled properly? Or could it be something other than or in addition to that, which is causing excessive heat? That is, there are two possible components involved in excessive heat: heat-production, and heat-removal. The fans would be the heat-removal side of the equation, but I wonder about the heat-production side. Could something be causing excessive heat production in the MBP while using Ubuntu? I ask, because I notice that while running OSX the MBP is just as quiet as when running Ubuntu. That is, there isn't any more fan activity in OSX than in Ubuntu. At least, none that is audible or palpable.

---

### Post by alexmurray on 2009-08-13
> **swarup said:**
> Do people think this issue of excessive heat is really just a matter of getting the fans to be controlled properly? Or could it be something other than or in addition to that, which is causing excessive heat? That is, there are two possible components involved in excessive heat: heat-production, and heat-removal. The fans would be the heat-removal side of the equation, but I wonder about the heat-production side. Could something be causing excessive heat production in the MBP while using Ubuntu? I ask, because I notice that while running OSX the MBP is just as quiet as when running Ubuntu. That is, there isn't any more fan activity in OSX than in Ubuntu. At least, none that is audible or palpable.

Yep. it has clearly been identified that the 9600M GT GPU causes the extra heat - if you boot via EFI and use the 9400M instead, the MBP is just as cool under Linux as it is under OSX.

---

### Post by Nikos.Alexandris on 2009-08-13
> **swarup said:**
> Do people think this issue of excessive heat is really just a matter of getting the fans to be controlled properly? Or could it be something other than or in addition to that, which is causing excessive heat? That is, there are two possible components involved in excessive heat: heat-production, and heat-removal. The fans would be the heat-removal side of the equation, but I wonder about the heat-production side. Could something be causing excessive heat production in the MBP while using Ubuntu? I ask, because I notice that while running OSX the MBP is just as quiet as when running Ubuntu. That is, there isn't any more fan activity in OSX than in Ubuntu. At least, none that is audible or palpable.

Hi swarup. 

I think that using the on-board Nvidia 9400 card, turning off all unnecessary devices when not used (wireless, bluetooth, which IMHO, are currently not that easy to turn off), maybe deactivate superficial deamons that run in the backgrounf will give a quiet, cool and longer lasting (battery) system.

That should be all.

There is always the possibility to make a test (at least for battery life): turn on the Nvidia 9600 under OS-X and work as you usually do under linux and check how long the battery will live, the fan speed behavior and noise.

Cheers

---

### Post by swarup on 2009-08-13
> **Nikos.Alexandris said:**
> Hi swarup. 

I think that using the on-board Nvidia 9400 card, turning off all unnecessary devices when not used (wireless, bluetooth...) 

Does OSX do these things (use on-board video, turn off devices) in order to keep itself cool? My thought would be that we should emulate OSX's way of keeping the computer cool, whatever that may be. OSX keeps itself quit cool, whereas Ubuntu heats up even under unstressful activities. I wonder if we could find out somehow the way OSX manages, so that the same arrangements can be made for Ubuntu.

I suppose the factors which cause the keyboard and palm-rest places to heat up are the same factors which cause shortened battery life? Although many others are primarily concerned with battery life, my main concern is the heat production as I use this computer as a desktop replacement.

Is [this the bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550") that is relevant to the heat issue for MBP 5,1 and 5,2, or is there one more directly related with these models?

---

### Post by freinn on 2009-10-10
Hi! in first place, sorry for my english, is not very well.

I`m using linux mint 7 (is like ubuntu 9.04, but a little modified) and I can`t control the temperature of my macbook 5,1!!

I`ve followed these steps:

1) I`ve installed the packages from mactel-support from the repository (all of them less the ones which starts with mbp)

2) I used that script from ryanczak, but I don`t know if I put it all right :S:S can you explain me better??

I dont know how to activate the neccesary modules, I do lsmod and the applesmc module is loaded, and in the system monitor python (2 times) is running!!

But, the macbook gets VERY hot (I cant touch the part next to the screen because it warms me. This happen running/not running compiz fusion, in all chases!!!

Please help me and explain me all the steps I have to follow because I need my laptop running linux for the university.

I would know too if the trackpad can be desactivated because when Im tippyng I touch it without wanting it.

Thanks!!!

---

### Post by CraigWatson on 2009-10-26
Does anyone have any update to this problem for 9.10 (Karmic)?

I'll be installing Karmic on my MB5.1 (October 2008 ) this coming weekend (sooner if I'm bored enough) so I'll have feedback on the heat problem, but just wondering if anyone has tried it yet?

---

### Post by khelidan on 2009-10-31
> **CraigWatson said:**
> Does anyone have any update to this problem for 9.10 (Karmic)?

I'll be installing Karmic on my MB5.1 (October 2008 ) this coming weekend (sooner if I'm bored enough) so I'll have feedback on the heat problem, but just wondering if anyone has tried it yet?

waiting for your feedback! :D

---

### Post by Nikos.Alexandris on 2009-10-31
> **khelidan said:**
> waiting for your feedback! :D

Here is mine using Karmic on MBP5,1: it's great :-) == is & feels cooler!

Regards

---

### Post by Silmathoron on 2009-10-31
Same here : much better on mbp 5,3 ! (& with the new 190,42 drivers)

---

### Post by buntuLo on 2009-11-01
indeed, same temperatures i was used to under intrepid, with fans now spinning only at 2000 rpm instead of 2800. still nvidia 185 here.
Nikos, are you using the 9400m chip via efi booting on karmic?

---

### Post by Nikos.Alexandris on 2009-11-01
> **buntuLo said:**
> indeed, same temperatures i was used to under intrepid, with fans now spinning only at 2000 rpm instead of 2800. still nvidia 185 here.
Nikos, are you using the 9400m chip via efi booting on karmic?

No (not yet!). Soon I will try it out.

(
I want to express (although off-topic) my excitement about Karmic on the mbp5,1. It's perfect :-p
)

---

### Post by rockstar1 on 2009-11-01
I read that in MacBook 5,1 using karmic koala I can't control de brightness, anybody know how can we fix this problem? Or with must wait some weeks?
And Does it work on Karmic Koala or only 9.04?

---

### Post by maximilianyuen on 2009-11-18
hi all, I am completely new to linux and there are so many codes here...

can anyone be kind and point me which post here should I follow to get my MBP 5.1 cool?

many thanks

---

### Post by linuxopjemac on 2009-11-18
[http://www.atpm.com/10.04/ibreeze.shtml](http://www.atpm.com/10.04/ibreeze.shtml) ;)

---

### Post by chokchaioldschool on 2009-11-18
> **Nikos.Alexandris said:**
> Here is mine using Karmic on MBP5,1: it's great :-) == is & feels cooler!

Regards

Yep I agree. Also MBP5.3 is great.

---

### Post by hitman9211 on 2009-11-18
Do you have the applesmc-dkms package installed? Please start from there, and if the problem exists, I will help you solve this.

---

### Post by maximilianyuen on 2009-11-19
> **hitman9211 said:**
> Do you have the applesmc-dkms package installed? Please start from there, and if the problem exists, I will help you solve this.

it said:
Couldn't find package applesmc-dkms

---

### Post by linuxopjemac on 2009-11-19
you probably didn't add the mactel repository to your sources.list...

[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by Gambit- on 2009-12-02
> **linuxopjemac said:**
> you probably didn't add the mactel repository to your sources.list...

[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

Actually, running Karmic on a 5,2 MBP, the applesmc-dkms package hasn't been pushed up yet.  It's available in the older repositories, though.  Any thoughts on whether or not it's worth a try?

I'd like to have better fan control as well.  Right now I'm staring at 20 different temp1 through temp20 sensors with no real idea what any of them refer to.  Plus, it doesn't seem like the fan's are spinning up or spinning down automatically at all - the CPU temperature got up to 80c before I slapped the fans up to high speed manually - that ain't cool at all.  Any suggestions on how to better manage this would be most welcome.

For those following along from home, right now the MBP 5,2+Karmic combination is proving quite capable in all avenues except for the temperature/fan control (which is an important one!).  Wireless, backlight control, keyboard backlight are all working.  I have not yet tested sound or BT, though.

---

### Post by alexmurray on 2009-12-02
The applesmc-dkms package in the mactel repo is older than the code included in the Karmic Linux kernel so there would be no point in building packages for Karmic - the applesmc module in the Karmic kernel is the latest version.

---

### Post by Gambit- on 2009-12-03
> **alexmurray said:**
> The applesmc-dkms package in the mactel repo is older than the code included in the Karmic Linux kernel so there would be no point in building packages for Karmic - the applesmc module in the Karmic kernel is the latest version.

That's good to know, thanks alexmurray!

I've added a bunch of details regarding what a MBP 5,2's temperature sensors track on the wiki at [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic).  Still no solution in place for responding to the temperature change and intelligently controlling the fan.

---

### Post by Sloth on 2009-12-06
> **Gambit- said:**
> That's good to know, thanks alexmurray!

I've added a bunch of details regarding what a MBP 5,2's temperature sensors track on the wiki at [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic).  Still no solution in place for responding to the temperature change and intelligently controlling the fan.

I used the fancontrol daemon posted a few pages ago, and it's controlling my fans beautifully.

I modified it to use both fans (fan #2 only when things get really hot - not sure I'm totally happy with this).

Note that I'm running kernel 2.6.32.

Here's the modified source.  Use at your own risk.  If your computer melts or the fans drill a hole in your MBP and spin around the room demolishing your priceless Monets, well, you are on your own.

```
#!/usr/bin/python
# This program is public domain - Use at your own risk :)
# Copyright 2009 by Matt Ryanczak
#
# I wrote this script for my macbook because I could not find anything else that worked very well.
# The algorithm used to control the fan speed was inspired by a shell script written by Nick Barcet
# His script (for the macbook pro) can be found here: https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl

import sys, os
import time
import os
import syslog

# Tweak these numbers to adjust the sensitivity of the fans
MaxTemp = 72
MinTemp = 46

# These number are tweakable as well but note that 6500 is the highest setting for the fan.
MaxFanSpeed = 6600
# I add 100 to this value before setting the fan speed in the code below. This works better IMHO
MinFanSpeed = 1600

# Set to 1 for logging to syslog. Set to 0 for none (fatal errors still get logged)
# At least on my system (Karmic Alpha 3) you must enable UDP logging in /etc/rsyslog.conf
# to see log messages from this program. Other distro's python may log to /dev/log.
# A better way to see what is going on with your tempurature and fans is to install lm-sensors
# then you can run 'watch sensors' to see temps and fan speed
DebugLogging = 0

# Daemon spawning function from python cookbook
def daemonize (stdin='/dev/null', stdout='/dev/null', stderr='/dev/null'):
    # Perform first fork.
    try:
        pid = os.fork( )
        if pid > 0:
            sys.exit(0) # Exit first parent.
    except OSError, e:
        sys.stderr.write("fork #1 failed: (%d) %sn" % (e.errno, e.strerror))
        sys.exit(1)
    # Decouple from parent environment.
    os.chdir("/")
    os.umask(0)
    os.setsid( )
    # Perform second fork.
    try:
        pid = os.fork( )
        if pid > 0:
            sys.exit(0) # Exit second parent.
    except OSError, e:
        sys.stderr.write("fork #2 failed: (%d) %sn" % (e.errno, e.strerror))
        sys.exit(1)
    # The process is now daemonized, redirect standard file descriptors.
    for f in sys.stdout, sys.stderr: f.flush( )
    si = file(stdin, 'r')
    so = file(stdout, 'a+')
    se = file(stderr, 'a+', 0)
    os.dup2(si.fileno( ), sys.stdin.fileno( ))
    os.dup2(so.fileno( ), sys.stdout.fileno( ))
    os.dup2(se.fileno( ), sys.stderr.fileno( ))

# Check to make sure the applesmc module is loaded 
if (os.path.exists("/sys/devices/platform/applesmc.768") == 0):
   sys.stderr.write("Fatal Error: /sys/devices/platform/applesmc.768 does not exist!\nIs the applesmc module loaded?\n")
   sys.exit()

syslog.openlog("mb-fancontrol")

# Function to set the fan speed
def setFanSpeed(Fan, FanSpeed, MinFanSpeed):
    try:
        if (FanSpeed < MinFanSpeed):
           FanSpeed = MinFanSpeed
        FanSpeedSysFn = '/sys/devices/platform/applesmc.768/fan%s_min' % Fan
        FanSpeedSys = open(FanSpeedSysFn, 'w+')
        if (DebugLogging == 1):
            syslog.syslog(syslog.LOG_NOTICE,'Setting %d fan speed to: %s' % (Fan, FanSpeed))
        FanSpeedSys.write(FanSpeed) 
        FanSpeedSys.close()
    except IOError:
        syslog.syslog(syslog.LOG_ERR,'Fatal Error: Cannot open: /sys/devices/platform/applesmc.768/fan1_min. Is the applesmc module loaded?')
    return 1

# Function to set the fan speed
def SetFanSpeed (FanSpeed, MinFanSpeed):
    setFanSpeed(1, FanSpeed, MinFanSpeed)
    if int(FanSpeed) < 3600:
        MinFanSpeed = "0"
        FanSpeed = "0"
    setFanSpeed(2, FanSpeed, MinFanSpeed)
    return 1

# Set the initial fan speed to MinFanSpeed
SetFanSpeed(str(MinFanSpeed), str(MinFanSpeed))

# Fork the daemon process
daemonize()

Temp5InputFn = '/sys/devices/platform/applesmc.768/temp5_input'
Temp8InputFn = '/sys/devices/platform/applesmc.768/temp8_input'
Temp14InputFn = '/sys/devices/platform/applesmc.768/temp14_input'

syslog.syslog(syslog.LOG_NOTICE,'Starting')

while True:
    try:
        Temp5Input = open(Temp5InputFn)
        Temp5 = int(Temp5Input.read())
        Temp5Input.close()
        Temp8Input = open(Temp8InputFn)
        Temp8 = int(Temp8Input.read())
        Temp8Input.close() 
        Temp14Input = open(Temp14InputFn)
        Temp14 = int(Temp14Input.read())
        Temp14Input.close()
    except IOError:
        syslog.syslog(syslog.LOG_ERR,'Error opening temperature sensors. Is the applesmc module loaded?')
        continue
    AverageTemp = ((Temp5 + Temp8 + Temp14)/3)
    if (DebugLogging == 1):
        syslog.syslog(syslog.LOG_NOTICE,'Average Temperature: (%s %s %s) %s' % (Temp5, Temp8, Temp14, float(AverageTemp)/1000))
    if (AverageTemp > (MaxTemp * 1000)):
        SetFanSpeed(str(MaxFanSpeed), str(MinFanSpeed))
        syslog.syslog(syslog.LOG_NOTICE,'Getting too hot! Setting fan speed to: %s' % (MaxFanSpeed))
    elif (AverageTemp <= (MinTemp * 1000)):
        SetFanSpeed("0", "0")
    else:
        FanSpeed = (((AverageTemp - (MinTemp * 1000)) * (6000 / (MaxTemp - MinTemp)) / 1000))
        SetFanSpeed(str(FanSpeed), str(MinFanSpeed))
    time.sleep(5)


```

---

### Post by ahorriblemess on 2009-12-20
never mind. feel free to delete this

---

### Post by Chicoboia on 2010-02-05
Hi.

Just installed ubuntu 9.10 on my MB 5,1. It gets hot even when it is doing nothing (just the fact of running linux is enough to observe this behavior). The fan keeps a high rotation. It is unconfortable to type in the keyboard because it is too warm. Is there anything i can do to solve this problem?

Cheers, Chico.

---

### Post by m.prebble on 2010-02-06
Hi guys,
EXCELLENT job on providing Ubuntu to the Mac users - I have always been a PC user, then wanted to broaden my horizons - but some things about MacOS drive me crazy, so very happy to be able to install something I can use properly! Anyway, I digress.
I have a MBP 5.4, and I am a little worried about the apparent lack of fan control on my machine. I am running Ubuntu Karmic, and the fan does not seem to adjust for the load conditions - running CPUburn or compiling a source tree, the core temp rises to 79 deg C before I pull the plug. The fan just sits calmly idling at 2000 rpm throughout this. Maybe the h/ware has some protection once the cpu reaches critical, but why does the apple module let it reach this point?

Of course, I have read the thread on cat'ing a value to

<CODE>echo 3500 | sudo tee /sys/devices/platform/applesmc.768/fan1_min</CODE> and this seems to work, but I feel that something as fundamentally important as fan control should be handled automatically - not by the user. What if a rogue application hangs and uses all the CPU? What if you are watching a movie and are not monitoring the cpu temp? It is nice to be able to control the fan speed manually when needed, but I would much rather let the OS handle this!
I have checked  /sys/devices/platform/applesmc.768/fan1_manual and it is 0. 

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/262550](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/262550)

This guy was a total dick in his attitude, but he does have a point - this is in an important issue. 
Is there anything I can do to enable automatic fan control on my machine? Something obvious which I am overlooking? Until I can be assured myself that the CPU won't cook itself, I can't rely on Ubuntu as a primary OS. 

Many, many thanks for any advice!

---

### Post by danielponte on 2010-03-08
I'm facing the same problem, recently installed Karmic on my 5.5 MBP.. I can monitor the temps, fan speeds, everything, but the damn thing refuses to automatically speed up the fan, I've got temps close to 100c when running prime and it wont go past the fan1_min speed :(

So annoying.. any fixes incoming to this problem? We need automatic fan speed based on temps, not manually... :(

EDIT: Fanspeed stays at whatever value I set fan1_min. Default is 2000. My fan1_manual is set to ZERO.

---

### Post by m.prebble on 2010-04-23
PLEASE can someone give some advice here? This problem still appears to be in the latest Lucid pre-release. I can't rely on that Ubuntu won't cook (or at least shorten the life of) my CPU if I am not monitoring it. There are other people with this issue, hoping someone can help.

---

### Post by kosumi68 on 2010-04-24
> **m.prebble said:**
> PLEASE can someone give some advice here? This problem still appears to be in the latest Lucid pre-release. I can't rely on that Ubuntu won't cook (or at least shorten the life of) my CPU if I am not monitoring it. There are other people with this issue, hoping someone can help.

There is a possibility that something changed in the SMC for the newer macbooks. Please read the top post in this thread
[http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096), and post back here. Maybe we will see something.

Cheers!

---

### Post by xxander on 2010-04-24
This might just be a problem with MacBooks because mine heats up in OS X a lot.  But for me, Ubuntu is working pretty well!

---

### Post by kosumi68 on 2010-04-27
I may have found the root cause of the problem described in the first post in this thread. Comparing raw SMC data from most laptop models since 2008, it seems Apple did indeed change the SMC in conjunction with the release of the MacBook5,1. Presumably the automatic overheat protection of the SMC was removed (or changed to some unknown mechanism).

Thus, at least for the models MB51, MBA21, MBP51, MBP54, an OS-based fan-control scheme MUST be used at this stage, to protect the computer.

Seems people were right all along. Since the machine models are so similar, it is hard to know which models are actually affected. The attached script detects some details of the SMC, and provides (or should provide, please contribute) advice on how to set up your system to best control the heat of your computer.

---

### Post by npfthunfan on 2010-04-27
@kosumi68 Sorry for being a bit thick... but what am I supposed to do with that?


Anyway... returning to this topic about 18 months after the first time I was here... 

From what I can tell we have a two-fold problem

1. The SMC does not increase the fan-speed soon enough (this is the same under OS X).
[INDENT]I use smcFanControl on OS X to set the min fan speed to 4000 most of the time (runs around 40º)... up to it's max (at least of smcFC) of 6000 when I am doing intensive tasks... even at that point the machine runs at about 70ºC

If I don't set the min fan speed it stays at 2000 until the CPU gets to 85ºC then it does enough to hold it[/INDENT]

2. Ubuntu creates more heat than OS X
[INDENT]Add about 20º to each of the values for OS X and you've got what I find on Ubuntu... For some reason the fans don't seem to have as much effect. When doing GPU/CPU intensive tasks the temp shoots above 80 way too quickly

My guess (as many have said before) is the GPU isn't quite managed as well on Ubuntu. (Just checked, I am using the 9400 on OS X rather than the 9600 which gets used by Ubuntu - I will take a look at what it looks like with the other card running) My assumption is that the hardware is just so well integrated in OS X that its so hard to get it right on Ubuntu

EDIT: Use of the 9600 on OSX makes a small difference but it's no way near as hot as Ubuntu[/INDENT]

---

### Post by npfthunfan on 2010-04-28
It appears that switching to the Higher Performance under OS X decreased the temperature under Ubuntu... that and turning off the visual effects in GNOME

Now, when I get the same sort of temps as OS X... I run the fans at 6000rpm all the time, GPU is at 50 and CPUs at 38 now (FF & Evolution open), then when Gaming GPU hits 85 and CPUs 75... which is similar to under OS X

Thoughts?

---

### Post by Aybara on 2010-04-28
I have a 5.1 from late 2008, and I believe it idles at about 60-65 degrees Celsius in Ubuntu. Is the fan-control script from [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid) the recommended fix/workaround?

---

### Post by npfthunfan on 2010-04-28
That seems to be the problem everyone has... 

I do the min fan speed hack... 
```
echo 6000 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
```
(Fan 2 appears to follow suit when increasing fan1's min)

I seemed to get a decrease in GPU temp by setting the Graphics to Higher Performance in OSX

---

### Post by kosumi68 on 2010-04-29
> **danielponte said:**
> I'm facing the same problem, recently installed Karmic on my 5.5 MBP.. I can monitor the temps, fan speeds, everything, but the damn thing refuses to automatically speed up the fan, I've got temps close to 100c when running prime and it wont go past the fan1_min speed :(

So annoying.. any fixes incoming to this problem? We need automatic fan speed based on temps, not manually... :(

EDIT: Fanspeed stays at whatever value I set fan1_min. Default is 2000. My fan1_manual is set to ZERO.

Tests by Alex Murray indicate that the SMC heat protection starts at 95 degC, after which the temperature levels out at 85 degC. It would be great to have that confirmed also on your model.

In addition, if the 5,5 is one of those with one fan, the temperature sensor support is poor for those models. If you would like to run the test scripts in this post [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096) and report the result here, that would be great. Thanks!

---

### Post by Aybara on 2010-04-30
> **npfthunfan said:**
> That seems to be the problem everyone has... 

I do the min fan speed hack... 
```
echo 6000 | sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
```
(Fan 2 appears to follow suit when increasing fan1's min)

I seemed to get a decrease in GPU temp by setting the Graphics to Higher Performance in OSX

I think I'll try that one as well. Do you put it in a shell script and run it as a Startup Application?

How fast did your fans spin in idle without this fix?

---

### Post by npfthunfan on 2010-04-30
> **Aybara said:**
> I think I'll try that one as well. Do you put it in a shell script and run it as a Startup Application?

How fast did your fans spin in idle without this fix?

I haven't done the shell script... it is a good idea though... fans just sit at 2000 (default) otherwise... until the temp hits 85-95

---

### Post by kosumi68 on 2010-04-30
> **npfthunfan said:**
> I haven't done the shell script... it is a good idea though... fans just sit at 2000 (default) otherwise... until the temp hits 85-95

Is it 85 or 95 or does it vary? I am asking to understand if the temperature threshold changed to the worse in models 2009 and later.

---

### Post by npfthunfan on 2010-04-30
I just ran full CPU in OS X, temp ran up to 100º without any fan response... I then aborted the test

---

### Post by kosumi68 on 2010-04-30
> **npfthunfan said:**
> I just ran full CPU in OS X, temp ran up to 100º without any fan response... I then aborted the test

Just to clarify, Apple's own OSX let you run the CPU up to 100 degC without increasing fan speed from idle?

---

### Post by alexmurray on 2010-05-01
@kosumi68 - today I had the fans speed up when CPU temp was only ~75C on my MBP51 during normal CPU intensive tasks (but other temps where different) as opposed to the the 95C which I saw before during artificial tests. This leads me to believe that either the SMC does some averaging of temps and perhaps has some hysteresis built in so it responds slowly to changes.... will try some more testing and monitoring and see if I can't figure more out.

---

### Post by kosumi68 on 2010-05-01
@alex - I see, thanks. It could well be that the effect of different SMC models is smaller than the effect of having several GPUs, only one fan, etc.

---

### Post by npfthunfan on 2010-05-03
> **kosumi68 said:**
> Just to clarify, Apple's own OSX let you run the CPU up to 100 degC without increasing fan speed from idle?

I just reset the SMC then repeated the test and videoed it... You can't really read stuff... but you get my lovely voice [http://www.youtube.com/watch?v=8j8ugN7dUbk](http://www.youtube.com/watch?v=8j8ugN7dUbk)

---

### Post by kosumi68 on 2010-05-03
> **npfthunfan said:**
> I just reset the SMC then repeated the test and videoed it... You can't really read stuff... but you get my lovely voice [http://www.youtube.com/watch?v=8j8ugN7dUbk](http://www.youtube.com/watch?v=8j8ugN7dUbk)

By the looks of it, OSX behaves just as (badly as) Ubuntu for this particular test, then. Very interesting. Thanks!

---

### Post by orengolan on 2010-08-10
my question might not be related to this thread but it's relevant to mackbook 5.1. I hope it's ok to post here.


In the past I installed ubuntu 9.4 on my macbook (5.1).
now i try to run the live CD of 10.4 and the menu is not even showing up. I also tried on another macbook, with mac os on it and nothing showed up. I tried both ubuntu and xubuntu.

is there a bug with 10.4 that not allowing install on macbookpro 5.1?

---

### Post by hyper84 on 2010-08-10
delete post

---

### Post by SwedishWings on 2010-08-23
Hi folks, 

I wrote a C daemon for fans speed control a few days ago, after getting annoyed with the heat. Is anyone interested in testing it on other mac's (i have only MacBook Pro 5,1)?

/Mike

---

### Post by dngfng on 2010-08-23
> **SwedishWings said:**
> Hi folks, 

I wrote a C daemon for fans speed control a few days ago, after getting annoyed with the heat. Is anyone interested in testing it on other mac's (i have only MacBook Pro 5,1)?

/Mike


Hi - I have got a MacBook Pro 6,2
I have also noticed that it seems to run fairly hot. Even so I thought that fan control came along with the mactel-support package:

> 
The mactel PPA modules needed on Ubuntu on this MBP are applesmc-dkms  (driver for light sensor, temperatures, fans and keyboard backlight),  mbp-nvidia-bl-dkms (driver for the LCD panel backlight) and pommed  (daemon to control them all). 
 Source: [https://help.ubuntu.com/community/MacBookPro6-2/Lucid](https://help.ubuntu.com/community/MacBookPro6-2/Lucid)

If this is not the case I would defiantly like to test your daemon

---

### Post by SwedishWings on 2010-08-23
Ok, here is my daemon hack. Please let me know of it's working.

Se README for instructions.

/Mike

EDIT: Updated the code

EDIT2: It turns out that it compiles and runs fine without build-essential. It also works fine without applesmc-dkms, except that there is no sensor labels present when using '-s' debug option.

---

### Post by SwedishWings on 2010-08-23
> **orengolan said:**
> my question might not be related to this thread but it's relevant to mackbook 5.1. I hope it's ok to post here.


In the past I installed ubuntu 9.4 on my macbook (5.1).
now i try to run the live CD of 10.4 and the menu is not even showing up. I also tried on another macbook, with mac os on it and nothing showed up. I tried both ubuntu and xubuntu.

is there a bug with 10.4 that not allowing install on macbookpro 5.1?

It works just fine on mine. Just pres and hold the C key after turning the mac on. Have you tried to do Alt-Cmd-R-P to reset the mac before booting from CD?

---

### Post by bash321 on 2010-08-29
thanks for the macfanctl! helped alot!
should ask if mactel can do more testing???????????
it should be located in the mac repistory for future releases!!!!!
It's ridiculous why it over heats!!!!!
btw work with 10.04! hopefully it will work in 10.10!

---

### Post by bash321 on 2010-08-29
this aint related either i had similar problems booting ubuntu especially 10.04 ever since apple released an update for its firmware last year!!! it takes a long time for ubuntu to even boot, one of the main things i found that refit wont even boot usb anymore at all!!! on 5.1 macbook pro's. try a different cd or wait it can take a long time, it sometimes froze for me when i was doing an install. Also make sure you have the latest 10.04 iso image.

---

### Post by SwedishWings on 2010-08-29
> **bash321 said:**
> thanks for the macfanctl! helped alot!
should ask if mactel can do more testing???????????
it should be located in the mac repistory for future releases!!!!!
It's ridiculous why it over heats!!!!!
btw work with 10.04! hopefully it will work in 10.10!

Happy it get to use :D

I have mailed Henrik Rydberg and asked if he/they want to merge it in the repo but have not received a reply yet.

I've had no time to try 10.10 yet, but if applecms-dkms works as in 10.04 it should not be a problem as far as i can see.

/Mike

---

### Post by SwedishWings on 2010-08-29
> **bash321 said:**
> this aint related either i had similar problems booting ubuntu especially 10.04 ever since apple released an update for its firmware last year!!! it takes a long time for ubuntu to even boot, one of the main things i found that refit wont even boot usb anymore at all!!! on 5.1 macbook pro's. try a different cd or wait it can take a long time, it sometimes froze for me when i was doing an install. Also make sure you have the latest 10.04 iso image.

I've had no problems neither installing or booting from CD. Have you tried to do Cmd-Alt-R-P a few times before booting from the CD?

---

### Post by bash321 on 2010-08-29
its all good now since i have ubuntu on my mac! but now that i have this code for my fans in my mac! it is brilliant since i had been using ubuntu 9.04, 9.10 on my mac it always use to get hot so i never use to use ubuntu. now i can finally make sure my system is not overheating! this best thing about is that when an application freezes and is non responsive the fan speed goes quicker to keep the cpu cooler!

---

### Post by swejap on 2010-11-01
I have installed all necessary tools to try and keep the macbook 5,1 stay cold, or at least not to hot and it's a big improvement compared to a few months ago when I tried 10.04 on my macbook. My average temperature is around 60-65 and RPM hits around 4500. Yesterday I tried to copy some files from my external HDD to the internal but had to stop be because the fan went crazy and cpu and gpu temperature hit 100! I was seriously thinking this is the end of my macbook...

I guess there wont be any fix soon for the heat issue and cpu load problem? Was thinking about checking the thermal compound paste to replace it with new one and eventually ad an copper modification to the gpu. I've done this before with a broken gpu on dell xps m1330 and made a huge different in heat problem, so maybe it works for macbook as well? Just tired of this damn laptop. Can't believe Apple charge so much for hardware that sucks and on purpose makes the costumers in need of their software only...

---

### Post by linuxopjemac on 2010-11-01
Did you try the macfanctld which is in the Mactel repository?

---

### Post by swejap on 2010-11-01
> **linuxopjemac said:**
> Did you try the macfanctld which is in the Mactel repository?

yes I have it installed and seem to do it's work. Is there some way to check the so everything works like it should? Can I provide you with some information about my system to see if anything is missing or system is configured right way?

I installed the following so far 

pommed
gpommed
macfanctld (latest version 0.3)
applesmc-dkms

I have the option to install **mbp-nvidia-bl-dkms** and **bcm5974-dkms**, but they are for macbook pro right?

---

### Post by linuxopjemac on 2010-11-01
bcm5974-dkms gives support for the multitouch trackpad present in modern MacBooks.

mbp-nvidia-bl-dkms is the backlight driver in macbook pro's

---

### Post by swejap on 2010-11-02
so in other words I dont need them. I think its no use to run Ubuntu on Macbook to be honest. It way to unstable with the hardware. If using my macbook at the library for studies, the fan just makes to much noise and is very distracting for others trying to focus on reading. Also reading abut how people struggle with getting everything to function normally seems a bit to much work at the moment.

I really like Ubuntu and use it as my main operative system on other computers. But when it comes to Macbook 5,1 and Ubuntu, Apple really managed to make people not use any other operative system than their own. This sucks and I will sell this peace of crap laptop.

---

### Post by SwedishWings on 2010-11-06
A new release of macfanctld is out, see: [http://ubuntuforums.org/showpost.php?p=10079620&postcount=65](http://ubuntuforums.org/showpost.php?p=10079620&postcount=65)

---

