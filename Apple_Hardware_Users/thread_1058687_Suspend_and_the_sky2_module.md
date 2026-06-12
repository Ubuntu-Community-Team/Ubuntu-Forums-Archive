---
title: "Suspend and the sky2 module"
date: 2009-02-03
forum: Apple Hardware Users
---

### Post by hyperboloid on 2009-02-03
For a long time I experienced flaky suspend issues in Ubuntu on my MBP. Occasionally, suspend would hang. This seemed especially likely to happen if I suspended & resumed several times in succession with no intervening boot. After completing most of the suspend process, I would be left with a blank screen with blinking cursor in the upper left hand corner, with no keyboard. Had to force power off by holding the power button. 

Then I switched to connecting via ethernet, and this issue immediately became 100 times worse. I eventually discovered that if I physically unplugged the ethernet cable prior to suspend, it would suspend just fine. 

All of this confused me for quite a while, and I mistakenly suspected wicd as the culprit, and filed a bug report. It was suggested there to try unloading the sky2 module (which controls the NIC) on suspend. When I did that, all my issues with suspend immediately went away! I have now suspended/resumed successfully more than 20 times without a single failure.

So, it appears that there is an issue with sky2 which sometimes interferes with (kernel) suspend. I'm not sure which models might be affected. Is anyone else having a similar issue?  To check if your Ubuntu uses sky2 do
```
lsmod | grep sky2
``` 
in a terminal. To unload the module on suspend, edit the file /etc/pm/config.d/00sleep_module (using sudo or as root) and add the line
```
SUSPEND_MODULES="sky2"
```
to the end of the file, and save changes. 

Please report in this thread if you also have this problem, and list your model number and Ubuntu distribution.

---

### Post by cyberdork33 on 2009-02-03
All Intel iMacs and Macbook / Macbook Pros should have this ethernet hardware. Not sure about minis and Mac Pros

---

### Post by souled on 2009-02-04
I'm on a rev 3 MBP Ubuntu 8.10, and this didn't work for me. It seems like my laptop suspends fine, but the problem is waking up. When I try to resume, I can hear the hard drive, but I get no response from the screen or keyboard (no caps or num lock LED). I have to hold the power button to shut it down.

---

### Post by hyperboloid on 2009-02-05
> **souled said:**
> I'm on a rev 3 MBP Ubuntu 8.10, and this didn't work for me. It seems like my laptop suspends fine, but the problem is waking up. When I try to resume, I can hear the hard drive, but I get no response from the screen or keyboard (no caps or num lock LED). I have to hold the power button to shut it down.

Looks like this [bug report]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/144732") might be relevant? You could try setting 
```
gconftool --set /apps/compiz/general/screen0/options/sync_to_vblank 0 --type bool
```
as suggested there. Dunno if this applies to 8.10 though.

---

### Post by Ixtao on 2010-06-14
I have this problem as well on Lucid. There is no /etc/pm/config.d/00sleep_module file anymore. As I understand I'm putting the notification in /etc/defaults/acpi-support. 

My problem is mainly that after suspend LAN doesn't function at all anymore and only reboot helps. I tried unloading + loading the module, restarting nm-applet. Hope this helps.

---

