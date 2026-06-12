---
title: "Problem: Resume from Suspend"
date: 2013-11-03
forum: Any Other OS
---

### Post by vmnrao on 2013-11-03
Running Mint 15, but I've found most of these problems are identical and these forums are much more active:

[COLOR=#333333][FONT=Lucida Grande]**Problem**[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]While my desktop appears to sleep ok, it does not resume from suspend (monitor turns on, but black screen and CTRL-ALT-F1 doesn't help). [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]Moving the mouse and pressing any buttons does nothing. (I have to do a hard power off)[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]===========================================================[/FONT][/COLOR]
**Suspend Log**
$ cat /var/log/pm-suspend.log | grep Fail
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory



[COLOR=#333333][FONT=Lucida Grande]**Investigating Resume UUID**[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande] (UUIDs obfuscated intelligently)[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande][0] % cat /etc/initramfs-tools/conf.d/resume[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]RESUME=UUID=ABC[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande][0] % sudo blkid[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]/dev/mapper/cryptswap1: UUID="DEF" TYPE="swap" [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]as you can see the UUID in my resume file [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]**does not match**[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande] my cryptswap1 UUID. (neither does it match [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]**any**[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande] of my volumes listed by blkid)[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I also did "ls -l /dev/disk/by-uuid" and of course the UUID specified by the resume doesn't match any of my disks.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I'm unable to get the blkid (using the blkid command) for the partition that the cryptswap1 partition is on, while the cryptswap is mounted.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande][0] % cat /etc/fstab[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]#UUID=HIJ none swap sw 0 0[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]/dev/mapper/cryptswap1 none swap sw 0 0[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Okay, now I'm really confused. None of these UUIDs match.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]===========================================================[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I installed Linux Mint Mate 15 x64 choosing the "encrypt home dir" option. So my swap is encrypted as well. (done automatically during install)

Any ideas?[/FONT][/COLOR]

---

### Post by Toz on 2013-11-03
*Moving to the **Other OS/Distro** forum.*

Swap file is not used when suspending (only when hibernating) so the swap information is not the issue. More likely, its related to your video card. Can you tell us more about your system:

1. The make and model

2. The video card(s) and drivers:
```
lspci -k | grep -iA2 VGA
```

3. The complete suspend log:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated. Note: you may need to install pastebinit. 

4. Any relevant info from your syslog:
```
cat /var/log/syslog | grep PM:
```

---

### Post by vmnrao on 2013-11-03
> **Toz said:**
> *Moving to the **Other OS/Distro** forum.*
Swap file is not used when suspending (only when hibernating) so the swap information is not the issue. More likely, its related to your video card. Can you tell us more about your system:



Thanks for trying to help! Here's the info:

> **Toz said:**
> 1. The make and model
Lenovo Thinkstation D20 


> **Toz said:**
> 
2. The video card(s) and drivers:

Card: NVIDIA GTX 670 4GB
Driver: 313.30-0ubuntu1

02:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 670] (rev a1)
    Subsystem: NVIDIA Corporation Device 097a
    Kernel driver in use: nvidia



> **Toz said:**
> 
3. The complete suspend log:

[http://pastebin.com/qLs0R6rR](http://pastebin.com/qLs0R6rR)


> **Toz said:**
> 
4. Any relevant info from your syslog:
```

Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7a0000 - 00000000df7c6000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c6000 - 00000000df7c8000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c8000 - 00000000e0000000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
Nov  3 11:16:17 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Nov  3 11:16:17 lenovo-linux kernel: [    2.093943] PM: Registering ACPI NVS region [mem 0xdf7c6000-0xdf7c7fff] (8192 bytes)
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7a0000 - 00000000df7c6000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c6000 - 00000000df7c8000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c8000 - 00000000e0000000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
Nov  3 11:21:37 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Nov  3 11:21:37 lenovo-linux kernel: [    2.097971] PM: Registering ACPI NVS region [mem 0xdf7c6000-0xdf7c7fff] (8192 bytes)
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7a0000 - 00000000df7c6000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c6000 - 00000000df7c8000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c8000 - 00000000e0000000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
Nov  3 12:11:01 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Nov  3 12:11:01 lenovo-linux kernel: [    2.199781] PM: Registering ACPI NVS region [mem 0xdf7c6000-0xdf7c7fff] (8192 bytes)
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7a0000 - 00000000df7c6000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c6000 - 00000000df7c8000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c8000 - 00000000e0000000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
Nov  3 12:55:50 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Nov  3 12:55:50 lenovo-linux kernel: [    2.194050] PM: Registering ACPI NVS region [mem 0xdf7c6000-0xdf7c7fff] (8192 bytes)
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7a0000 - 00000000df7c6000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c6000 - 00000000df7c8000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c8000 - 00000000e0000000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
Nov  3 13:15:04 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Nov  3 13:15:04 lenovo-linux kernel: [    2.188975] PM: Registering ACPI NVS region [mem 0xdf7c6000-0xdf7c7fff] (8192 bytes)
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7a0000 - 00000000df7c6000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c6000 - 00000000df7c8000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000df7c8000 - 00000000e0000000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
Nov  3 18:17:40 lenovo-linux kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Nov  3 18:17:40 lenovo-linux kernel: [    2.099832] PM: Registering ACPI NVS region [mem 0xdf7c6000-0xdf7c7fff] (8192 bytes)
```

---

### Post by neu5eeCh on 2013-11-04
Try this:

[http://xubuntugeek.blogspot.com/2012/11/solved-suspend-causes-reboot-on-sony.html](http://xubuntugeek.blogspot.com/2012/11/solved-suspend-causes-reboot-on-sony.html)

And see what happens. Who knows? Might work...

---

### Post by Toz on 2013-11-04
According to the log file, your system is not returning from suspend (as opposed to returning from suspend but not delivering a video signal). There is nothing in syslog to help diagnosis the issue.

In addition to @VTPoet's suggestion, can you also try this:
```
sudo modprobe -r tmp_tis
```
...then:
```
sudo pm-suspend
```
...and see if the system returns. If it does, run:
```
sudo modprobe tpm_tis
```
...to reload the module.

You might also want to try [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug").

---

