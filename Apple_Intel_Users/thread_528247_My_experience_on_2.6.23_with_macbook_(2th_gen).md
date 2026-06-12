---
title: "My experience on 2.6.23 with macbook (2th gen)"
date: 2007-08-17
forum: Apple Intel Users
---

### Post by kestaz on 2007-08-17
sorry for poor english .. very sorry ...

i am installed ubuntu yestarday ... so  i want  exchange my experience...

i downloaded .config from gentoo wiki .. added some parameters(hpet timer, ho_hz, usb_suspend) and other from powertop suggestions.. 

Main problem: sky2 makes many wakeups even then i don't use eth0. so i blacklisted this module..

Problems:

root@box:/# modprobe speedstep_centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.23-rc3-maclinux-mactelpatches-macbook-core2duo/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Device or resource busy

So I added acpi-cpufreq in /etc/modules .. loaded it.. now as i think acpi chaning cpu speed ? hmm.. i want use speedstep driver..

and i want ask.. which powernowd, powersave, cpufreqd daemon to use ??? 

acpi-cpufreq makes many wakeups.. don't know if it's right.. any suggestions ?

root@box:/# acpid 
acpid: can't open /proc/acpi/event: Device or resource busy

seems to be something wrong with events ...

why ? because :

then i unplug mag safe cable :

i got this:

root@box:/# cat /proc/acpi/ac_adapter/ADP1/state 
state:                   on-line

and

root@box:/# acpi -T
     Battery 1: charged, 99%

even if cable is unplugged

after some time i make acpi -T again:

root@box:/# acpi -T
     Battery 1: charged, 98%

or i need to wait some minutes ? don't think so.....

switching cable on:

root@box:/# acpi -T
     Battery 1: charging, 94%, 00:20:47 until charged

hmm.. everything ok .. but applets didn't inform my about time( usage of computer) and when mag safe cable is removed...

This situation is because:
state:                   on-line

state on-line every time ...


i am using m$ mouse ...
got this:
root@box:/# dmesg | grep i8042
i8042.c: No controller found.

i had hp nx6325 where was problem ... battery state don't changed because of psmouse driver..

maybe same situation ??

how can i enable two finger tapping and touchpad key press to get right mouse button ?

---

### Post by cyberdork33 on 2007-08-17
can you say which version of ubuntu you installed?

---

### Post by kestaz on 2007-08-17
Ubuntu 7.10 (Gutsy Gibbon) Tribe 3

[http://cdimage.ubuntu.com/releases/gutsy/tribe-3/](http://cdimage.ubuntu.com/releases/gutsy/tribe-3/)

---

### Post by cyberdork33 on 2007-08-17
> **kestaz said:**
> how can i enable two finger tapping and touchpad key press to get right mouse button ?

most of your comments are a bit technical, plus you are using non-final versions of software so there are going to be issues anyway. Did you get the latest mactel patches?

as for your touchpad:
[http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)

I don't think there is any solution available to get touchpad button press working. It is not supported by the driver.

---

### Post by Gen2ly on 2007-08-17
Using an rc kernel there gonna be issues I expect.

---

### Post by kestaz on 2007-08-18
So which kernel version i need to choose ? at this moment ?

---

### Post by cyberdork33 on 2007-08-18
> **kestaz said:**
> So which kernel version i need to choose ? at this moment ?
the normal ubutnu kernel in the repository should work fine.
The latest stable vanilla kernel release is 2.6.22

---

### Post by shivathreya on 2007-08-19
I have compiled 2.6.22 with mactel patches. Now battery comes to around 2 hours though a great improvement from 1 hour I used to get.

I am attaching my kernel config file.

Best Regards,

Shiva

---

### Post by cyberdork33 on 2007-08-19
> **shivathreya said:**
> I have compiled 2.6.22 with mactel patches. Now battery comes to around 2 hours though a great improvement from 1 hour I used to get.

I am attaching my kernel config file.

Best Regards,

Shiva

Can you say exactly what machine your config is for? The same as the opening poster's?

---

