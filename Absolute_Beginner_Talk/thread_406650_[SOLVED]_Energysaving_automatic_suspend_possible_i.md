---
title: "[SOLVED] Energysaving automatic suspend possible in Xubuntu?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by tommie74 on 2007-04-11
I have found a screensaver in *Applications -> Settings -> Settingsmanager -> Screensaver* but that can only inactivate the screen after a certain time of no computer input. What I would like to have is an energy saver which sets my computer in suspend after a certain time of no input. Xubuntu is so swift in reanimating after a suspend that not suspending my computer while not using it seems completely unnecessary. Anybody has a clue about how this can be done in Xubuntu? Please try to be as clear as possible for I am in my first week of Linux experience.
Thx for looking,
Thomas de Graaff.

---

### Post by john.nicholls on 2007-04-12
In the screensaver settings, click on the Advanced tab and under Display Power Management you will find the Suspend settings.

---

### Post by tommie74 on 2007-04-12
Hello John,
I've set those suspend settings in the advanced tab of the screensaversettings to 2 minutes on my computer to test it, but this only shuts down, blank, my screen. When I push Applications -> Quit -> Suspend, my computer seems to shut down almost totally, my harddisk stops spinning, and I have to push the power button to restart it. It looks as if almost everything that can be shut down is shut down. When it restarts I have to login on the Xubuntu Login screen. While on the other hand the effect of the screensaver suspend setting is that my computerscreen lights up whenever I move the mouse or touch a button, and then I can get back to work without needing to login. It seems that the suspend in the advanced screensaver settings is a different suspend than the  Applications -> Quit -> Suspend one. But maybe it is my computersetting or something that make this difference, so if the screensaver suspend on your computer shuts down your harddisk etc. let me know, it migh give some insight.
Anyhow John, thx for helping me,
Thomas de Graaff.

---

### Post by john.nicholls on 2007-04-12
The screensaver suspend on my computer doesn't appear to shut down the hard disk. If the same thing is happening on yours maybe that is why the computer comes out of suspense so quickly - as mine does.
John

---

### Post by tommie74 on 2007-04-13
Hello John,
well, it does come out of the screensaver suspense quickly like your computer. But it also come to life quickly from the total suspense when the harddisk does shut down, of course it takes a little extrra time but compared to a total restart of the system it is very swift.
Grts,
Thomas.

---

### Post by tommie74 on 2008-02-28
I found the following wiki to get energysaving for Xubuntu at:

