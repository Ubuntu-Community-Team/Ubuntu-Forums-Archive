---
title: "Edgy and fans"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Proshka on 2006-10-28
Hi,

I recently upgraded from Dapper to Edgy and now I cannot stop the fans from working. Most of the time they are on even when I only have a Firefox window open. I have spent hours browsing forums and tried almost everything I read to find a solution. During my Dapper days the laptop was very quiet, but now it is really annoying. Any suggestion will be greatly appreciated. 

Proshka

---

### Post by Klaidas on 2006-10-28
Stopping the fans is a BAD, BAD idea. Even if you don't have any windows open...
Anyway, did you use to stop them in dapper?

---

### Post by Proshka on 2006-10-28
The problem is that they were running under Dapper as one should expect, I mean, running a bit, then stopping when the temperature went down, working faster when many applications were running, etc. Now it happens they are working almost all the time and even with minimum CPU requirements (same problem when I was a Microsoft user...). It has something to do with Edgy, I guess, since it did not happen with Dapper and I have not installed any new software after the upgrading.

---

### Post by AgenT on 2006-10-28
It is possible that the upgrade replaced a configuration file that you edited to make the power management of the fans work. Chech that configuration file again.

Also note that even if you did not change anything yourself, there could be a new configuration file that has fan power management disabled by default.

If you are using laptop-mode-tools, make sure you remove the laptop-mode package (*very* outdated version of laptop-mode-tools).

Edit the correct config file as it may be disabled by default.

