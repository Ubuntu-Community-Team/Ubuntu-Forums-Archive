---
title: "Eject command as toggle"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by noynac on 2008-01-02
I use panel application launchers with the following commands to open and close the trays on my DVD writers:

eject /dev/scd0

eject -t /dev/scd0

Rather than have two panel launchers for each drive, I'd like each drive to have one panel launcher that works as a toggle (open when closed and close when open). Eject has an option, -T, that works as a toggle but it doesn't work with either of my drives (I get an "ioctl: Input/output error)."

Is there any command that would accomplish what I want? Would a script using exit status accomplish what I want.

Thanks for the help.

---

### Post by hardyn on 2008-01-02
wonder if there is a way to query the status of the drive?  then use a condition against that status.

there may be a way use a variable, but then any number of things could upset that variable, like booting with a disk in the tray.

I will keep checking this thread, i would be intested to see how it turns out.

---

### Post by Rhubarb on 2008-01-02
I thought I might use this thread as an excuse to try to learn some simple bash scripting.
My idea is to have a text file in your home folder that contains the current drive status.
```
echo "Closed" > .tray_status.txt
```
Then all your bash script has to do is to querey .tray_status.txt to see if it contains the text "Open" or "Closed".
If it's "Open", then "echo "Closed" > .tray_status.txt" then "eject -t"
If it's "Closed", then "echo "Open" > .tray_status.txt" then "eject"

I'll try and get this script working and will post back soon hopefully.

---

### Post by Rhubarb on 2008-01-02
Okay, I've got a working script now:

```
tray_status=`cat .tray_status.txt`
if [ "$tray_status" == "Closed" ]
then
	eject
	echo "Open" > .tray_status.txt
elif [ "$tray_status" == "Open" ]
then
	eject -t
	echo "Closed" > .tray_status.txt
else
	eject
	echo "Open" > .tray_status.txt
fi
```

This checks to see what ~/.tray_status.txt contains.
If Closed, then it opens the tray and changes  ~/.tray_status.txt to "Open".
If Open, then it closes the tray and changes  ~/.tray_status.txt to "Closed".
If ~/.tray_status.txt does not exist, it assumes the tray is closed, so it Opens the tray and changes ~/.tray_status.txt to "Open".

As I only have one optical drive on my system, I don't need to specify which drive to control with the eject command.  In your case noynac, when ever you see:
"eject" replace with "eject /dev/scd0"
"eject -t" replace with "eject -t /dev/scd0"
Also, if you have more than one optical drive you wish to control with your script, you will need to have another variable stored in a text file containing the status of the other optical drive (and obviously you must edit this script to do so aswell).

---

### Post by Dr Small on 2008-01-02
Magnifico! That looks awesome :)

---

### Post by marx2k on 2008-01-02
From the manpage for 'eject':

```

       -t   With  this option the drive is given a CD-ROM tray close command. Not all devices support this command.

       -T   With this option the drive is given a CD-ROM tray close command if it&#8217;s opened, and a  CD-ROM  tray eject  command  if it&#8217;s closed. Not all devices support this command, because it uses the above CD-ROM tray close command.


```

---

### Post by noynac on 2008-01-02
Rhubarb,

Many thanks. I created one script file for each drive with each script creating a separate text file. This only took a few minutes and works great. 

Thanks again.

Modred

---

### Post by noynac on 2008-01-02
> **marx2k said:**
> From the manpage for 'eject':

```

       -t   With  this option the drive is given a CD-ROM tray close command. Not all devices support this command.

       -T   With this option the drive is given a CD-ROM tray close command if it&#8217;s opened, and a  CD-ROM  tray eject  command  if it&#8217;s closed. Not all devices support this command, because it uses the above CD-ROM tray close command.

```

I tried the -T option, but it wouldn't work with either of my drives. Apparently others are experiencing the same problem, as there is a bug report on this at:

[https://bugs.launchpad.net/ubuntu/+source/eject/+bug/91873](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/91873)

---

