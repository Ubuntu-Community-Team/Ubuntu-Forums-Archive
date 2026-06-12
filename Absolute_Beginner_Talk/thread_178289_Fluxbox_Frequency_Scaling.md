---
title: "Fluxbox Frequency Scaling"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by xtacocorex on 2006-05-17
Since there is no "Semi-Advanced" section to the forums, I'm posting here  even though most of the threads I start are pretty technical, ie: [http://www.ubuntuforums.org/showthread.php?t=112072](http://www.ubuntuforums.org/showthread.php?t=112072).

I would like to get fluxbox to recognice my cpu frequency scaling on my laptop since the default outside of KDE is set to performance. 

The following works:
```

sudo chmod 666 /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

I have tried to make an init script that would do the permission change for me on boot, but I don't know what order I should put it in and if that is even allowed. Then I would have my fluxbox autostart file set the scaling governor when it loads.

When I get home from work, I can post what I put in my init script, but it's just the default init script setup with nothing in restart and stop, but the chmod command from above minus the sudo.

EDIT: If a mod wants to move this to a more acceptible location, please do so.

---

### Post by xtacocorex on 2006-05-17
Mad props goes to robotgeek for reminding me on irc about crontabs and how to make them. 

This problem has been figured out.

EDIT:
```
sudo crontab -e
```
Type @reboot command

---

