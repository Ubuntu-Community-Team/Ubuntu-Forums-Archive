---
title: "Broadcom 4306's light doesn't come on..."
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by ishift on 2006-10-29
ok, so i searched already.

and, i've tried all the how-tos and instructions.

the light still doesn't come on.

any ideas on what the problem is? i read that the ndiswrapper version that worked on dapper doesn't work on edgy, but i can't seem to compile the new version of ndiswrapper.

not only that, ndiswrapper shows that the hardware and driver are present and installed correctly...

..yet the light is not on.

any help?](*,) :-k

---

### Post by ishift on 2006-10-29
apologies for the quick bump, but i gotta get this fixed before school tomorrow :)

---

### Post by ishift on 2006-10-30
any ideas?

---

### Post by wieman01 on 2006-10-30
Perhaps you have not blacklisted the Linux driver. Try this howto: [http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

---

### Post by ishift on 2006-10-30
yup. already tried that

---

### Post by wieman01 on 2006-10-30
Ahem... Broadcom 4306... I think that's a known issue & relates to the driver that is shipped with the device. Trying to resolve the same problem in another thread. You can try my last proposal which includes a link to the driver that allegedly works: 

[http://www.ubuntuforums.org/showthread.php?t=284216&page=5]("http://www.ubuntuforums.org/showthread.php?t=284216&page=5")

Hope this help.

---

### Post by ishift on 2006-10-30
> **wieman01 said:**
> Ahem... Broadcom 4306... I think that's a known issue & relates to the driver that is shipped with the device. Trying to resolve the same problem in another thread. You can try my last proposal which includes a link to the driver that allegedly works: 

[http://www.ubuntuforums.org/showthread.php?t=284216&page=5]("http://www.ubuntuforums.org/showthread.php?t=284216&page=5")

Hope this help.

i tried your method. here's what i got after inputting the code to scan:

```
iwlist wlan0 scan
```

```
wlan0    Interface doesn't support scanning.
```

when the wireless used to work, it used eth0

i tried to scan that as well:

```
eth0     no wireless extensions.
```

oh and there's no light on either.

---

### Post by ishift on 2006-10-30
bump

edit:

i did some more searching and doing

```
find /sys | grep led
```

gives:

```
/sys/class/input3/capabalities/led
/sys/class/input2/capabalities/led
/sys/class/input1/capabalities/led
/sys/class/input0/capabalities/led
```

there's no mention of an led for bcm43xx...

---

### Post by ishift on 2006-10-30
ok, not only is the light not on, but when i click on the network icon (the 2 monitors in the top panel), i get this error:

"Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device"

---

### Post by PriceChild on 2006-10-30
In case you don't get another reply, may i advise you that Edgy is really a dev platform.

It is unstable, and there have been several regressions, such as broadcom support.

I advise you to use Dapper... check the sticky in abs beginners.

---

### Post by ishift on 2006-10-30
good point. the thing is, it did work before. which is why i'm confused. but i guess you're right.

thanks though!

---

### Post by ishift on 2006-10-30
ok, i'm in a hurry, but my friend (who's very good in linux) basically installed ndiswrapper-utils 1.8 and did the usual modprobe and all that.

and it works wonderfully.

:D

i hope that helps someone else too..

---