[http://www.thinkwiki.org/wiki/Installing_Debian_Lenny_on_a_ThinkPad_T60#automated_sleep](http://www.thinkwiki.org/wiki/Installing_Debian_Lenny_on_a_ThinkPad_T60#automated_sleep)
 
> automated sleep

You could also set it up so that your laptop goes to sleep when you close the lid. I however prefer to have my laptop remain awake when the lid is closed so that it can continue background tasks such as ripping a cd, downloading a file, compiling a kernel, playing music, etc. I do however want to have some system of going to sleep during inactivity. For this I use the sleepd package which automatically puts the laptop to sleep after a period of inactivity. It does however requires some configuration to make it actually do this.

First of all, if you haven't already installed it, do so

aptitude install sleepd

and for the popup window install zenity

aptitude install zenity

Now edit the configuration file /etc/default/sleepd. Set PARAMS to the arguments you want to give the sleepd daemon as started by init. You can take a look at the sleepd man page to get an idea of what you might want to put here. As an example, you might have

PARAMS="-u 180 -U 1800 -s /etc/acpi/sleep.sh -i 1 -i 12 -i 23"

This tells sleepd to sleep after three minutes of inactivity while on battery(-u 180) and after half an hour of inactivity while on ac (-U 1800). I have defined "activity" as signals on irqs 1(keyboard), 12(mouse), and 23(usb mouse) (-i 1 -i 12 -i 23). 1 and 12 will be autodetected, but 23 may not be. You can see what uses the various interrupts by running the command cat /proc/interupts.You can also use the xosview utility to discover when the various IRQ's are used. Finally sleepd itself doesn't actually know how to put the computer to sleep, so you have to supply it with the command to do so (-s /etc/acpi/sleep.sh). You could really put anything at all here.

You'll note however, that the above is a rather limited definition of "inactivity". Unfortunately, it's the best sleepd has to offer. Alas, none of the above mentioned background tasks that I want my computer to continue doing can be reliably mapped to the use of a particular IRQ. The next best thing then is to have our sleep command be a script that before putting the computer to sleep checks for a wider range of activity before actually going to sleep and aborts the sleep process if such activity is detected. This will reset the sleepd timer so that it must wait for an other interval of human inactivity before running the sleep/check script again.

There are four checks that I want to do before going to sleep:

   1. CPU activity
   2. Disk activity
   3. Network activity
   4. Is sound playing? 

The first three can be checked using the sar utility included in the sysstat package, while the latter can be checked using the rec utility included in the sox package. If you haven't already, install those packages. Sox is additionally going to need alsa support, so you could install that package, or just go ahead an install off of sox since its a handy program to have the full functionality of.

aptitude install sysstat sox sox-fmt-all

The following script autosleep.sh is intended to be called by sleepd after user inactivity to check for the background inactivity described above. If there is inactivity in these four fronts, it calls the sleep.sh script and puts the computer to sleep.

```
#!/bin/bash
# autosleep.sh
# Checks if the computer is inactive before going to sleep. Aborts if it looks like 
# there's some action.
#

# Thresholds - these may depend on what you do with your computer and what 
# you want it to stay awake for.
CPUTHRESH=5        # in percent 
DISKTHRESH=500     # in blocks/sec (the sar manpage says blocks are 512 bytes in normal cases) 
NETTHRESH=10       # in kB/s
SNDTHRESH=200      # in ???? rms 
# (no sound playing is ~25 while playing mp3 w/ pcm+master turned all the way to zero is ~250)

# Sample times (in seconds) - again needs may vary
CPUTIME=1   
DISTTIME=2  
NETTIME=2 
SNDTIME=2 


# Check CPU usage defined as non-idle time.
CPU=`sar $CPUTIME 1 | awk '/Average/ { printf "%d\n",100-$8}'`
echo "CPU = $CPU%"
if [ $CPUTHRESH -lt $CPU ];then
    echo CPU is working, not sleeping
    exit;
fi

# Check disk usage (read + write)
DISK=`sar -b $DISKTIME 1 | awk '/Average:/ { printf "%d",$5 + $6 }'`
echo "DISK = $DISK"
if [ $DISKTHRESH -lt $DISK ];then
    echo Disk is working, not sleeping
    exit;
fi

# Check net usage (exclude wifi0 which appears to have activity all the time for some weird reason)
NET=`sar -n DEV $NETTIME 1 | awk '/Average:/ && $2 !~ /(IFACE|wifi0)/ { SUM += $5 + $6 } END { printf ("%d\n",SUM)}'`
echo "NETWORK = $NET"
if [ $NETTHRESH -lt $NET ]; then
    echo Network is in use, not sleeping
    exit;
fi

# Set the mixer to some controlled values and set it to record the mixed sound output
# This unfortunately is going to be sound-chip specific.
alsactl -f /var/tmp/sound.state store
amixer sset Capture 20% cap
amixer sset Digital 20%
amixer sset Mix cap
# Record to null and use RMS amplitude in resulting statistics with a convenience 
# factor to make it integer
SND=`rec -n stat trim 0 $SNDTIME 2>&1 | sed -n 's/^RMS[ ]*amplitude:[ ]*/1000000 * /gp' | bc | cut -d. -f 1`
# Restore previous mixer state
alsactl -f /var/tmp/sound.state restore
echo "SOUND = $SND"
if [ $SNDTHRESH -lt $SND ];then
    echo Sound is playing, not sleeping
    exit;
fi

# check for remote login
REMOTELOGIN=`last | head | grep "pts/.*still logged in"`
if [ -n "$REMOTELOGIN" ];then
    echo Remote login active:
    echo $REMOTELOGIN
    echo Not sleeping
    exit;
fi

# Timer 10 secs with popup window allows cancel
(for ((i=0;i<100;i+=1)) ; do echo $i ; sleep 0.1; done) | zenity --progress --auto-close --title='' --text='This computer is going to standby in 10 sec.'

test=$?

if [ $test -eq "1" ]; then
  exit;
fi  

# Go into standby

. /etc/acpi/sleep.sh
```


Now, a little abstract:
1) put this script in /etc/acpi/autosleep.sh
```
sudo nano /etc/acpi/autosleep.sh
```
copy and paste the code using the right mouse button then save and exit nano

