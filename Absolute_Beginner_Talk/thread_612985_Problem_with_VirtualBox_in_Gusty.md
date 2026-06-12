---
title: "Problem with VirtualBox in Gusty"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-11-14
I have just installed VirtualBox and started to set it up, but when I click on the SETTINGS button I get an error about my USB :confused:

All my usb ports are working fine, has anyone got any ideas??

Please see attached screen shot for error message

Cheers
Ian

---

### Post by schorsch on 2007-11-14
The version in the repos (virtualbox-ose) does not include USB support. Please remove it and install the "full" version from the official website [here]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by ianb72 on 2007-11-14
> **schorsch said:**
> The version in the repos (virtualbox-ose) does not include USB support. Please remove it and install the "full" version from the official website [here]("http://www.virtualbox.org/wiki/Downloads")

Thats where I installed it from, I didn't know it was in the repo's

---

### Post by schorsch on 2007-11-14
Uhm, well, o.k.. According to [this]("http://www.virtualbox.org/wiki/User_FAQ") page "... Ubuntu removed support for /proc/bus/usb/* ...". So I added the following line to /etc/fstab
```
none    /proc/bus/usb   usbfs   devgid=120,devmode=664          0 0
```, rebooted and everything worked fine. Be sure to replace the value for "devgid" with the actual gid for  the group vboxusers.

---

### Post by ianb72 on 2007-11-14
Great I got the USB working.

Now when I start VBox I get another error about permissions and I cant seem to find how to add me the user group, I thought it did it on install :( :confused:

Here is a screen shot of the error

---

### Post by overdrank on 2007-11-14
> **ianb72 said:**
> Great I got the USB working.

Now when I start VBox I get another error about permissions and I cant seem to find how to add me the user group, I thought it did it on install :( :confused:

Here is a screen shot of the error

go to systems>administration>users and groups
type your administrator password
select manage groups,look for the group VBOXUSERS,
select properties and check the box in front of your user name.

---

### Post by schorsch on 2007-11-14
... or in a terminal type
```
sudo adduser schorsch vboxusers
```
Subsitute schorsch with your username, logout, login and this problem should be solved.

---

### Post by lazyart on 2007-11-21
Confirming that this works.  To find the devgid of vboxusers, try ```
cat /etc/groups | grep vboxusers
```

---

