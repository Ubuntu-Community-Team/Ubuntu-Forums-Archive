---
title: "[PPC] - Hardy frequency-scaling - working for you?"
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by stream303 on 2008-05-03
Just wondering how frequency scaling with the default powernowd is working for anybody?

After installation, I like to make sure that frequency scaling is working by using the cpu frequency-monitoring applets, or doing it manually by letting the system settle for a little bit and doing
```
cat /proc/cpuinfo
```

I found that on my G5 iMac, it was always running at full-tilt at 1.8ghz, even with powernowd installed by default.

To fix this so that it would scale back to 900mhz when not doing much of anything, I had to use CPUDYN as my frequency scaler instead.

Anyone else having any problems with powernowd not doing frequency scaling on a default Hardy?

---

### Post by Harpoon on 2008-05-03
Intel Core2Duo in a Lenovo laptop also runs full tilt with no apps running (both cores). The CPU scaling monitor reports "frequency scaling not supported."  Strange, as it worked perfectly in Feisty

---

### Post by stream303 on 2008-05-03
Wow, that's interesting even though you are running an intel box.  I wonder how many might not even realize that their boxes are running hot due to this?

Have you tried uninstalling powernowd, and using another scaler, like cpudyn?

---

### Post by Harpoon on 2008-05-07
Stream:
Interesting, indeed.  More interesting is that fooling around trying to cix it, I installed some things that had configuration conflicts, making it worse.  The idle core tem was over 70 C which is unreasonable.

I also lost my internet connection for a few days, so I did a complete fresh install.  The processor no longer locked at max speed, but did spend a lot of time up there when it should have been idle.

Powernowd said  that it was set at mode 1 (aggressive) (default) and I blame that setting, mostly.  I have manually reset it to "2" which is "passive" and it seems to run cooler (52-53 C) .  I have no idea what the setting 0 (SINE) or 3 (LEAP) translate to in human terms. 

If anyone is reading this, run sudo powernowd -vv -d to see what is going on.  You get hints on screen on how to change settings.

I don't yet know if those changes are persistent, since I have not rebooted yet.

---

### Post by usererror on 2008-09-30
> **stream303 said:**
> Just wondering how frequency scaling with the default powernowd is working for anybody?

After installation, I like to make sure that frequency scaling is working by using the cpu frequency-monitoring applets, or doing it manually by letting the system settle for a little bit and doing
```
cat /proc/cpuinfo
```

I found that on my G5 iMac, it was always running at full-tilt at 1.8ghz, even with powernowd installed by default.

To fix this so that it would scale back to 900mhz when not doing much of anything, I had to use CPUDYN as my frequency scaler instead.

Anyone else having any problems with powernowd not doing frequency scaling on a default Hardy?

[COLOR="Lime"]THANK YOU!!![/COLOR]

```
sudo apt-get remove powernowd
``` removed the unworking CPU / Processor scaling.

```
sudo apt-get install cpudyn
``` installed the **working** CPU / Processor scaling!  As soon as I installed this the CPU usage monitor instantly started showing the speed monitor go up and down!

This is on a G4 ibook 1.46mhz processor.

---

### Post by jrb114 on 2008-11-13
I've got a, "Me, too," here.

Thanks. After installing cpudyn (which automatically removes powernowd), the frequency scaling kicked in straight away on my iBook 1.33GHz.

J

---

### Post by stream303 on 2008-11-14
It is even simpler now - you just have to start the process to install cpudyn, and it will automatically remove powernowd for you - and it's just as easy to switch back - just install powernowd, and cpudyn is gone.

Note that powernowd can be fixed with an edit to the /etc/init.d/powernowd file:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

(see about half-way down the page) if you'd prefer that.  I still prefer the lower latency of cpudyn after experimenting with the two.

---