2) change permissions so it can be executed
```
sudo chmod ugo+x /etc/acpi/autosleep.sh
```
3)and then add the following line to /etc/rc.local:
```
sleepd -U 900 -u 180 -s /etc/acpi/autosleep.sh -i 1 -i 11 -i 12
``` Before the exit command!
Of course you have to adapt the times (900,180) and the irq's (1,11,12) to your own situation. Irq's of the keyboard, touchpad and mouse can be found using xosview.
4) restart your computer

---

### Post by hemish on 2008-03-22
I like the autosleep script Tommie.

But I would love if it could be tweaked for home server use too. I have a laptop I use as home server and only ssh to for terminal interaction so keyboard and mouse interrupts on the machine itself is non active. 

I have used your autosleep script now, which works fine while the machine is i/o or cpu loaded (e.g. streaming music to external player), but it's hard to detect simple ssh command line activity only (e.g. when only editing files and not streaming/transfering anything) by looking at network bandwidth or CPU load alone.

Would it be possible to detect ssh activity over longer periods? E.g. if any ssh activity has taken place the last 30 mins, don't sleep? That would be perfect.

Also having a look at ethernet bandwidth over longer time could be nice, so just a single spike going over the threshold within an x minute time window would exclude a sleep.

---

### Post by tommie74 on 2008-03-22
Hello Hemish,
I didn't write the scripts myself, I used a wiki. You can see it in the post. Maybe you better try there if the maker can help.

---

### Post by shaunbarlow on 2008-03-28
Hemish,
Did you find a way to use sleepd so it doesn't sleep if there is an ssh connection?
Anyone else?
Cheers,
Shaun

---

### Post by tommie74 on 2008-03-29
Found this script, maybe it can be adapted:
```
#!/bin/bash
#
# MythShutdownCheck
#
# checks to see if any other user is
# logged in before idle shutdown
#
# returns "1" if yes, stopping shutdown
# returns "0" if ok to shutdown
#

if last | head | grep -q "pts/.*still logged in"   # check for active *remote* login?

then
   exit 1

else
   exit 0
fi
```

---

### Post by hemish on 2008-03-29
Great last script.

I have added it like this to my current autosleep.sh script

```

REMOTELOGIN=`last | head | grep "pts/.*still logged in"`
if [ -n "$REMOTELOGIN" ];then
    echo Remote login active:
    echo $REMOTELOGIN
    echo Not sleeping
    exit;
fi

```

---

### Post by tommie74 on 2008-04-24
> **hemish said:**
> Great last script.

I have added it like this to my current autosleep.sh script

```

REMOTELOGIN=`last | head | grep "pts/.*still logged in"`
if [ -n "$REMOTELOGIN" ];then
    echo Remote login active:
    echo $REMOTELOGIN
    echo Not sleeping
    exit;
fi

```

Thx Hemish, I have added it with the rest of the script in the post. Also I have added a little popup window that makes it possible to cancel.:

# Timer 10 secs
(for ((i=0;i<100;i+=1)) ; do echo $i ; sleep 0.1; done) | zenity --progress --auto-close --title='' --text='This computer is going to standby in 10 sec.'

test=$?

if [ $test -eq "1" ]; then
  exit;
fi  

# Go into standby (insert this just before the standby command)

---

