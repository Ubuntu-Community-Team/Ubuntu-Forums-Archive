---
title: "How-to: Keeping Your Laptop Cool"
date: 2011-07-12
forum: Apple Hardware Users
---

### Post by Neds Moar Salt on 2011-07-12
As far as I know, the lack of cpu scaling on macbook(pro)s is a big problem.  Don't bother using your brain to find a solution, for I am here to do that for you.  Note that the script will not work very properly on the new quad-core computers.  You can do some tweaking to get it running though.

Step 0: If you read the official Ubuntu MacbookPro page, you can skip this.
We need to ensure that sensors are working properly here.  Do these things:
apt-get install lm-sensors
sensors-detect (make sure you allow it to edit /etc/modules)
And for now: modprobe coretemp

Step 1: Put the following script in /usr/local/sbin: 
```
TEMP1=55000
TEMP2=65000
FANSPEEDLOW=2000
FANSPEED1=4000
FANSPEED2=6200

COUNT=1

for i in `seq 1 9`
do

CURRTEMP1=`cat /sys/devices/platform/coretemp.0/temp1_input`
CURRTEMP2=`cat /sys/devices/platform/coretemp.1/temp1_input`

if test $CURRTEMP1 -ge $TEMP2; then
echo $FANSPEED2 > /sys/devices/platform/applesmc.768/fan1_min
elif test $CURRTEMP1 -ge $TEMP1; then
echo $FANSPEED1 > /sys/devices/platform/applesmc.768/fan1_min
else
echo $FANSPEEDLOW > /sys/devices/platform/applesmc.768/fan1_min
fi

echo "Sleeping for 6 seconds"
echo $i

sleep 6

done
```Step 2: Add this script to root's crontab.   It needs to run every minute.  Here is my crontab line: ```
* * * * * /usr/local/sbin/temp.sh >> /var/log/temp.sh.log
```  Use google if you don't know how to do this.  You're a linux user now, get used to it.

Step 3: Check /var/log/temp.sh.log to see if things are working

Step 4: Tweak the values to suit your temperature needs.  Resting that hot computer on your leg is bad for your sperm count you know.

---

### Post by teejmya on 2011-07-13
I'm diggin' your style, and the way you tell things. Love it.

But I just wanted to say that some won't need this. I'm rocking a Macbook 6,1, a white unibody model, and the fan comes right on when it needs to.

---

### Post by Neds Moar Salt on 2011-07-13
> **teejmya said:**
> I'm diggin' your style, and the way you tell things. Love it.

But I just wanted to say that some won't need this. I'm rocking a Macbook 6,1, a white unibody model, and the fan comes right on when it needs to.

Then you are certainly luckier than I.  Mine runs at a constant 2000 rpm.

---

### Post by alexmurray on 2011-07-14
Have you tried [resetting your SMC]("http://support.apple.com/kb/ht3964") - my fans also work fine to regulate the temp without any such script.

---

