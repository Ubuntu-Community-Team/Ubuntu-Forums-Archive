---
title: "Bluetooth not working after suspend (MacBook C2D)"
date: 2007-09-06
forum: Apple Intel Users
---

### Post by Ganonzote on 2007-09-06
Hello,

I have a problem with my MacBook C2D (2007), all works fine, but **after suspending bluetooth doesn't works**, if I restart it works again, but if I suspend again it doesn't.

I'm running Gutsy, with 2.6.22-10-generic kernel, but when using Feisty (2.6.20 kernels) i have the same problem.

---

### Post by agni on 2007-09-08
I can confirm this. I'm running Feisty with 2.6.20. Interestingly my bluetooth mouse continues to partly work after a suspend (everything except the scroll wheel works).

---

### Post by Meck1982 on 2007-09-14
Same on my MacBook and Logitech MX900

---

### Post by cyberdork33 on 2007-09-14
Can you guys try restarting bluetooth to see if that makes things work again (without restarting the computer?)

```
sudo /etc/init.d/bluetooth restart
```or maybe even:

```
sudo /etc/init.d/bluetooth force-reload
```

---

### Post by linuxfood on 2007-09-28
> **cyberdork33 said:**
> Can you guys try restarting bluetooth to see if that makes things work again (without restarting the computer?)

```
sudo /etc/init.d/bluetooth restart
```or maybe even:

```
sudo /etc/init.d/bluetooth force-reload
```

I tested your suggestions, and they do not help.

However, by pure chance, I found that running
```
sudo /usr/sbin/hid2hci
```
after suspend fixes the problem.

I tried adding a script that runs that command to /etc/acpi/resume.d, but to no avail.

Thoughts anyone?

---

### Post by cattin on 2007-10-06
Similar to you, I also found out the running the command hid2hci solves my bluetooth problem. putting the following script in the folder /etc/acpi/resume.d solved it completely:

  more /etc/acpi/resume.d/99-rescue-bluetooth.sh
  #!/bin/sh

  sleep 5
  /usr/sbin/hid2hci

the sleep 5 seems to be doing part of the trick! I didn't tune 5 seconds. maybe the delay can be shortened. I don't mind to much as it takes a couple of seconds to enter the password anyways.

don't ask my we it solved my bluetooth problems. it just worked for me.

regards, Philippe

PS: my black macbook is by far the best linux laptop I've ever had. everything is working, except the camera (didn't yet try it) and the caps lock LED.

---

### Post by Dale Cooper on 2007-10-14
Cattin : thanks for the easy trick, will perfectly do the job until the issue gets fixed

---

