---
title: "Rollback to a prior version of x-org?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by da5id on 2006-08-27
Following these instructions [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper) at 11.2, I lost my working version of x-0rg.  All I have is a command line.  In terminal it made made a backup, but I failed to write down the backup command.  Does anyone know what it is?

--Gene

---

### Post by jimrz on 2006-08-27
> **da5id said:**
> Following these instructions [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper) at 11.2, I lost my working version of x-0rg.  All I have is a command line.  In terminal it made made a backup, but I failed to write down the backup command.  Does anyone know what it is?

--Gene

What exactly were you doing that trashed your xorg?

or, if you are certain that it is xorg.conf that got trashed, type
```
ls /etc/X11
```

look for xorg.conf.(or- or_)xxxxx to identify the correct file name of the backup, then
```
sudo cp /etc/X11/<whatever the backup is named> /etc/X11/xorg.conf
```

this will restore your previous config file

---

### Post by charbo on 2006-08-27
I am not quite sure what you are talking about here. 

If you mean that you have run 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

and you want to recover the original configuration, then all you need to do is
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
to copy the backup file to the original file.

I think what you need to do is edit the xorg.conf file. Use pico or nano or vi, if you know how to use it, and change the driver from "nv" to "nvidia". Following is how.

Type 
sudo nano /etc/X11/xorg.conf

look for section like 
Section "Device"
	[INDENT]  [/INDENT]Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	[INDENT][/INDENT]Driver		"nvidia"
	[INDENT][/INDENT]BusID		"PCI:1:0:0"

and change the Driver  "nv" to "nvidia".
Save the file, and reboot.

That's how I got my X working again after installing nvidia video card and driver.

I hope this solves the problem.

---

### Post by da5id on 2006-08-27
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable

---

