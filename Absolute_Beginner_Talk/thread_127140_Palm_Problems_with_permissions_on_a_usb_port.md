---
title: "Palm Problems with permissions on a usb port"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-02-08
My palm wont sync. Ive tried to follow the instructions but i get to this:

> 
Port

    Your handheld is represented to the computer as a special file in the /dev directory. The name of the file will vary from system to system. In many cases however, it will be /dev/pilot. Other possible values are /dev/ttyS0 or /dev/ttyS1 for serial cradles (under Windows, these would be referred to as COM ports), or items under /dev/usb/, for USB cradles.

    You will need to make sure that your user account has read, write, and execute permissions on this device. To add those permissions, become root with the su command and enter the command chmod a+wrx /dev/ttyS0. Substitute the name of the device you are setting.

    If you have not chosen the correct device, you will get an error message when you click OK.



This is fine except that ttyUSB1 is only available when you press the sync button on the palm! When the port dissapears (when the palm goes off). also the permissions +orwx +grwx  cannot be set with chmod and it simply says operation not permitted.

I know the palm is there from device manager and it picked up the name and id from the unit.. it just wont sync. Is there a way of telling it to start talking instead of relying on autodetect?

---

### Post by dgrafix on 2006-02-08
Here you can see my attempt, but the permissions are still the same!?!?

xxd@LinuxPC:/dev$ sudo chmod +orwx,+grwx pilot
xxd@LinuxPC:/dev$ ls pilot -la
lrwxrwxrwx  1 root root 7 2006-02-08 15:15 pilot -> ttyUSB1
xxd@LinuxPC:/dev$ ls ttyUSB1 -la
crw-rw-r--  1 root dialout 188, 1 2006-02-08 15:15 ttyUSB1
xxd@LinuxPC:/dev$ sudo chmod +orwx,+grwx ttyUSB1
xxd@LinuxPC:/dev$ ls ttyUSB1 -la
crw-rw-r--  1 root dialout 188, 1 2006-02-08 15:15 ttyUSB1


if i go into sh and dmesg i get this )lots of timesÖ=

[4295043.342000] visor ttyUSB1: Device lied about number of ports, please use a lower one.

---

