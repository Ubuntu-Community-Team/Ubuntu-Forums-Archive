---
title: "Console not recognizing files"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by koresho on 2008-03-25
Hey everyone, I have a little issue. 
I am using Ubuntu 8.04 x86 Beta, and I am not sure if this a beta problem or a user error so that's why I posted here, mods please move as necessary. This is about the console in general, not just the aircard installation. 

I need to get my Verizon Aircard USB720 modem installed. I have followed the steps [here]("http://kenkinder.com/evdo-pc5740/") and [here,]("http://http://ubuntuforums.org/archive/index.php/t-470119.html") but the issue is that whenever I type in console commands they do not return what the tutorial says to expect. This is on anything that has to do with the console, not just these specific tutorials.
For example, I type
```
koresho@koresho-ubuntu:~$ cd /
koresho@koresho-ubuntu:/$ cat /proc/driver/nvidia/agp/status
```
But what it returns is:
```
cat: /proc/driver/nvidia/agp/status: No such file or directory
```.

If I type
```
modprobe ohci-hcd
``` it gives me no return, just starts another line.
```
koresho@koresho-ubuntu:/$ cat /proc/bus/usb/devices > devices
bash: devices: Permission denied
``` is what I get trying to pull up a list of USB devices, and if I try it on root I get this:
```
koresho@koresho-ubuntu:/$ sudo -i
[sudo] password for koresho: 
root@koresho-ubuntu:~# cat /proc/bus/usb/devices > devices
cat: /proc/bus/usb/devices: No such file or directory
```

Any help? I'm fine with consoles and command lines... the problem that I have is that I am not getting what I am apparently supposed to get. 
Thanks in advance!

---

### Post by Oldsoldier2003 on 2008-03-25
> **koresho said:**
> Hey everyone, I have a little issue. 
I am using Ubuntu 8.04 x86 Beta, and I am not sure if this a beta problem or a user error so that's why I posted here, mods please move as necessary. This is about the console in general, not just the aircard installation. 

I need to get my Verizon Aircard USB720 modem installed. I have followed the steps [here]("http://kenkinder.com/evdo-pc5740/") and [here,]("http://http://ubuntuforums.org/archive/index.php/t-470119.html") but the issue is that whenever I type in console commands they do not return what the tutorial says to expect. This is on anything that has to do with the console, not just these specific tutorials.
For example, I type
```
koresho@koresho-ubuntu:~$ cd /
koresho@koresho-ubuntu:/$ cat /proc/driver/nvidia/agp/status
```
But what it returns is:
```
cat: /proc/driver/nvidia/agp/status: No such file or directory
```.

If I type
```
modprobe ohci-hcd
``` it gives me no return, just starts another line.
```
koresho@koresho-ubuntu:/$ cat /proc/bus/usb/devices > devices
bash: devices: Permission denied
``` is what I get trying to pull up a list of USB devices, and if I try it on root I get this:
```
koresho@koresho-ubuntu:/$ sudo -i
[sudo] password for koresho: 
root@koresho-ubuntu:~# cat /proc/bus/usb/devices > devices
cat: /proc/bus/usb/devices: No such file or directory
```

Any help? I'm fine with consoles and command lines... the problem that I have is that I am not getting what I am apparently supposed to get. 
Thanks in advance!

there is nothing wrong with the console. the files you are trying to cat just don't exist

---

### Post by koresho on 2008-03-25
So then according to Linux I do not have any USB devices attached to my computer?

---

### Post by OffAxis on 2008-03-25
some commands need to be run as 'sudo'. Typically a 'Permission Denied' error is returned when it's not there. Try

```
sudo lsusb
```

to see your usb devices.

---

### Post by koresho on 2008-03-25
```
koresho@koresho-ubuntu:~$ sudo lsusb
```
and
```
root@koresho-ubuntu:~# lsusb
```
both sit there forever with a blinking cursor on the next line. I have waitied more than 10 minutes, and it should not- I have a Core 2 Duo T7280 @ 2Ghz and 4gb (only 3 addressed, of course) of memory, along with SATA 3gbps hard drives. Performance lag should not be an issue...

---

