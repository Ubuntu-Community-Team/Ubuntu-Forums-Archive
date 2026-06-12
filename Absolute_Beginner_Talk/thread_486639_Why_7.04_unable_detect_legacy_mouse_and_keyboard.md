---
title: "Why 7.04 unable detect legacy mouse and keyboard ?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-06-28
Hello--

I've put Xubuntu and Ubuntu on many machines, but this one has me stumped.

I have a Compaq Presario 5441 (specs below) upon which I dual boot Win 2000 Pro and Xubuntu 7.04 .

The legacy PS2 mouse and the keyboard operate fine in Windows 2000.
On the Xubuntu side, I get nada.  No interaction between those devices and response on screen.

One possible clue is that the BIOS is from before 2000, and when Xubuntu first load it says something about pre-2000 thus needing to force ACPI.  I can't find any BIOS after 2000 for this machine.

I am wondering how this could be?  I've never had this problem in installing X/Ubuntu over 20 times on different machines including old ones like this.

Thank you and specs below:
Compaq Presario 5441 ... 475 MHz AMD K6-2 ... 384MB PC100 RAM ... Sis 530/620 chipset (8 MB graphics memory enabled in BIOS)

---

### Post by smoker on 2007-06-28
does the keyboard and mouse work ok with the live-cd? if so, then the install driver for both may be damaged, corrupted in some way, there may be some info in the log files if you can access them via the live cd.

best of luck

---

### Post by ukripper on 2007-06-28
Can you post output of this:

```
dmesg| tail 
```

---

### Post by Average_Joe on 2007-06-28
Thanks to you both.  In the live of Xubuntu, I am able to get the keyboard to respond to CTRL + ALT + F1, so that I can shut down Xorg and get to a terminal prompt.

The mouse does not work in the live Xubuntu.

So here is the output of my 



```
dmesg | tail
```


```
.
.
.
>


[  362.694347] fuse init (API version 7.8)
[  364.183415] Adding 530104K swap on /dev/hda5.  Priority:-1
[  367.513486] NET: Registered protocol family 17
[  400.783662] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  400.784206] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  400.785332] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  400.785975] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  418.044681] lp0: using parport0 (interrupt-driven)
[  423.135954] ppdev: user-space parallel port driver
[  437.244316] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)


>
>
```

Any further help greatly appreciated in getting the mouse to work on Ubuntu.  Thanks!!

---

### Post by Average_Joe on 2007-06-28
: bumper :

---

### Post by Average_Joe on 2007-06-29
bump for the Euro crowd who were assisting yesterday

---

### Post by ukripper on 2007-06-29
What version of kernel are you using? Try different kernel.

---

