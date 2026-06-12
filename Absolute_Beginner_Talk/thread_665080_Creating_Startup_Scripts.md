---
title: "Creating Startup Scripts???"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Bascote on 2008-01-11
Hey guys,

I was just wondering if this would work..

I want to create a script that starts up and loads before drivers or X loads because apparently to unlock pixel piping with Nvclock, you must unload the nvidia driver and get out of X.

The way I was planning to do it (please correct me if this process is completely wrong) is this:

Open the text editor and type in..

nvclock -n 380
nvclock -m 770
nvclock -v 111111

Once I have this file created I will save it and place it in **/etc/xdg/autostart**

Will this run this script the way I want it to (or at all?) and specifically before X and the nvidia driver loads?

The reason I am doing this is everytime I overclock using nvidia settings or nvclock the settings go back to normal and also to unlock vertex units and pipelines I have to do it this specific way (before X and drivers load)

Thanks in advance, please assist! :KS

---

### Post by PeterJS on 2008-01-11
The most common way is to to put stuff in /etc/rc.local, but that's not going to work in this case as you need to have it run before the nvidia drivers are loaded. So you're going to want to integrate your script in to the boot up process rather than have it run as an after thought with rc.local. All the scripts that control boot up are located in /etc/init.d/ and then symlinked in to the rc folder that describes where in the boot order they are supposed to run. /etc/init.d is kinda picky about the format of the file names used in the start up scripts, it wants all lowercase letters, no spaces, and no .sh on the end. The name of your script will be the name of the service used when you integrate it in to the boot process.

So I've looked at boot up process for runlevel 2 (the default) in /etc/rc2.d the only thing that jumps out at me and says "Hey I load the nvidia drivers" is the nvidia-kernel scrip that runs after gmd starts, so I don't think that's it. I think the nvidia module is loaded by the module auto loader in initramfs, but I haven't actually found it yet, so I can't say for sure(**EDIT:** So I just found it the lrm-video script that loads it, it is done during the initramfs module load). Anyway the driver absolutely has to be loaded by the time gdm starts in slot 13, so where ever you put your script it has to be before that, and I'd suggest leaving a fair bit of padding just to be on the safe side. I would also suggest unloading the module at the top of your script doing what needs to be done, and then reloading the module.  And wrap the whole thing in an if block to test if the first parameter is "start" so it only runs on start up and not shutdown, it probably wouldn't hurt the system if it also ran on shutdown, but why risk it. Technically speaking to stick to the debian sysv standards your script needs to support, start, stop, restart, and status but that's a bit much for the task at hand.

To link the script in to the boot process:
```

sudo update-rc.d *service_name* defaults 09

```

To unload the module
```

modprobe -r nvidia

```
There's no need for sudo here as all boot scripts run as root
Then to reload it:
```

modprobe nvidia

```

---

### Post by Bascote on 2008-01-12
Now I just need to learn scripting lol..

Well I figured out how to do an overclock/unlock of pipelines while booted up using:

Control+Alt+F1
sudo /etc/init.d/gdm stop
sudo rmmod nvidia
sudo nvclock -P 1111 -V 111111 -f
sudo modprobe nvidia
sudo gdm

and then once I get back in I overclock but it only lasts for the session.

If anything I'd like a script to keep my overclocked settings when I boot up.

---

### Post by PeterJS on 2008-01-12
if that's a working set of commands the script would be:
```

#!/bin/sh
rmmod nvidia
nvclock -P 1111 -V 111111 -f
modprobe nvidia

```
Like I said above, sudo isn't needed because the boot scripts are already running as root.

---

### Post by Bascote on 2008-01-12
Sorry im a little slow at this, is there anyway you could give me more instructions after I create that script?

Like where it goes, what command to activate it (from what ive been reading theres some kind of command and place to put the script to make sure it works on bootup)

Think of this as explaining it to a complete scripting newbie.

Thanks!

---

### Post by PeterJS on 2008-01-12
```

#/bin/sh
if [ "$1" = "start" ]
then
  rmmod nvidia
  nvclock -P 1111 -V 111111 -f
  modprobe nvidia
fi

```
The script contents themselves.
```

sudo gedit /etc/init.d/nv.overclock

```
And stick the script I purposed above in there and save it.
```

sudo chmod +x /etc/init.d/nv.overclock

```
Tell the security and permission system that the script is allowed to execute.
```

sudo update-rc.d nv.overclock defaults 09

```
And finally insert it in to the boot process.

---

### Post by Bascote on 2008-01-12
Beautiful this is what I've been looking for I believe, my script was very basic I thought you could just type the first line with the # symbol and then the commands but obviously it didn't work, I'll give this a shot thanks!

