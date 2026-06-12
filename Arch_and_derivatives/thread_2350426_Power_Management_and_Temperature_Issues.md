---
title: "Power Management and Temperature Issues"
date: 2017-01-24
forum: Arch and derivatives
---

### Post by thomaszimmerman93 on 2017-01-24
Hello all, 


I'm currently running Arch Linux and Cinnamon *3.2.8* on a Macbook Pro *11,3* with the *4.8.13-1* kernel and a NVIDIA *GT-750M* GPU that I'm driving with the proprietary NVIDIA driver. I'm experiencing some power management and temperature issues and I'm wondering if you guys can provide any insight onto how I can rememdy them. 


System temps are between *60* and *85* depending on load and usually idle around *70*.Obviously this is very hot compared to temperatures when running in MacOS which are usually between *30* and *50* depending on load. Additionally, my battery life is only around *2 hours* when driving two external monitors and *3 hours* without. With MacOS, however, I can usually expect around *5-8 hours* of battery life when driving two monitors. 


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




**LM-Sensors output:**


```

Dir: /home/tj 
Usr: tj - Tue 24, 11:28AM > sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +65.0 C  (high = +84.0 C, crit = +100.0 C)
Core 0:         +62.0 C  (high = +84.0 C, crit = +100.0 C)
Core 1:         +60.0 C  (high = +84.0 C, crit = +100.0 C)
Core 2:         +65.0 C  (high = +84.0 C, crit = +100.0 C)
Core 3:         +62.0 C  (high = +84.0 C, crit = +100.0 C)


applesmc-isa-0300
Adapter: ISA adapter
Left side  : 3675 RPM  (min = 2160 RPM, max = 6156 RPM)
Right side : 3681 RPM  (min = 2000 RPM, max = 5700 RPM)
TB0T:         +33.5 C  
TB1T:         +33.5 C  
TB2T:         +31.5 C  
TBXT:         +33.5 C  
TC0E:         +64.2 C  
TC0F:         +65.5 C  
TC0P:         +53.5 C  
TC1C:         +62.0 C  
TC2C:         +62.0 C  
TC3C:         +64.0 C  
TC4C:         +62.0 C  
TCGC:         +61.0 C  
TCSA:         +62.0 C  
TCTD:          +0.0 C  
TCXC:         +64.2 C  
TG0D:         +61.8 C  
TG0P:         +56.5 C  
TG1D:         +64.0 C  
TG1F:         +63.5 C  
TG1d:         +58.0 C  
TH0A:         +35.8 C  
TH0B:         +35.8 C  
TH0F:         -45.2 C  
TH0R:         -45.2 C  
TH0V:         +37.0 C  
TH0a:         +35.8 C  
TH0b:         +35.8 C  
TH0c:        -127.0 C  
TM0P:         +47.2 C  
TM0S:         +46.5 C  
TP0P:         +47.5 C  
TPCD:         +52.0 C  
TW0P:         +45.5 C  
Ta0P:         +36.2 C  
TaSP:         +35.8 C  
Th1H:         +44.0 C  
Th2H:         +52.2 C  
Ts0P:         +31.5 C  
Ts0S:         +37.0 C  
Ts1S:         +37.0 C  

```


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




**Power Management Configuration:**


