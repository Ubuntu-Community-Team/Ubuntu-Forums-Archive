---
title: "Automatic shutdown after idle 1 hour"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by BennyS on 2007-08-21
Hello all,

I am looking a way to automatic shutdown after idle 1 hour.

Would you guys ubuntu gurus tell me how to do it ?

thanks you
B.

---

### Post by kerry_s on 2007-08-21
well sounds like a cron job could be used, but i wouldn't reccomend a shutdown. if you have applications open you can lose stuff or worse corrupt your system.
what's wrong with just letting the system go to sleep/idle? that's what mine does, but i have mine for 5 min if idle then it turns off the monitor & just idles, 0% cpu. i just have to move the mouse or press a key to wake it up.

---

### Post by BennyS on 2007-08-22
some of our user leave the pc on and just go.
so i think better set 1 hour idle shutdown to save electricity bill hehe

B.

---

### Post by Thingymebob on 2007-09-05
The problem with sleep/idle for me is that I can not get ubuntu to wake up again on my 4 year old sons laptop who uses the machine for 5 minutes and then wanders off to do something else for hours. Inevitably what happens after the machine goes to sleep, is the power button gets held until the system stops which is potentially far more damaging than a shutdown with apps open.

I know what cron does and how it does it, but would be grateful of some advice on a script I could use to automate shutting down after 1 idle hour. Or is there a way to modify the power management settings to do this?

---

### Post by rpontes on 2008-03-30
Hey, 

I know this is an old thread but I fought with this issue because my kid would leave her system running all day, it's old so the power management is limited. I called the script sidle.shl and execute it using cron, from a user location /home/ubuntu. It checks for activity for the id defined by userid, I set it to shutdown after 25 minutes. It works so hope it helps... in the spirit of saving energy. 

#!/bin/bash
#
# This is scheduled in CRON using ROOT, it runs every 5 minutes 
# and uses who -a to determine user activity. Once the idle time is
# more than the threshold value it shuts the system down.
#
echo "Start of sidle.shl"

threshold=25
log=/home/ubuntu/sidle.log
userid=kids
inactive=`who -a | grep $userid | cut -c 45-46 | sed 's/ //g'`

if [ "$inactive" != "" ]; then
	
	  echo "Idle time is: " $inactive

	  if [ "$inactive" -gt "$threshold" ]; then
	    	echo "Threshold met so issuing shutdown command"
	       	/sbin/shutdown -h now
	  else
	    	echo "Bellow threshold"
	  fi
else
	  echo "Idle time is: 0"
fi 

echo "Ending"

---

### Post by vashwood on 2008-06-16
With rpontes help, here's a script I put together for my headless server to suspend after network inactivity.  Let me know if you guys have any suggestions.

I enabled 'sudo /etc/acpi/sleep.sh force' to run w/o password by running

sudo visudo and adding the line at the End of File

```
ryan ALL= NOPASSWD: /etc/acpi/sleep.sh force
```

```
#!/bin/bash
#
# This is scheduled in CRON.  It will run every 20 minutes
# and check for inactivity.  It compares the RX and TX packets
# from 20 minutes ago to detect if they significantly increased.
# If they haven't, it will force the system to sleep.
#

log=~/Scripts/idle/log

# Extract the RX/TX
rx=`/sbin/ifconfig eth0 | grep -m 1 RX | cut -d: -f2 | sed 's/ //g' | sed 's/errors//g'`
tx=`/sbin/ifconfig eth0 | grep -m 1 TX | cut -d: -f2 | sed 's/ //g' | sed 's/errors//g'`

#Write Date to log
date >> $log
echo "Current Values" >> $log
echo "rx: "$rx >> $log
echo "tx: "$tx >> $log

# Check if RX/TX Files Exist
if [ -f ~/Scripts/idle/rx ] || [ -f ~Scripts/idle/tx ]; then
	p_rx=`cat ~/Scripts/idle/rx`  ## store previous rx value in p_rx
	p_tx=`cat ~/Scripts/idle/tx`  ## store previous tx value in p_tx
	
	echo "Previous Values" >> $log
	echo "p_rx: "$p_rx >> $log
	echo "t_rx: "$p_tx >> $log

	echo $rx > ~/Scripts/idle/rx    ## Write packets to RX file
	echo $tx > ~/Scripts/idle/tx    ## Write packets to TX file
	
	# Calculate threshold limit 
	t_rx=`expr $p_rx + 1000`
	t_tx=`expr $p_tx + 1000`

	echo "Threshold Values" >> $log
	echo "t_rx: "$t_rx >> $log
	echo "t_tx: "$t_tx >> $log
	echo " " >> $log
	 
	if [ $rx -le $t_rx ] || [ $tx -le $t_tx ]; then  ## If network packets have not changed that much
		echo "Suspend to Ram ..." >> $log
		echo " " >> $log
		rm ~/Scripts/idle/rx
		rm ~/Scripts/idle/tx
		sudo /etc/acpi/sleep.sh force  ## Force Sleep
	fi
	
#Check if RX/TX Files Doesn't Exist
else 
	echo $rx > ~/Scripts/idle/rx ## Write packets to file
	echo $tx > ~/Scripts/idle/tx
	echo " " >> $log
fi
```