---

### Post by Bascote on 2008-01-12
Seems that it hasn't worked again, I followed the instructions precisely but when I booted up and typed in:

```
nvclock -i
```

it returned:

-
Card:           nVidia Geforce 6800LE
Architecture:   NV40 A1
PCI id:         0x42
GPU clock:      299.250 MHz
Bustype:        AGP

-- Pipeline info --
Pixel units: 2x4 (0011b)
Vertex units: 4x1 (010111b)
HW masked units: pixel 1100b vertex 101000b
SW masked units: pixel 1100b vertex 101000b

-- Memory info --
Amount:         128 MB
Type:           256 bit DDR
Clock:          702.000 MHz

-- AGP info --
Status:         Enabled
Rate:           8X
AGP rates:      4X 8X 
Fast Writes:    Disabled
SBA:            Enabled

-- Sensor info --
Sensor: Maxim MAX6659
Board temperature: 33C
GPU temperature: 49C
Fanspeed: 53.0%

-- VideoBios information --
Version: 05.40.02.57.68
Signon message: nv40 p212 sku5 VGA BIOS
Performance level 0: gpu 300MHz/memory 700MHz/1.10V/53%
VID mask: 3
Voltage level 0: 1.10V, VID: 0
Voltage level 1: 1.40V, VID: 2
Voltage level 2: 0.00V, VID: 0


Another setting I had added to the script was to set the fanspeed at 100 but that didn't change either.

---

### Post by PeterJS on 2008-01-12
Well I'm officially out of information. I've never tried to use the nvidia overclocking tools. My only suggestion would be to add:
```

echo "The script ran" > /home/username/scripttest

```
To see if the script is actually running.

---

### Post by Bascote on 2008-01-12
I really appreciate your help Peter, thank you =)

Im going to try a couple things and add that line in right now.:KS

---

### Post by Bascote on 2008-01-12
No luck again,

I added the line to see if the script was running but no message is popping up, would it be logged somewhere?

---

### Post by PeterJS on 2008-01-12
Well that's at least a good sign, that means it's not working because it's not running, not because there is something wrong with it. It should have been logged in your home folder under file name scripttest (you did change the file path to point to a real place, right?). Let's see if the script is actually where it should be:
```

ls -l /etc/rc2.d/ | grep S09

```
if that returns nothing then the script isn't loaded in to the boot process. And you'll need to re-run the update-rc.d step.

---

### Post by Bascote on 2008-01-12
Hey again,

:lolflag: I forgot to add my username into the path. I'll do that now.

As for

```
ls -l /etc/rc2.d/ | grep S09
```