1. **powertop** I have set *powertop* to run at start with a systemd service module with the *--auto-config* parameter that uses a config I created with the *--calibrate* flag. Here is the report that it generates for me: [https://tjzimmerman.com/Files/public/powertop.html](https://tjzimmerman.com/Files/public/powertop.html)


2. **cpupower** I'm using *cpupower* with the conservative governor as defined in /etc/default/cpupower. However, I have not defined a maxium cpu frequency in that file.


3. **mbpfan-git** I'm using *mbpfan-git* with the following configuration. I derived the settings by using the advice in the config file and at [https://ineed.coffee/3838/a-beginners-tutorial-for-mbpfan-under-ubuntu](https://ineed.coffee/3838/a-beginners-tutorial-for-mbpfan-under-ubuntu)


```

Dir: /home/tj 
Usr: tj - Tue 24, 11:28AM > cat /etc/mbpfan.conf 
[general]
# see https://ineed.coffee/3838/a-beginners-tutorial-for-mbpfan-under-ubuntu for the values
min_fan_speed = 2000	# put the *lowest* value of "cat /sys/devices/platform/applesmc.768/fan*_min"
max_fan_speed = 6156	# put the *highest* value of "cat /sys/devices/platform/applesmc.768/fan*_max"
low_temp = 55		# try ranges 55-63, default is 63
high_temp = 65			# try ranges 58-66, default is 66
max_temp = 84			# take highest number returned by "cat /sys/devices/platform/coretemp.*/hwmon/hwmon*/temp*_max", divide by 1000
polling_interval = 1	# default is 7 seco

```


4. **cpufreqd** I have installed *cpufreqd* but have left it to use the default configuration.


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




**Additional Tweaks I've performed:**


1. I disabled the *gpe17* and *sci* *ACPI Interupts* as I noticed that I was experiencing hundreds of thousands of them when I ran *grep . -r /sys/firmware/acpi/interrupts*. There are *0* interrupts listed now, though:


```

Dir: /home/tj 
Usr: tj - Tue 24, 11:14AM > grep . -r /sys/firmware/acpi/interrupts
/sys/firmware/acpi/interrupts/ff_gbl_lock:       0   enabled
/sys/firmware/acpi/interrupts/gpe15:       0   invalid
/sys/firmware/acpi/interrupts/gpe05:       0   invalid
/sys/firmware/acpi/interrupts/gpe3F:       0   invalid
/sys/firmware/acpi/interrupts/gpe33:       0   invalid
/sys/firmware/acpi/interrupts/gpe2F:       0   invalid
/sys/firmware/acpi/interrupts/gpe23:       0   enabled
/sys/firmware/acpi/interrupts/gpe1F:       0   invalid
/sys/firmware/acpi/interrupts/gpe13:       0   invalid
/sys/firmware/acpi/interrupts/gpe0F:       0   invalid
/sys/firmware/acpi/interrupts/gpe03:       0   invalid
/sys/firmware/acpi/interrupts/gpe3D:       0   invalid
/sys/firmware/acpi/interrupts/gpe31:       0   invalid
/sys/firmware/acpi/interrupts/gpe2D:       0   invalid
/sys/firmware/acpi/interrupts/gpe21:       0   invalid
/sys/firmware/acpi/interrupts/gpe1D:       0   invalid
/sys/firmware/acpi/interrupts/gpe11:       0   invalid
/sys/firmware/acpi/interrupts/ff_pwr_btn:       0   enabled
/sys/firmware/acpi/interrupts/ff_slp_btn:       0   invalid
/sys/firmware/acpi/interrupts/gpe0D:       0   disabled
/sys/firmware/acpi/interrupts/gpe01:       0   invalid
/sys/firmware/acpi/interrupts/ff_pmtimer:       0   invalid
/sys/firmware/acpi/interrupts/gpe3B:       0   invalid
/sys/firmware/acpi/interrupts/gpe2B:       0   invalid
/sys/firmware/acpi/interrupts/gpe1B:       0   invalid
/sys/firmware/acpi/interrupts/gpe38:       0   invalid
/sys/firmware/acpi/interrupts/gpe0B:       0   invalid
/sys/firmware/acpi/interrupts/gpe28:       0   invalid
/sys/firmware/acpi/interrupts/gpe18:       0   invalid
/sys/firmware/acpi/interrupts/gpe08:       0   invalid
/sys/firmware/acpi/interrupts/sci:       0
/sys/firmware/acpi/interrupts/gpe36:       0   invalid
/sys/firmware/acpi/interrupts/gpe26:       0   invalid
/sys/firmware/acpi/interrupts/error:       0
/sys/firmware/acpi/interrupts/gpe16:       0   enabled
/sys/firmware/acpi/interrupts/gpe06:       0   enabled
/sys/firmware/acpi/interrupts/ff_rt_clk:       0   disabled
/sys/firmware/acpi/interrupts/gpe34:       0   invalid
/sys/firmware/acpi/interrupts/gpe24:       0   invalid
/sys/firmware/acpi/interrupts/gpe14:       0   invalid
/sys/firmware/acpi/interrupts/gpe04:       0   invalid
/sys/firmware/acpi/interrupts/gpe3E:       0   invalid
/sys/firmware/acpi/interrupts/gpe32:       0   invalid
/sys/firmware/acpi/interrupts/gpe2E:       0   invalid
/sys/firmware/acpi/interrupts/gpe22:       0   invalid
/sys/firmware/acpi/interrupts/gpe1E:       0   invalid
/sys/firmware/acpi/interrupts/gpe12:       0   invalid
/sys/firmware/acpi/interrupts/gpe0E:       0   invalid
/sys/firmware/acpi/interrupts/gpe02:       0   invalid
/sys/firmware/acpi/interrupts/gpe3C:       0   invalid
/sys/firmware/acpi/interrupts/gpe30:       0   invalid
/sys/firmware/acpi/interrupts/gpe2C:       0   invalid
/sys/firmware/acpi/interrupts/gpe20:       0   invalid
/sys/firmware/acpi/interrupts/gpe1C:       0   invalid
/sys/firmware/acpi/interrupts/gpe10:       0   invalid
/sys/firmware/acpi/interrupts/gpe39:       0   invalid
/sys/firmware/acpi/interrupts/gpe0C:       0   invalid
/sys/firmware/acpi/interrupts/gpe00:       0   invalid
/sys/firmware/acpi/interrupts/gpe3A:       0   invalid
/sys/firmware/acpi/interrupts/gpe29:       0   invalid
/sys/firmware/acpi/interrupts/gpe2A:       0   invalid
/sys/firmware/acpi/interrupts/gpe19:       0   invalid
/sys/firmware/acpi/interrupts/gpe1A:       0   invalid
/sys/firmware/acpi/interrupts/gpe09:       0   enabled
/sys/firmware/acpi/interrupts/gpe37:       0   invalid
/sys/firmware/acpi/interrupts/gpe0A:       0   invalid
/sys/firmware/acpi/interrupts/gpe27:       0   invalid
/sys/firmware/acpi/interrupts/gpe17:       0   disabled
/sys/firmware/acpi/interrupts/sci_not:       0
/sys/firmware/acpi/interrupts/gpe07:       0   enabled
/sys/firmware/acpi/interrupts/gpe35:       0   invalid
/sys/firmware/acpi/interrupts/gpe25:       0   invalid
/sys/firmware/acpi/interrupts/gpe_all:       0

```


2. I've tried to install the *linux-macbook* package from the aur but it fails to build and pass a integrity check whenever I try. 


3. Computer backlight and keyboard light have been turned down. 


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




**My Questions**


1. What can I do to reduce my core temperatures and increase my battery life? I have several friends running Linux on their MBPs without the same issues I'm experiencing so I know it's possible. One runs Arch Linux with a custom kernel and the other uses Xubuntu 16.04. Both of them experience temps in the *40-55* degree range and battery lives of *4-6 hours.*


2. Do you guys see anything in my *powertop* report that I can do to help my situation? [https://tjzimmerman.com/Files/public/powertop.html](https://tjzimmerman.com/Files/public/powertop.html)


3. Should I be using a different configuration of power management daemons?


4. Does anyone else run Linux on a MBP? What distro? What are your battery life/temps like?

---

### Post by howefield on 2017-01-24
Thread moved to the "*Arch and derivatives*" forum.

---

