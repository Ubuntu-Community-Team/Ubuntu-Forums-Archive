---
title: "[SOLVED] fprint help!! - fingerprint reader"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by master_kernel on 2008-04-18
```
$ fprint_demo 
uru4000:error [dev_init] interface claim failed
fp:error [fp_dev_open] device initialisation failed, driver=uru4000
```

And see the screenshot below.

Anyone know why this error comes up? When I use sudo it works fine.

---

### Post by sam_delta on 2008-04-18
you need super user (sudo) privileges to access hardware
can some1 confirm this?

i dont know if theres a way to make it work without sudo some1 else might be able to help here

---

### Post by Dr Small on 2008-04-18
Apparently the device requires root privilages.

---

### Post by master_kernel on 2008-04-18
Other ubuntu users have been able to do it without root privs though...

EDIT: Found this: [http://reactivated.net/fprint/wiki/Installation](http://reactivated.net/fprint/wiki/Installation)
My problem is in troubleshooting, but the fix doesn't apply to Ubuntu specifically.

---

### Post by Dr Small on 2008-04-18
Who owns /proc/bus/usb and what group?
```
ls -l /proc/bus/usb
```

I would certainly try changing the group to something else that I am in, or create a new group and put myself in it. (I don't know what groups control usb)

Dr Small

---

### Post by master_kernel on 2008-04-18
> **Dr Small said:**
> Who owns /proc/bus/usb and what group?
```
ls -l /proc/bus/usb
```

I would certainly try changing the group to something else that I am in, or create a new group and put myself in it. (I don't know what groups control usb)

Dr Small
Output:
$ ls -l /dev/bus/usb
total 0
drwxr-xr-x 2 root root 100 2008-04-18 19:59 001
drwxr-xr-x 2 root root 120 2008-04-18 20:07 002
drwxr-xr-x 2 root root  60 2008-04-18 17:52 003
drwxr-xr-x 2 root root  60 2008-04-18 17:52 004
drwxr-xr-x 2 root root  60 2008-04-18 20:06 005
drwxr-xr-x 2 root root 100 2008-04-18 21:18 006

/proc/bus/usb had nothing in it.

How would I go about changing the group ownership?

---

### Post by Dr Small on 2008-04-18
Try:
```
sudo chgrp -R *group* /dev/bus/usb/
```

You never can tell, but is worth a try, I guess.

---

### Post by master_kernel on 2008-04-19
> **Dr Small said:**
> Try:
```
sudo chgrp -R *group* /dev/bus/usb/
```

You never can tell, but is worth a try, I guess.
Thanks! I used the plugdev group since it made the most sense. Your advice worked perfectly.

---

### Post by Dr Small on 2008-04-19
> **master_kernel said:**
> Thanks! I used the plugdev group since it made the most sense. Your advice worked perfectly.
No problem, sir.
Glad to have been able to help :)

Dr Small

---

