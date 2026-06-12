---
title: "How do I know I have the latest/best ATI drivers?"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by billingsworld on 2007-01-26
I have a Radeon 9600SE board by Micron, I have installed some device managers to see what driver is installed.

HAL Device Manager shows:

 RV350 AQ (Radeon 9600)


Sysinfo shows:

echnologies Inc RV350 AQ [Radeon 9600] 

I have a good resolution at a decent refresh rate.  Is there a command to determine your fps?

ATI has a site for Radeon drivers at:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Any ideas?  I am not that interested in breaking my system.. yet.

---

### Post by CowzRule on 2007-01-26
In a terminal type ```
glxgears
```That will show you some fps numbers, but don't take them to seriously. They're not a true measure of performance. There really is no "benchmark" software for linux like there is for windows. (someone correct me if I'm wrong)

For more info on installing the drivers from the ati.amd website see:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_Driver_Manually")

---

### Post by ardchoille42 on 2007-01-26
shouldn't that be

```

glxgears -printfps

```

---

