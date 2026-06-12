---
title: "Updated from 12.04 to 12.10: Screen Resolution dropped"
date: 2012-10-28
forum: Apple Hardware Users
---

### Post by wilberfan on 2012-10-28
Upgraded from 12.04 to 12.10 today, and my screen rez went from a correct 1440x900 down to 1152x864.

It's on an Intel iMac5,1.

I've been googling and trying things for about 3 hours but have yet to find a solution.

Here is the output of xrandr:

```
$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1152 x 864, maximum 1152 x 864
default connected 1152x864+0+0 0mm x 0mm
   1152x864       60.0* 
   1024x768       61.0  
   800x600        61.0
```

Is there a way I can force it up to 1440x900?  

Any help would be most appreciated!

---

### Post by rencemc on 2012-10-28
Go to System Settings->Display. You can set the resolution.

---

### Post by wilberfan on 2012-10-28
Tried that.  The "1152x864" is the highest rez listed there...

(And because this is LXDE, it's under Preferences > Monitor Settings)

---

### Post by rencemc on 2012-10-28
I wonder if the graphics driver got changed. You can see if there are any listed in "Additional Drivers" and give it a try.

---

### Post by wilberfan on 2012-10-28
> **rencemc said:**
> I wonder if the graphics driver got changed. You can see if there are any listed in "Additional Drivers" and give it a try.

Tried that, too.   The only driver listed is one for wifi...

---

### Post by wilberfan on 2012-10-30
This iMac has an ATI, Radeon X1600 video card in it.  Hmm.  Wonder if nouveau is the best driver in this situation?

According to this page: [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

> For ATI graphics, you will need to install the proprietary graphics drivers. This can be done with the Driver Manger in System > Adminstration > Driver Manager. When installed correctly, reboot, and an additional check is to run
fglrxinfo
The output should tell you that the provider is ATI and not MESA.

When I ran that command, I got this:

```
$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```

No idea what that means...

---

### Post by wilberfan on 2012-11-10
[SOLVED] (Sort of)

I should have known better than to upgrade rather than clean-install.  

I've been playing with Ubuntu since Dapper Donkey (or whatever it was), and I have literally NEVER had an upgrade work out satisfactorily.

This afternoon I did a *clean* install of Lubuntu 12.10 and everything looks awesome.  Full 1440x900 screen rez...  :)

---

