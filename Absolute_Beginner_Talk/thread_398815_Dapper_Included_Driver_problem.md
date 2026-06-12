---
title: "Dapper Included Driver problem"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by deposition on 2007-04-01
Installed the "Dapper's Included Driver" from the restricted repository and my resolution  goes up as high as it should but all the windows are really messed up. In firefox when i scroll down nothing happens, as if the screen isnt refreshing itself. I remeber reading somewhere that ATI is known to have this problem but i cant find the fix. Does anyone kow anything about this?

---

### Post by FakeOutdoorsman on 2007-04-01
I had some trouble with my ATI card until I followed the instructions at the [Unofficial ATI Linux Driver Wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29").

If you have trouble with that guide post your questions here.

---

### Post by deposition on 2007-04-01
that is the exact guid i followed

---

### Post by FakeOutdoorsman on 2007-04-01
Did you try Method #2 from that guide as well?  Method 1 is for the open source drivers, and Method 2 is for the proprietary drivers from ATI.  Are you running Beryl?

Did you try reconfiguring X server?
```
sudo cp /etc/X11/xorg.conf xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg
```

If that doesn't help you can restore your backup:
```
sudo rm /etc/X11/xorg.conf
cp /etc/X11/xorg.conf.bak xorg.conf
```

Here's are some interesting threads that might help more than my recommendations:  [AIGLX bug?]("http://ubuntuforums.org/showthread.php?t=295052")

and another one:  [Firefox scrollbars really sluggish with beryl]("http://ubuntuforums.org/showpost.php?p=2343898&postcount=13")

---

