---
title: "Touchpad frozen after suspend on ibook g4"
date: 2009-11-17
forum: Apple Hardware Users
---

### Post by evilgold on 2009-11-17
Hello again all,

 I've finally gotten around to installing ubuntu on a PPC laptop, and everything is working great except for the touchpad. If i suspend the laptop the touchpad no longer works, although everything else seems to come back fine, and a USB mouse still works.

Is there any way to fix this? 

If nothing else could someone tell me the module i'd need to reload manually to try and get the mouse working without restarting.

---

### Post by kosumi68 on 2009-11-26
You might want to try adding a new file /etc/pm/sleep.d/20_touchpad to the pm configuration hooks, with the following text (replace module with the one appropriate for your touchpad)
```

#!/bin/sh

module=the-name-of-your-trackpad-module-goes-here

case "${1}" in
        suspend|hibernate)
		/sbin/rmmod $module
                ;;
        resume|thaw)
		/sbin/modprobe $module
                ;;
esac

```

Make sure the file is executable:
```

sudo chmod +x /etc/pm/sleep.d/20_touchpad

```

---

### Post by kosumi68 on 2009-11-26
(btw, your module might be called appletouch, but it all depends on what computer module you have)

---

### Post by evilgold on 2009-11-29
Thanks for the tip. I'm not sure how to find out what module my trackpad uses (lsmod doesnt list anything that looks like it).... however, i tried adding the scrip with appletouch as the module, but whenever i create and chmod  /etc/pm/sleep.d/20_touchpad my system will simply stop going to sleep all together.

The problem seems to be intermittent though, and sometimes i can fix it simply by putting the machine back to sleep and waking it up again.

---

### Post by linuxopjemac on 2009-11-30
you need powerpc-utils for the touchpad behavior, hope it helps for you

---

### Post by rednose0607 on 2009-11-30
Hi,
I think the driver is called evdev. At least is the one that I understand having a look at the logs. Not able to rmmod it though...
Bye

---

### Post by linuxopjemac on 2009-11-30
maybe with 
```
sudo rmmod -f evdev
```

---

### Post by rednose0607 on 2009-12-01
... unfortunally nope. tried rmmod -w and rmmod -f, either via script or via prompt or even kill -9 X process, from one of the tty. the module can't be removed ...
bye
r.
p.s.
being root naturally ...:)

---

### Post by linuxopjemac on 2009-12-01
Is it possible that evdev is used by another module and the other module needs to be removed first?

---

### Post by rednose0607 on 2009-12-01
Hi, 
well a rmmod -r should force the remove... but nope. Is not clear to me how the trackpad is managed in karmic on a ppc g4. I don't see doing a lsmod any specific module ... For example I used the workaround to remove a module and loading it in the cycle suspend/remove with the wifi (b43 module). I'm still not able to automate it in the script, but if I do it explicity (root prompt) it works. I guess for the trackpad is not so strightforward.
Ah, btw, if you have attached a mouse everything works fine. I mean that the mouse is managed correctly in suspend/resume cycle ...
bye
r.

---