It mentions nv.overclock script and my old script that I tried named nvid (the file is deleted but its still showing up after using this command, **could that be the problem?**

Also would you happen to know how I could edit scripts in init.d and SAVE them without logging into root?
 
The only way I found is to save it so somewhere else then use the sudo mv command to move it back to init.d

---

### Post by PeterJS on 2008-01-12
The old script shouldn't hurt anything, but might as well be safe:
```

sudo unlink /etc/rc2.d/nvid

```
To edit the script in place
```

sudo gedit /etc/init.d/nv.overclock

```

---

### Post by Bascote on 2008-01-12
I usually use

```
sudo gedit /etc/init.d/filename
```

but after editing it I do not have permissions to save it without logging into root and saving it to a permissible folder and moving it with sudo mv.

The script IS running apparently, the file was created in my home/username folder that says it ran.

=/ Maybe I need to look into this more.

**EDIT** Scratch that, apparently i was using just gedit and no sudo gedit, thanks!

---

### Post by PeterJS on 2008-01-12
That's weird there should be no practival difference between giving your self root with sudo and actually logging in to the root accound. I was kinda hoping it was something easier like the script just wasn't running, good luck. I'll be around to answer questions, but I'm not sure how much more insight I can offer.

---

### Post by Bascote on 2008-01-12
Ok I think I may have found a fix but perhaps someone else understands it better than I do..

At this site:

[http://ubuntuforums.org/archive/index.php/t-346483.html](http://ubuntuforums.org/archive/index.php/t-346483.html)

there was a similar problem to run a different script before x loads.

My nvclock commands work if I press control+alt+f1
```

sudo /etc/init.d/gdm stop
sudo rmmod nvidia
sudo nvclock -P 1101 -V 111111 -F 100 -f
sudo modprobe nvidia
sudo gdm (to start it back up)

```

So I think the problem is that although the script is running, its not running at the correct time in the bootup process (maybe too late?)

In that post one guy mentioned fixing his problem by:

> I have finally found the fix. I call my code from the /etc/init.d/gdm file. I placed it in as the first line of code and it works. Thanks for everyone help.

I dont understand exactly how to do this but does anyone think its related and, if so, what would i have to do?

Thanks in advance.

---

### Post by PeterJS on 2008-01-12
If the GDM hack works then the problem isn't that your script is running too late, but rather that it's running to eary. It's a rather hackish solution, but if it works, it pretty clever.

Here's a cleaner version of the final result from that thread:
[http://ubuntuforums.org/showpost.php?p=2068488&postcount=19](http://ubuntuforums.org/showpost.php?p=2068488&postcount=19)

So it looks like you want to pull your script from the boot process (directly)
```

sudo update-rc.d nv.overclock remove

```

And insert it at the top of the gdm script as shown in red in the linked post.

---

### Post by Bascote on 2008-01-12
So after the # in the red part I would be in the whole script including all the code to unlock the pixel pipings?

Also when removing the old script from the process it gives me a messages saying it exists and use -f to force and i use -f but it gives the same message, does that mean its working?

```
update-rc.d: /etc/init.d/nv.overclock exists during rc.d purge (use -f to force)

```

**EDIT** I had to move the file first, so ignore the part about removing it from rc.d, its all done.

---

### Post by Bascote on 2008-01-12
Hmm what im trying so far isnt working,

Should I ignore all the other steps in the other post and just focus on adding it into the gdm file?a cleaner version of the final result from that thread:

---

### Post by PeterJS on 2008-01-12
Steps 1 and 2 are specific to that script. Step three is the right idea, it's just using the content of their script instead of ours. Aside from using more on topic file names the steps 4,5, and 6 can be used verbatium.

---

### Post by Bascote on 2008-01-12
I did 4,5,6 verbatim. After I did 4,5 I simply copied the red text and inserted it as is, no luck. Is that what I was suppose to do?

---

### Post by PeterJS on 2008-01-12
If you read the red text you'll see that is says something to the effect of "and now we run our script" and then has the script name. You're going to want to use the name and path of your script instead of theres.

---

### Post by Bascote on 2008-01-12
In the red they have this

```
# Call the xorg.conf_switcher.sh command to copy the correct xorg.conf file to /etc/X11
 /usr/local/bin/xorg.conf_switcher.sh
```

I kept the space between  "/etc/X11 and /usr...."

Basically I've put my script in the same location they have which is /usr/local/bin/

and I've named my script nvclocktime so after I pasted what was in the red it looked like..

```

#! /bin/sh
#
# Originally based on:
# Version:	@(#)skeleton  1.8  03-Mar-1998  miquels@cistron.nl
#
# Modified for gdm, Steve Haslam <steve@arise.dmeon.co.uk> 14mar99
# modified to remove --exec, as it does not work on upgrades. 18jan2000
# modified to use --name, to detect stale PID files 18mar2000
# sleep until gdm dies, then restart it 16jul2000
# get along with other display managers (Branden Robinson, Ryan Murray) 05sep2001
[b]# Call the nvclocktime command to copy the correct xorg.conf file to /etc/X11 
/usr/local/bin/nvclocktime[/b]



set -e

# To start gdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/gdm
PIDFILE=/var/run/gdm.pid
UPGRADEFILE=/var/run/gdm.upgrade
```

Still whenever I check it seems that not even my command to increase the fan speed is working, even though that doesnt matter whether you run it with X and nvidia drivers loaded or not.

But the script must be running if I get my scripttest file generated in home folder? I delete it and it still generates after a restart.

---

### Post by PeterJS on 2008-01-12
Yeah, the script is running, could you post the script? As I wrote it is expecting to be run as an init script with a function (start, stop, etc) passed to, but if it's being run that way the command isn't being passed to in and it may need to be modified to run that way.

---

### Post by Bascote on 2008-01-12
```

#/bin/sh
if [ "$1" = "start" ]
then
 
  rmmod nvidia
  nvclock -P 1101 -V 111111 -F 100 -f
  modprobe nvidia
  

echo "The script ran" > /home/karim/scripttest

fi

```

Thats the nvclocktime script

---

### Post by PeterJS on 2008-01-12
Darn so much for that theory, I was hoping that the echo was outside of the if, and that is why that was working, but not the overclocking bit.

---

### Post by Bascote on 2008-01-12
Seems like everywhere I go I find incomplete forums about this topic =/

Oh well, its something i just wanted to know how to do and its ok because along the way I got use to using all these different commands with linux and im feeling closer to it. Unfortunately when the next new game im looking to play comes out I might have to go windows or dual boot.

But God willing if I can figure out my OTHER problems on using ipass on my laptop with ubuntu i would LOVE to have ubuntu there instead.

---

