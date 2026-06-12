---
title: "What's a good startup script for this?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-09-12
I was told over on the Nvidia linux forums that in order to have my overclock be applied at startup (instead of having to manually reset it all the time), I have to add this line to a file that is run at bootup:

> 
# nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=<GPU>,<MEM> -a GPU3DClockFreqs=<GPU>,<MEM>


What's a good startup file I can add this to?

---

### Post by davmac on 2006-09-12
I don't know if it's the "right" place to do it, but I'd put something like this in /etc/init.d/bootmisc.sh

Dave Mac

---

### Post by bswilson on 2006-09-12
Depends on exactly where in the boot process this must take place; do you know?  You could write a script and place it in **/etc/init.d** which will be read by the **init** process.  Or, if it can happen later in the boot sequence, you could write a simpler script in **/etc/cron.hourly** or something like that.

If you'll provide some more details, I think I can help you!

---

### Post by fatsheep on 2006-09-12
> **bswilson said:**
> Depends on exactly where in the boot process this must take place; do you know?  You could write a script and place it in **/etc/init.d** which will be read by the **init** process.  Or, if it can happen later in the boot sequence, you could write a simpler script in **/etc/cron.hourly** or something like that.

If you'll provide some more details, I think I can help you!

Here's what I know:

[http://www.nvnews.net/vbulletin/showthread.php?p=986059](http://www.nvnews.net/vbulletin/showthread.php?p=986059)

---

### Post by bswilson on 2006-09-13
OK, that we can work with!

On Ubuntu, there are 2 places you could put this script.  The first is the file **/etc/bash.bashrc**, which is executed at startup for all users.  In your home directory, you have a file called **.bashrc** which is executed for only you when you log in.  So, you can edit either script and place this line in there.  I recommend backing the script(s) up first, and adding some comments to remind yourself what you did.  For example:

1. Back up your bash startup scripts:
```
$ sudo cp /etc/bash.bashrc /etc/bash.bashrc.BAK
$ sudo cp ~/.bashrc ~/.bashrc.BAK
```

2. Edit either /etc/bash.bashrc or ~/.bashrc and add the following:
```
# Added the following nVidia graphics card overclocking settings to system startup
nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=<GPU>,<MEM> -a GPU3DClockFreqs=<GPU>,<MEM>
```

Good luck!

---

### Post by fatsheep on 2006-09-14
Thanks for the info.  I backed up my bash scripts and decided to use the one in my home directory.  First I tried adding this line to the end of it:

> nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=<GPU>,<MEM> -a GPU3DClockFreqs=<GPU>,<MEM>

But then it dawned on me that I should probably insert my settings. #-o  So I tried this:

> nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=300,1000 -a GPU3DClockFreqs=550,1100

Unfortunately neither worked.  When I restart, overclocking is turned off and frequencies are at default.

---

### Post by fatsheep on 2006-09-15
Sorry for the bump but I just realized this.  Everytime I open a terminal now I get this:


>   Attribute 'GPUOverclockingState' (fatsheep:0.0) assigned value 1.

  Attribute 'GPU2DClockFreqs' (fatsheep:0.0) assigned value 300,1000.

  Attribute 'GPU3DClockFreqs' (fatsheep:0.0) assigned value 550,1100.

And this does really work. :)  Any way I could implement this into the script?

---

### Post by bswilson on 2006-09-18
Sounds like you want to redirect those informational messages to a log file of some kind.  Shouldn't be a problem; just add this to the end of the line:

```
>2&1
```

Which means to direct the STDOUT and errors to a logfile like syslog.

---

### Post by fatsheep on 2006-09-19
Sorry I forgot to add that I had found a work around for this problem.  Instructions are in Section 3 of this topic:

[http://www.ubuntuforums.org/showthread.php?t=254397](http://www.ubuntuforums.org/showthread.php?t=254397)

---