---

### Post by stream303 on 2008-06-18
> **rpontes said:**
> I know this is an old thread but I fought with this issue because my kid would leave her system running all day, it's old so the power management is limited.

This is working GREAT on my Apple G5 iMac, which has limited power management.  Thank you so much for the script - I'd like to share my experience based on your setup.

It works well, but I sometimes have virtual terminals or gnome terminals up and running, so I had to make some modifications to take those into account.

I did the normal **sudo nano -w /etc/crontab**, and my crontab checks every 5 minutes:

```
# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
00,05,10,15,20,25,30,35,40,45,50,55 * * * * root /home/stream303/poweroff.sh
#
```

Works great, and you can see it checking if you tail /var/log/syslog.  So far so good.

Now for the script - I just renamed it **poweroff.sh** and put it into my home directory out of habit.

```
#!/bin/bash
threshold=55
username=stream303
**inactive=`who -a | grep $username | cut -c 45-46 | sort | grep [0-9] | head -n1 | sed 's/ //g'`**

if [ "$inactive" != "" ]; then

echo "Idle time is: " $inactive

if [ "$inactive" -ge "$threshold" ]; then
echo "Threshold met so issuing shutdown command"
/sbin/shutdown -h now
else
echo "Below threshold"
fi
else
echo "Idle time is: 0"
fi
echo "Ending"
```

I made it executable with **sudo chmod +x poweroff.sh**, and then when everything was working, changed the chmod to 700 so only root can do anything with it.

To take into account virtual terminals or gui terminals being up, I had to use sort, as well as grep [0-9] (sort alone left me with one or more blank entries which choked), and then used head to look at just the one line with the least amount of inactivity.  I'm not using my Ubuntu forum logon name as my home username btw. :)

I can't believe how well this works and want to say thanks once again - my system is now shutting down to save energy based on user inactivity, rather than just a predetermined amount of time.  Due to hardware limitations, this is one thing that no Linux distro has been able to handle on my G5 iMac.

Note: I can't seem to make this work on my AMD64 box. :(

---

### Post by Roger-Roger on 2008-06-18
It's built in:

On the system menu: [System]->[Preferences]->[Screen Saver]

Then the screen saver settings dialogue appears.

Click the [Power Managment] button

In the "On AC Power" tab (the default one)

Slide the Actions / "Put computer to sleep when inactive for"
to 1 hour.

then [Close].

Voila!

hope this helps,
R-R

---

### Post by vashwood on 2008-06-18
> **Roger-Roger said:**
> It's built in:

On the system menu: [System]->[Preferences]->[Screen Saver]

Then the screen saver settings dialogue appears.

Click the [Power Managment] button

In the "On AC Power" tab (the default one)

Slide the Actions / "Put computer to sleep when inactive for"
to 1 hour.

then [Close].

Voila!

hope this helps,
R-R

That doesn't shut down the computer after inactivity or put the computer to sleep after network inactivity.  That just puts the computer to sleep after regular inactivity.

---

### Post by stream303 on 2008-06-18
With some models of Apple PPC, the hardware doesn't respond to normal settings, so you have to rely on work-arounds such as this.

The only thing my box will do is blank the screen, or activate the screensaver - other settings just get ignored.  This is due to the various manufacturers not providing the linux devs enough information.

---