[http://www.samwel.tk/laptop_mode/](http://www.samwel.tk/laptop_mode/)

---

### Post by PriceChild on 2006-10-28
Please remember that it is regressions like this in some areas, (another being wireless) that make Edgy "edgy".

If you were running Dapper fine before, there is no real reason to upgrade.

"If it ain't broke, don't fix it"

---

### Post by Proshka on 2006-10-28
If you are using laptop-mode-tools, make sure you remove the laptop-mode package (*very* outdated version of laptop-mode-tools).

Edit the correct config file as it may be disabled by default.

[http://www.samwel.tk/laptop_mode/](http://www.samwel.tk/laptop_mode/)[/QUOTE]

Synaptic says that if I remove this package, I will have trouble with a lot of other packages related to Gnome (gnome-desktop-environment, -office, -power-manager, -session) as well as powermanagement-interface and acpi-support. Should I proceed anyway?

---

### Post by Proshka on 2006-10-28
> **PriceChild said:**
> Please remember that it is regressions like this in some areas, (another being wireless) that make Edgy "edgy".

If you were running Dapper fine before, there is no real reason to upgrade.

"If it ain't broke, don't fix it"

You are right, I should have stayed with Dapper. The fan problem is not the only one I have. I upgraded because I could not fix some audio and video issues, but I still have them in Edgy. Is it possible to go back to Dapper without reinstalling it and perhaps lose data and configurations?

---

### Post by PriceChild on 2006-10-28
> **Proshka said:**
> Is it possible to go back to Dapper without reinstalling it and perhaps lose data and configurations?nope sorry... its one way.

---

### Post by Proshka on 2006-10-28
> **PriceChild said:**
> nope sorry... its one way.

Thanks. I will try Edgy a bit more and before getting crazy by the fans I will wipe everything out to return to Dapper. A good lesson for future upgrades, anyway.

---

### Post by AgenT on 2006-10-28
> **Proshka said:**
> Synaptic says that if I remove this package, I will have trouble with a lot of other packages related to Gnome (gnome-desktop-environment, -office, -power-manager, -session) as well as powermanagement-interface and acpi-support. Should I proceed anyway?
This means that you have package dependency problems. If you have laptop-mode-tools installed you should be able to remove laptop-mode. This may be due to you having non-official Ubuntu packages installed or worse, non-official Ubuntu repositories.

You may have the wrong version of laptop-mode installed (with wrong dependencies). Go here and download this version of the deb, then install it:
[http://packages.ubuntu.com/edgy/admin/laptop-mode](http://packages.ubuntu.com/edgy/admin/laptop-mode)
After you install it, try to remove it.

You should be able to remove it because I just did a test and it removed fine. If it does not, you have package dependency problems that you should first fix.

It works this way: NEVER install any unofficial package that has any type of dependency or you are asking for trouble. And as a rule of thumb, never install any unofficial package period. ;) Also, I have upgraded from Hoary Beta up until now. Hoary Beta was my first and only clean install of Ubuntu.


[quote=PriceChild]nope sorry... its one way.[/quote] This is not true. However, it does take some knowledge of how things work, and is not an easy endevour.

Check out my sig: "I apt-get dist-upgraded from Libranet to Debian Woody, from there to Sarge, and
from there to Ubuntu Hoary". If you can do it between distributions, you can do it between releases. And yes, none of those are downgrades, but downgrades work in a very similar fashion.

---

### Post by PriceChild on 2006-10-28
> **AgenT said:**
> This is not true. However, it does take some knowledge of how things work, and is not an easy endevour.

Check out my sig: "I apt-get dist-upgraded from Libranet to Debian Woody, from there to Sarge, and
from there to Ubuntu Hoary". If you can do it between distributions, you can do it between releases. And yes, none of those are downgrades, but downgrades work in a very similar fashion.Ok then... but its not reccomended, or easy.

---

### Post by AgenT on 2006-10-28
> **PriceChild said:**
> Ok then... but its not reccomended, or easy. Correct, it is not recommended and not something that is easy.

If fact, for those that are "regular" Ubuntu users, doing a clean install should not be a big problem since they don't edit their system by hand like some other users. Just backup /home/ and do a clean install. Then all that is left is installing any extra programs needed and multimedia packages. Copy and paste your /home/ contents and you are done. I would not recommend restoring your configuration files from /home/, however (they are hidden for a reason).

---

### Post by Proshka on 2006-10-28
> **AgenT said:**
> This means that you have package dependency problems. If you have laptop-mode-tools installed you should be able to remove laptop-mode. This may be due to you having non-official Ubuntu packages installed or worse, non-official Ubuntu repositories.

You may have the wrong version of laptop-mode installed (with wrong dependencies). Go here and download this version of the deb, then install it:
[http://packages.ubuntu.com/edgy/admin/laptop-mode](http://packages.ubuntu.com/edgy/admin/laptop-mode)
After you install it, try to remove it.

You should be able to remove it because I just did a test and it removed fine. If it does not, you have package dependency problems that you should first fix.


Thanks AgenT. I did what you told me and I could remove the package via Synaptic (I could not do anything with laptop-mode-tools). Is there anything else I should do now or just wait to see the results?

---

### Post by dillbertdabomb on 2006-10-28
your processor must be workin hard!

---

### Post by Proshka on 2006-10-28
> **dillbertdabomb said:**
> your processor must be workin hard!

Well, actually not. The system monitor usually shows a 6-12 % CPU usage and more than 30% when I click on it (it returns to the above values immediately). Now the fans are running very slowly, so it is enough to open a new Firefox tab for them to resume working louder. When I have a couple of applications running, they work at full speed.

---

### Post by AgenT on 2006-10-29
> **Proshka said:**
> Thanks AgenT. I did what you told me and I could remove the package via Synaptic (I could not do anything with laptop-mode-tools). Is there anything else I should do now or just wait to see the results?
You should keep laptop-mode-tools. Did you read the link to the laptop-mode-tools website? It gives information on how to edit the configuration files. Note that laptop-mode-tools controls your computer when you run on battery. Config file is here: /etc/laptop-mode/laptop-mode.conf
You can check if laptop-mode-tools is running (by default, it should only run when you are on battery - and this is the setting you want):
```
cat /proc/sys/vm/laptop_mode
``` 0 means it is off, anything but 0 means it is on.

You never explained in detail your problem. Does it always happen? When you are using the power supply? The battery? What computer do you have? Did you use any program in Dapper to control or fix this problem? You may also try looking (search for bugs) in [launchpad]("https://launchpad.net/distros/ubuntu/+bugs") to see if anyone else is having the same problem.

---

### Post by Proshka on 2006-10-29
> **AgenT said:**
> You should keep laptop-mode-tools. Did you read the link to the laptop-mode-tools website?You can check if laptop-mode-tools is running (by default, it should only run when you are on battery - and this is the setting you want). 

You never explained in detail your problem. Does it always happen? When you are using the power supply? The battery? What computer do you have? Did you use any program in Dapper to control or fix this problem? You may also try looking (search for bugs) in [launchpad]("https://launchpad.net/distros/ubuntu/+bugs") to see if anyone else is having the same problem.

Yes, I have read the information on the website and the laptop-mode.conf file, but, frankly speaking, I did not understand too much. One reason is my poor English, but the main one is the fact that I have never gone through this kind of things and of course I do not want to add more damage to my computer (although I should add that, apart from the fans, I do not have BIG problems or some that would stop the system from working). 

Coming back to your recommendations, cat /proc/sys/vm/laptop_mode showed # 2, so it is working.

Details: The laptop (Toshiba Satellite A75-S226, 3.06 GHz Pentium 4, 512 Mb RAM, 2 years old) works on AC almost all the time. When I used Dapper, I could have Amule, Firefox (two or three tabs), Abiword, Gnumeric and Adobe Reader open without any perceptible or annoying fan activity. That was something that I enjoyed a lot because  the fans were very busy working when I used Windows XP. I never touched anything related to sensors, fan control or anything, firstly because I did not need it and secondly because I did (and still do) not know how to do anything with that. With Edgy I open a Firefox window and the fans begin to run. The more applications open, the more fan activity, of course, and more heating. I put some paper blocks under the laptop and it seemed to work, but of course I would prefer something more sophisticated. I have also checked out the launchpad and yes, there are some bugs related to fans in two ways: fans not working at all or fans working too much. I also checked out the Ubuntu forums with the same results. 

To sum up, I miss the quiet working environment I had before this upgrade. The main reason to upgrade was simple: I have had some problems with OpenOffice (under Dapper and XP as well), video files and Wine, and when I begun reading that Edgy would be better in this, better in that, etc., I thought "ok, perhaps it will fix my problems", so I upgraded. Although I cannot deny that Edgy looks more beautiful than Dapper (I could also fix the blurry typography) and has a lot of improvements, I still have the same problems and some new ones: the fans, something related to the partition table and other minor things not so important.

---

### Post by AgenT on 2006-10-29
> reason is my poor English I understand. Do not worry. If you need me to explain anything in more detail or in a different way, please ask (and/or message me) and I will reword it. You should be proud. You write English very well and it is not your primary language. Most native English speakers are only able to speak one language. And a large number of them have a horrible command of their first and only language.

Now on to your problem:

It could be that your acpi is not working correctly. Also, check your BIOS settings in case you have not done so already.

Here are some ideas for you. This is as far as I can help you. Maybe someone with a Toshiba laptop can help you more than I.

CPU Frequency Scaling Monitor
Get this on your Desktop (if you are using GNOME). It is an applet. Right click on task bar -> Add to Panel. This will show you your CPU. If you are not doing anything and it is running at full speed, something is wrong. Your CPU should only run full power if there is something that needs it. For example, when you start a program, you should expect your CPU MHz to be much higher than when you are just reading a website.

System Monitor
Get it in the same place that you find CPU Frequency Scaling Monitor. Use it to watch your CPU usage. If your CPU is not doing anything, but CPU Freq Monitor shows that your CPU is running very hight, something is wrong. If System Monitor shows your CPU being high all the time, then the problem is with a program that you are using.

/sys/devices/system/cpu/cpu0/cpufreq/
In this folder you will find your CPU information and the ability to change settings (note that settings will be reset if your restart your computer). Please note that you probably cannot force any CPU frequency you would like on your CPU. Your CPU probably supports about 5 frequencies and you have to know what they are. For example:
```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
```This will show you your CPU speed.

/proc/acpi/fan
Your fan information and files to tweak should be in here. If not, look around in /proc/ as sometimes they are in another place. IBM is in /proc/acpi/ibm/fan/. You should be able to control your fans here. BE CAREFUL: you can turn off your fan and burn your CPU!!

If you find a tweak that works for you, you can always create a short script with the commands you used and have them load on startup (or just start the script yourself every time you boot the computer)

cpufreqd
cpufrequtils
These are utilities used to chance cpu frequency, however I have never used them and I think something else is used in Ubuntu by default.

> fully configurable daemon for dynamic frequency and voltage scaling
cpufreqd is meant to be a replacement of the speedstep applet you can find on
some other OS, it monitors the system status and selects the most appropriate
CPU level.  It is fully configurable and easily extensible through the many
available plug-ins (more to come).And here is something I found on the internet:
[http://www.irisvista.com/tech/index.htm](http://www.irisvista.com/tech/index.htm)

And this quote:
> I work in a computer shop in aberystwyth in west wales uk, i have come acros
s this problem before. its simply cured by removing the underside panel with
 the heat caution label on it. then removing the 4 outer screws that hold th
e heatsink to the cpu. remove the heatsink and clean it well. i usually use 
an unused paint brush to remove dust, then some brasso or other mild abrasiv
e metal polish to polish the part of the heatsink that comes into contact wi
th the cpu. also clean the contacting surface of the cpu. then apply your he
atsink paste, and replace the heatsink. and a can of compressed air can be u
sed for additional cleaning of dust inside the case. it is a pretty silly de
sign because it can clog up really easily.
Good luck!

---

### Post by Proshka on 2006-10-29
Thank you very much for your help. I tried everything you suggest and the results are the following:

BIOS: no references to ACPI whatsoever. 

CPU Frequency Scaling Monitor: no support for frequency scaling, just shows the processor maximum speed (3.07 GHz).

System monitor: nothing remarkable (very low usage when idle, no more than 35 % when using some applications).

/sys/devices/system/cpu/cpu0/cpufreq/: the folder cpufreq does not exist, so sudo cat /sys/devices/
system/cpu/cpu0/cpufreq/cpuinfo_cur_freq does not work.

/proc/acpi/fan: all folders under /acpi are either empty or with blank files (no information whatsoever).

cpufreqd and cpufrequtils: are they applets? I cannot make them work using the terminal.

Sensors are not working or are not accesible. By typing $ sensors I got: "Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!"

ACPI packages installed: acpi, acpid, acpi-support, but I found somewhere (I do not remember how I managed to get this information, but I was using the terminal or some system tools) that the current kernel does not support ACPI. 

This is what I have so far. The laptop whas idle for a couple of hours and the fans were working very quietly but constantly. I cleaned them with compressed air yesterday. As to disassemble the laptop, I do not have the guts to do it by now, but I will consider it if the fans continue working the way they are.

---

### Post by AgenT on 2006-10-29
> **Proshka said:**
> BIOS: no references to ACPI whatsoever.Have you looked for any "Power", "Processor" or "CPU" section? There may be a section where it askes you to  configure what power settings you want for battery and power supply. There may  be some option such as "Maximum Performance" - this option is BAD because it will force your CPU to maximum speed, which looks like what your computer is suffering from. You wan't to change these types of settings to something more decent like "normal" or even "battery save".

> CPU Frequency Scaling Monitor: no support for frequency scaling, just shows the processor maximum speed (3.07 GHz). This may be your problem. I find it strange that your new CPU does not support cpu scaling.

> System monitor: nothing remarkable (very low usage when idle, no more than 35 % when using some applications). That should be expected, especially when your CPU is always stuck at the highest frequency.

> /sys/devices/system/cpu/cpu0/cpufreq/: the folder cpufreq does not exist, so sudo cat /sys/devices/
system/cpu/cpu0/cpufreq/cpuinfo_cur_freq does not work. Again, this may point to your problem. You have a new CPU which should support cpu frequency scaling.

> /proc/acpi/fan: all folders under /acpi are either empty or with blank files (no information whatsoever). Is the /proc/acpi/fan folder empty? Are there any files? Just so you know, nothing under /proc/ is a real file. You cannot open these and they will always appear to be size 0mb because they are not files. Think of them as direct links to your hardware.

> cpufreqd and cpufrequtils: are they applets? I cannot make them work using the terminal.They are programs. You have to install them as they are not installed by default. You should try them. Search in Synaptic for them. I have never used them because my CPU scaling works in a different fashion than most laptops.

> Sensors are not working or are not accesible. By typing $ sensors I got: "Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!" I do not know about sensors so I cannot help you there.

> ACPI packages installed: acpi, acpid, acpi-support, but I found somewhere (I do not remember how I managed to get this information, but I was using the terminal or some system tools) that the current kernel does not support ACPI.  The current kernel does support ACPI as far as I know and has for a very long time now. What kernel are you using? (see below for further instructions)

> The laptop whas idle for a couple of hours and the fans were working very quietly but constantly. I cleaned them with compressed air yesterday. Has this made a difference?>  As to disassemble the laptop, I do not have the guts to do it by now, but I will consider it if the fans continue working the way they are.I understand and agree. Disassembling your laptop should be the last thing you do.

Please post the output of these commands in seperate code tags:
```
uname -a
cat /proc/cpuinfo
ls /sys/devices/system/cpu/
ls /sys/devices/system/cpu/cpu0/
ls /proc/acpi/fan
sudo lshw
```Watch out, that last command (sudo lshw) will give you a LOT of information. If you want, run this instead:
```
sudo lshw > ~/Desktop/lshw.txt
```This will save all that text to lshw.txt on your Desktop. You can then open that file and it will be much easier to copy/paste the output. Or you can just attach that file to your post.

From what information you have given so far, it appears that there is something wrong with how your CPU behaves. Your fans appear to work the way they are supposed to work. However, because your CPU is not behaving properly, it may be overheating and your fans are always trying to cool it.

And just so you can compare: my CPU frequency is usually at 600MHz and my CPU usage at about 15% when not opening programs. It does just up once in awhile and always when opening new programs up, but then quickly jumps back down to 600MHz and ~15% (which is only ~90MHz!!).

---

### Post by jd65pl on 2006-10-29
> A good lesson for future upgrades, anyway.

Edgy is not so much an upgrade to dapper as a cutting edge environment, the distrobution is there to test software as it is release while dapper is a more stable long term solution.

---

### Post by Proshka on 2006-10-29
Ok, AgenT, thanks again for your help and your time. 
New information:

Rechecked BIOS and no "Power", "Processor" or "CPU" sections and no ACPI anywhere either.  It is a Phoenix BIOS 1.01. 

/proc/acpi/fan: empty, no files.

Cpufreqd and Cpufrequtils: yes, I installed them used Synaptic but I cannot make them work. 

Sensors: one Gnome applet (a sensor monitor which is supposed to show temperature and fan speed) could not recognize any sensors. I did not know if it had something to do with this problem of if it could help anyway.

Outputs:

kid@Minerva:~$ uname -a
Linux Minerva 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

kid@Minerva:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Mobile Intel(R) Pentium(R) 4 CPU 3.06GHz
stepping        : 4
cpu MHz         : 3067.459
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pni monitor ds_cpl est tm2 cid xtpr
bogomips        : 6138.04

kid@Minerva:~$ ls /sys/devices/system/cpu/
cpu0

kid@Minerva:~$ ls /sys/devices/system/cpu/cpu0/
cache  crash_notes

kid@Minerva:~$ ls /proc/acpi/fan
Nothing appeared.

I have attached the other information. As to the fans, I understand that at least they are preventing the CPU from burning, but it is not normal. Cleaning the dust did not change their behaviour either. They continued working since my last posting even with 0% CPU usage. 

One more time, thanks. I hope/wish you may find out something helpful from the outputs.

---

### Post by Proshka on 2006-10-29
> **jd65pl said:**
> Edgy is not so much an upgrade to dapper as a cutting edge environment, the distrobution is there to test software as it is release while dapper is a more stable long term solution.

I know, but since Edgy was sooooo publicited as full of improvements, I hoped it would fix some issues I had with Dapper. My conclusion was meant to stress out the fact that I should have felt happy by keeping three or four old problems instead of falling into new ones just for being so impulsive/candid/ignorant/pretentious?. After all, I just want to get rid of Microsoft forever, but learning Linux this way it is being painful.

---

### Post by jd65pl on 2006-10-29
If you are experiencing problems that were handled by dapper you should probably flag them as regression. Linux should be seen as an alternative to windows not a replacement. However I agree that Edgy should have been more publicised as a different solution to dapper and not an upgrade.

---

### Post by Proshka on 2006-10-29
> **jd65pl said:**
> Linux should be seen as an alternative to windows not a replacement.

Well, I have found a lot of people in this forums who cannot even write the word "Microsoft" without repugnance. It is not my case:  I acknowledge the fact that they have many applications that work much better than the similar ones under Linux. However, I hope to live long enough to see Microsoft replaced by Linux one day.

---

### Post by AgenT on 2006-10-30
I found a program for you to check your power information, including temperature:
```
acpi -V
``` This should tell you 1) information about the battery 2) computer temperature 3) information about the power supply
> kid@Minerva:~$ uname -a
Linux Minerva 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux While you are using the correct number version of the kernel, you should know that 386 kernel can cause trouble for some users. For example, it would not let me use all of my memory. This kernel is NOT the default that Ubuntu uses.

Go into Synaptic and install this package:
```
linux-generic
```NOTICE: You have the Radeon 9100. If you installed closed source ATI drivers, then install this before you restart your PC. Install this *after* you install your new kernel (above), but before you restart:
```
linux-headers-generic
```Now install your ATI drivers again.

Restart your computer and run:
> uname -aIt should say 2.6.17-10-generic instead of 2.6.17-10-386.

> 
  *-core
       description: Motherboard
       product: EDW10
       vendor: TOSHIBA
       physical id: 0
       version: Null
       serial: 0123456789AB
       slot: SVGA-Out
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.10 (05/28/2004)
          size: 104KB
          capacity: 448KB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
If you notice under capabilities, it says your motherboard is capable of acpi. One possibility is that your motherboard BIOS does not show these capabilities in the menu anywhere and does not give you any option of changing them.

> 
*-cpu
          description: CPU
          product: Mobile Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: NWD
          size: 3100MHz
          capacity: 3200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pni monitor ds_cpl est tm2 cid xtpr
Under capabilities, you have acpi but you do NOT have cpufreq. This means that you cannot scale your CPU down and shows us why your cpu folder is lacking any cpu control links. They are lacking because your CPU does not support them.

Try this and see if your CPU supports power management.
```
cat /proc/acpi/processor/CPU/info
``` If your CPU supports power management and throddling (throttling means you can change the CPU MHz), it will state:
```
power management:        yes
throttling control:      yes
```To start cpufreqd, you should write:
```
/etc/init.d/cpufreqd start
```Does this folder exist on your system?:
```
/proc/acpi/thermal_zone/THM0/
``` If you have this, what links are listed?

You may want to try this:
```
cat /proc/acpi/thermal_zone/THM0/cooling_mode
``` Does it say "<setting not supported>"?

Even if CPU usage is very small, if the CPU does not have frequency scaling it will either get very hot very quickly or your fans will not understand that the CPU is not hot and turn on. Example: If I stay in the BIOS for about 2 minutes my fans turn on. Now the BIOS is NOT CPU intensive by any means; however, when in the BIOS CPU frequency scaling is turned off and the fans turn on.

Basically, what the problem is on your computer is the CPU not scaling down. This is what is needed and you need to figure out how to enable scaling on the CPU.

Websites that have more information for you:
[http://www.linux-on-laptops.com/hosted/mandrake-d480w/](http://www.linux-on-laptops.com/hosted/mandrake-d480w/)
[http://mandrivausers.org/index.php?showtopic=29653](http://mandrivausers.org/index.php?showtopic=29653)
[http://ubuntuforums.org/showthread.php?t=21930](http://ubuntuforums.org/showthread.php?t=21930)
[http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_A70-RW#CPU_Info](http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_A70-RW#CPU_Info)

---

### Post by Proshka on 2006-10-31
Latest news:

Linux-generic and linux-headers-generic were already installed, so I chose this option when booting. I never touched ATI drivers before, so I did not do anything this time.
Outputs:

kid@Minerva:~$ uname -a
Linux Minerva 2.6.17-10-generic #2 SMP 

kid@Minerva:~$ acpi -V
     Battery 1: charged, 100%
No support for device type: thermal
  AC Adapter 1: on-line

kid@Minerva:~$ cat /proc/acpi/processor/CPU/info
cat: /proc/acpi/processor/CPU/info: The file or folder does not exist.

kid@Minerva:~$ sudo /etc/init.d/cpufreqd start
 * Starting CPU Frequency daemon cpufreqd                                [fail]


/proc/acpi/thermal_zone/THM0/ does not exist (the folder thermal_zone is empty), so cat /proc/acpi/thermal_zone/THM0/cooling_mode does not work.

I continued looking for information on the forums and I confirmed the fact that a lot of people is experiencing problems with the fans after installing Edgy and not under Dapper. Other postings talk about compiling some modules because of ACPI problems; in fact, some have tried (with more or less success) enabling several options in GRUB: ACPI=force, ACPI=on, ACPI=off. I tried every single option without any results.  Toshiba has a very poor Linux support (I checked out the website), but Sourceforge mentions that there are some utilities for Omnibook and Satellite which are suppose to monitor different variables and which are being under development. This utilities should also be compiled into the kernel. I still have to check out the links you mentioned. Many, many thanks again.

---

### Post by AgenT on 2006-11-07
UPDATE:
Proshka sent a private message explaining that the problem was indeed with the CPU running at full speed. After further research, Proshka found [EmiFreq]("http://zzrough.free.fr/emifreq.php") that "is just a little applet for the Gnome 2 desktop to show and control the CPU frequency scaling for laptops thanks to the CPUFreq **/sys** interface of the Linux Kernel 2.6". Proshka's computer (Toshiba laptop) uses a different than usual CPU control mechanism and thus Proshka's CPU control links were in /sys, not in /proc. EmiFreq made it easy for Proshka to control the CPU frequency of his computer and no longer suffers from fans roaring at full speed. This was done by having the CPU frequency lower itself when not used, which uses less electricity, hence the CPU runs cooler. Because the CPU no longer becomes very hot, the fans do not turn on as much.

This is being posted for anyone in the future with a similar problem.

---

### Post by jd65pl on 2006-11-07
That little app may be quite useful in conserving some of my battery life! Thanks AgenT for the info!

---

### Post by Proshka on 2006-11-09
More info on the fans problem.

AgentT, I rechecked the information you kindly provided before. After installing the applet (EmiFreq) I had new outputs:

```
kid@Minerva:~$ ls /sys/devices/system/cpu/
cpu0  cpu1
```

It seems that now the processor was "splitted" into two, with 1.87 GHz each one. It is consistent with the minimum speed the applet shows when the laptop is idle.

```

kid@Minerva:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Mobile Intel(R) Pentium(R) 4 CPU 3.06GHz
stepping        : 4
cpu MHz         : 1867.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl est tm2 cid xtpr
bogomips        : 6138.52

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Mobile Intel(R) Pentium(R) 4 CPU 3.06GHz
stepping        : 4
cpu MHz         : 1867.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl est tm2 cid xtpr
bogomips        : 6134.10
```

```
kid@Minerva:~$ sudo powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 2 scalable units:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 1867Mhz - 3067Mhz (5 steps)
powernowd:   cpu1: 1867Mhz - 3067Mhz (5 steps)
```

I suppose the 5 steps refer to 5 different processor speeds, which is consistent with the way the applet controls the processor. The applet's menu has these options: performance, fixed speed, powersaving and automatic.The "fixed speed" option shows 2133, 2400, 2667 and 3067. Being 1870 the default speed, it totalizes 5 speeds. Now, the information on the developer's webpage shows lower values (beginning with 800 Mhz), so I suppose it can be customized. I wrote to him asking about that but I still have no answer. There is more info here: 

[http://packages.debian.org/unstable/gnome/emifreq-applet]("http://packages.debian.org/unstable/gnome/emifreq-applet")


When I was trying to install this I changed many things without keeping track of them. That was bad because at one moment the processor speed lowered to 387 Mhz but later it did not work again.

Now the information I have from other pages. It seems that some Toshiba laptops which are equipped with a Phoenix bios have some kind of trouble regarding to ACPI. Sourceforge has a patch to correct this (information in the attached file) but it is supposed to be included in the current kernel and still the problem remains (at least for me). There is a driver (Toshiba ACPI Driver) which is supposed to work on some laptops as well as a specific one for Omnibook and some Satellite models like mine: 

[http://memebeam.org/toys/ToshibaAcpiDriver]("http://memebeam.org/toys/ToshibaAcpiDriver")
[http://omnibook.sourceforge.net/doku.php]("http://omnibook.sourceforge.net/doku.php")

I do not know how useful this information may be. Do you think I should try to install the Omnibook patch and see what happens? The instructions seem to be easy, [http://omnibook.sourceforge.net/doku.php?id=install]("http://omnibook.sourceforge.net/doku.php?id=install"), but as I have no idea about modules and specifications I fear I may make things worse.

---

### Post by AgenT on 2006-11-09
> **Proshka said:**
> I suppose the 5 steps refer to 5 different processor speeds, which is consistent with the way the applet controls the processor. The applet's menu has these options: performance, fixed speed, powersaving and automatic.The "fixed speed" option shows 2133, 2400, 2667 and 3067. Being 1870 the default speed, it totalizes 5 speeds.So are you saying that the applet works for you? Does setting a fixed speed work? Also, try "powersaving" as that is probably what you want. This will use the minimum CPU power needed, but if you need more CPU power, then your CPU speed will increase. 
> **Proshka said:**
> Now, the information on the developer's webpage shows lower values (beginning with 800 Mhz), so I suppose it can be customized. I wrote to him asking about that but I still have no answer.This applet was created for multiple computers and processors, not just the one you have. The lower speeds are probably for other processors. Having 5 speeds available sounds about right.

> **Proshka said:**
> It seems that some Toshiba laptops which are equipped with a Phoenix bios have some kind of trouble regarding to ACPI. Sourceforge has a patch to correct this (information in the attached file) but it is supposed to be included in the current kernel and still the problem remains (at least for me). 
Does the following folder exist on your system?:
```
/proc/acpi/toshiba/
```If so, great. Play around with what is inside. If not, check if the module is loaded:
```
lsmod | grep toshiba
```Maybe the module is not loaded, but it exists (HINT: it exists on my computer, but is not loaded). To check that, try this:
```
modinfo toshiba_acpi
```If it does exist, but is not loaded, load the module like so:
```
sudo modprobe toshiba_acpi
``` Now go look in /proc/acpi/toshiba/ and play with the links (use cat to see what they say). Read the "Driver Use" section on the website you linked.


> **Proshka said:**
> There is a driver (Toshiba ACPI Driver) which is supposed to work on some laptops as well as a specific one for Omnibook and some Satellite models like mine
...
I do not know how useful this information may be. Do you think I should try to install the Omnibook patch and see what happens? The instructions seem to be easy, [http://omnibook.sourceforge.net/doku.php?id=install](http://omnibook.sourceforge.net/doku.php?id=install), but as I have no idea about modules and specifications I fear I may make things worse.DO NOT install that patch using those instructions. If you read the homepage, there is a link to deb files for Debian and Ubuntu already made for you! (see "Download" section). Here is a link to their supported (tested) laptop page:
[http://omnibook.sourceforge.net/doku.php?id=laptops](http://omnibook.sourceforge.net/doku.php?id=laptops)
Notice that your laptop is not listed. Also notice that every Toshiba A* does not have fan support. And it does not provide any CPU frequency scaling functions.

---

### Post by Proshka on 2006-11-10
> **AgenT said:**
> So are you saying that the applet works for you? Does setting a fixed speed work? Also, try "powersaving" as that is probably what you want.
The minimum speed cannot be changed under any of the options.

> This applet was created for multiple computers and processors, not just the one you have. The lower speeds are probably for other processors.

Is it right to have the processor working at 1.87 GHz even when the laptop is idle?

> Does the following folder exist on your system?:
```
/proc/acpi/toshiba/
```

No.

> If not, check if the module is loaded:
```
lsmod | grep toshiba
```

Nothing appears.

```
kid@Minerva:~$ modinfo toshiba_acpi
filename:       /lib/modules/2.6.17-10-generic/kernel/drivers/acpi/toshiba_acpi.ko
author:         John Belmonte
description:    Toshiba Laptop ACPI Extras Driver
license:        GPL
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        
srcversion:     E73B5ABFD06EC29F006E1E5
parm:           hotkeys_check_per_sec:uint
parm:           hotkeys_over_acpi:uint
```


```
kid@Minerva:~$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.17-10-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device
```
I have had this message from the very beginning of this thread.
> Notice that your laptop is not listed. Also notice that every Toshiba A* does not have fan support. And it does not provide any CPU frequency scaling functions.

Yes, you are right. I will choose my next laptop more carefully;)

---

### Post by AgenT on 2006-11-10
> **Proshka said:**
> Is it right to have the processor working at 1.87 GHz even when the laptop is idle?This is possible. It is hard to tell. I would highly recommend you visit Intel's website and look up the technical documentation of your CPU. Look for the frequency scaling details. This will save you a lot of time in the end because you may be trying to enable something that does not exist in your CPU. 1.87 GHz may or may not be the lowest. Try to find out officially from Intel.
> **Proshka said:**
> ```
kid@Minerva:~$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.17-10-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device
```I have had this message from the very beginning of this thread.It appears that this module is not made for your laptop. There is no reason to compile and install this module from the website you posted because you will have the same result.

> **Proshka said:**
> Yes, you are right. I will choose my next laptop more carefully;)Good idea.

---

### Post by Proshka on 2006-11-23
Hi AgentT,

First of all, thank you very much again for all the efforts you put on me during my troubles with this laptop. I have learnt a lot from your advices. By the way, in the meantime I did other awful things... I was trying to get rid of junk files to save some disk space and of course I wiped them out... along with other things, of course. (BTW; I swear I will always remember an advice I had from PriceChild on this thread: "If it is not broke, do not fix it"...). 
To sum up, I had to reinstall Edgy from scratch. Without doing anything more than playing around with the panel, now I see the processor is working at 1.87, 2.13, 2.40, 2.67 and 3.07 GHz, which I suppose it is what I was trying to do during the times I bothered you (throttling and so). In other words, thanks again!!!

Proshka (native Spanish speaker, just in case you may need any assistance.)

---

### Post by AgenT on 2006-12-06
> **Proshka said:**
> Hi AgentT,

First of all, thank you very much again for all the efforts you put on me during my troubles with this laptop. I have learnt a lot from your advices. By the way, in the meantime I did other awful things... I was trying to get rid of junk files to save some disk space and of course I wiped them out... along with other things, of course. (BTW; I swear I will always remember an advice I had from PriceChild on this thread: "If it is not broke, do not fix it"...). 
To sum up, I had to reinstall Edgy from scratch. Without doing anything more than playing around with the panel, now I see the processor is working at 1.87, 2.13, 2.40, 2.67 and 3.07 GHz, which I suppose it is what I was trying to do during the times I bothered you (throttling and so). In other words, thanks again!!!

Proshka (native Spanish speaker, just in case you may need any assistance.)You are very welcome. And look at it from this perspective: if you break it and then fix it, you learn how it works. Sometimes breaking things is a very good way of learning.

---

