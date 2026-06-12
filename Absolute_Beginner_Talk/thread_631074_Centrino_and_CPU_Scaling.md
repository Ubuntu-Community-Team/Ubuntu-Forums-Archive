---
title: "Centrino and CPU Scaling"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by ubuntu_amatuer on 2007-12-04
I don't know if this issue has been brought up before, but with Ubuntu running in my Centrino which has a max freq of 1.7 GHz at battery mode it reduces to 800 MHz which is the lowest frequency. 

Now my issue is when I had windows in this machine the frequency would go as low as 400 - 500 MHz. Is there a way I could achieve these frequency range with Ubuntu or is it not possible.

ThankYou

---

### Post by mellowd on 2007-12-04
I've installed an app called powernowd which will show you exactly what frequencies your CPU should be capable of.

---

### Post by ubuntu_amatuer on 2007-12-04
According to powernowd my frequency's lowest is 800 MHz, but I know under Windows the frequency has gone lower than that. 

Could this be an issue with Windows giving the wrong information or Ubuntu / powernowd not being able to down scale or support lower frequencies in the Centrinos ?

---

### Post by lswest on 2007-12-04
i'm not sure, but honestly 800MHz is the best idea, its the best performance for the power usage.  Don't really think it would be great if it dropped below 800...might cause some issues.  My processor (Dual core amd at 1.8GHz) only goes down to 800 and i'm quite happy with that.  i mean, if you want it down to 400MHz i'm not sure you can even force it down that far, but you can just run a powernowd command to change the mode to power saver (or something like that) so that it stays at 800MHz longer, reducing power usage.  (more information on the man pages of powernowd).  hope it helps

---

### Post by mellowd on 2007-12-04
I don't think it ever went down to 500Mhz. powernowd is very good at telling you exactly what the cpu is capable of. You could check Intel's site to see exactly what they say about that model.

---

