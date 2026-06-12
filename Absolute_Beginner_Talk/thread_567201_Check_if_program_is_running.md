---
title: "Check if program is running"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Hunterjelly on 2007-10-04
Basically, I need to check is fah6 is running, and if it's not then launch it. I have it set to auto-launch at startup (via Sessions). But it appears to randomly close it's self for whatever reason. Since it runs in the background and there is no window for me to see, when it closes I have no idea it's not running; except from when I manually check myself about twice a day.

I used some program I found to make Cron thingy's, which kinda worked but after 5m I checked the running processes and... 5 fah6's were running, just gobbling up more and more memory each min. (as it ran every min.)

So I'll re-state: I need a way to launch fah6 if it's not already running if it's not running then nothing needs to be done. I'd like a way for it to check at least every 5m, but 1m is prefered.

Thanks :)

---

### Post by kevdog on 2007-10-04
Write a cron script that runs every x minutes.  This would most likely need to be a system wide script since it requires root priviledges to run.  The script would make a call to ps -eF and then grep the output for the name of the program you are looking for.  If its found, do nothing, if its not found then start the program.

---

### Post by wpshooter on 2007-10-04
> **Hunterjelly said:**
> Basically, I need to check is fah6 is running, and if it's not then launch it. I have it set to auto-launch at startup (via Sessions). But it appears to randomly close it's self for whatever reason. Since it runs in the background and there is no window for me to see, when it closes I have no idea it's not running; except from when I manually check myself about twice a day.

I used some program I found to make Cron thingy's, which kinda worked but after 5m I checked the running processes and... 5 fah6's were running, just gobbling up more and more memory each min. (as it ran every min.)

So I'll re-state: I need a way to launch fah6 if it's not already running if it's not running then nothing needs to be done. I'd like a way for it to check at least every 5m, but 1m is prefered.

Thanks :)

If this is folding-at-home that you are talking about, my first concern would be why it is closing on it's own.  I think I would go to the folding-at-home forum and pose your question there as to why this closing was taking place.  Perhaps you just need to get rid of everything regarding the FAH, then restart the computer and then download the finstall script from the proper site and rerun the install from scratch.  Are you making sure that you are NOT logged on as ADMIN (or have recently used SUDO command) when you are running FINSTALL script ?

Good luck.

---

### Post by Hunterjelly on 2007-10-04
Yeah... It obviously should not be stopping on it own - I know that. I'm not all that concerned about it though, I just need it to re-launch after it goes down; which it does randomly. I've never really documented how long it stays up before going down, but I had it going 4 days straight this week. I rebooted my computer, upgraded to the SMP client and ran it. A few hours after that I checked the processes and noticed it wasn't there (yes, I am positive it was running).

Now Kevdog.... I really don't know how to do that, only way I can make Cron work is through a program called "GNOME Schedule 1.0.0".

If you could maybe give me some syntax examples, I'd give it a shot and see how it works.

---

### Post by Hunterjelly on 2007-10-06
Shameless bump. (This always happens, nobody answers me!)

---

### Post by nick_h on 2007-10-06
Perhaps something along the lines of:
```

#!/bin/bash
CNAME=`ps -eo comm | grep fah6`
NOW=`date`
if [ "$CNAME" = "" ]
then
	echo "fah6 started -" $NOW >> fah6.log
	/usr/bin/fah6
fi

```
You will have to check the process name, the path to the bin, if and where you want a log file etc...

---

### Post by Hunterjelly on 2007-10-13
One problem.. I have no idea where I'm putting that :confused:

---

### Post by steve.horsley on 2007-10-13
A one-liner in the cron job like this might do the trick:
```
ps -ef | grep fah6 || fah6
```
This lists all running processses, loks for fah6 and if one is not found, it then runs fah6. You might need to give the full path to that last fah6.

---

### Post by nick_h on 2007-10-13
Create a file, for example fah6_restart.sh, with the code in it and place it in /usr/local/bin
Make sure it is executable with:
```
cd /usr/local/bin
chmod a+x fah6_restart.sh
```
Then you can run this script from the crontab.

---

### Post by nick_h on 2007-10-13
> A one-liner in the cron job like this might do the trick
```
ps -ef | grep fah6
```
will find the process *grep fah6* even if fah6 is not running, but yes a one-liner is possible.

---

### Post by steve.horsley on 2007-10-13
Doh! You're right.

---

### Post by mysurface on 2007-10-13
you can use pgrep

```
pgrep fah6
```

---

