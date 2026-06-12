---
title: "Error: Can't change hdparm settings"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Darko Beta on 2007-02-10
My Ubuntu is really slow.  I'm running a P4 1.8ghz with 1gb of ram, and XP is very snappy on this PC.  I am trying to figure out how to speed up Ubuntu, and it seems there are two ways to improve performance: optimize disk performance and optimize video performance.  First, I am trying optimize disk performance by following this guide:

[http://opensource.apress.com/article/65/command-line-gems-hdparm](http://opensource.apress.com/article/65/command-line-gems-hdparm)

My disk settings could use some changes:

```
/dev/hdb2:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 228363975, start = 78156225
```

However, when I try to adjust any of the settings, I get the following error:

```

/dev/hdb2:
 HDIO_GET_IDENTITY failed: Invalid argument
```

Does anyone have suggestions for how to get around this error and change these settings?  I tried editing my hdparm.conf file and rebooting but the settings remained, presumably because the same error occurred at boot...

---

### Post by Darko Beta on 2007-02-10
Anyone know how to fix or work around this error?

---

### Post by nickoli_02 on 2007-02-10
That's odd, my system is an Intel Centrino 1.73GHz, 512MB RAM, 100GB hard drive, ATI Mobility X700, and Ubuntu is easily twice as responsive as Windows, most noticable at boot time. Sorry I can't help you with your error but maybe Ubuntu is slow to respond because a process is eating up system resources? At the terminal try typing "top" to get a list of running processes and to see what is using what. Worth a shot

---

### Post by %hMa@?b&lt;C on 2007-02-10
what do you have for your video drivers?

---

### Post by Darko Beta on 2007-02-11
Thanks for taking a look.  Nickoli: this is why I think it's strange because in reading the forum it sounds like my system should be running a lot faster.  If anyone knows how I could change the hdparm settings let me know!  I'm going to start a new thread about the video drivers.

---

### Post by rsambuca on 2007-02-11
What is the command you are using when you get that error message?

---

### Post by Darko Beta on 2007-02-11
Hmm.  I'm getting a slightly different error now.  Here is what I've just tried.  What is the invalid argument that it's referring to?

```
sudo hdparm -c3 /dev/hdb2
```

which reveals:

```
/dev/hdb2:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)
```

and then I tried:
```

sudo hdparm -u1 /dev/hdb2
```

and got:

```
/dev/hdb2:
 setting unmaskirq to 1 (on)
 HDIO_SET_UNMASKINTR failed: Invalid argument
 unmaskirq    =  0 (off)
```

---

### Post by rsambuca on 2007-02-11
Take out the "2" at the end of your command.  ie use hdb, not hdb2.  I believe you have to make the settings for the drive, not a partition.

---

### Post by Darko Beta on 2007-02-11
Hey, thanks rsambuca!  You were right.  I am now able to edit the settings for my drive.

---

### Post by rsambuca on 2007-02-11
Good stuff!!!

If you want to check your current settings, as well as see the capabilities of your drive, try this command```
sudo hdparm -iI /dev/hdb
```

---

### Post by Darko Beta on 2007-02-11
Very cool.  Thanks again, I learned from this.

---

