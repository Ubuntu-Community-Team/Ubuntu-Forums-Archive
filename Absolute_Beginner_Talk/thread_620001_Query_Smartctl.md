---
title: "Query Smartctl"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by kilroy423 on 2007-11-22
I'm wondering if there are any negative effects on querying smartctl too many times.  I have a script that I plan on running to monitor the drives temperature and was wondering if it would have any adverse effects on the drive.  If I query the drive every 5 minutes could this cause damage to the drive in the long run?



thx

---

### Post by kilroy423 on 2007-11-25
*bump*

---

### Post by nick_h on 2007-11-25
smartctl should just query the drive interface to get the SMART data.  The hddtemp utility does a similar thing and gives you the option to create a log entry after a specified interval (in seconds).

Both of these utilities should be safe to run frequently.  There are no warnings against doing so in the man pages.

---

### Post by kilroy423 on 2007-11-27
> smartctl should just query the drive interface to get the SMART data. The hddtemp utility does a similar thing and gives you the option to create a log entry after a specified interval (in seconds).

Both of these utilities should be safe to run frequently. There are no warnings against doing so in the man pages.

Thanks for your reply.  Correct it will query the drive for SMART data, but I think that it might  have some kind of effect on the read/write and I was concerned that it might in the long run cause some kind of damage to the device.  What is hddtemp?  I have written a bash script to query smartctl and dump information to a textfile with a timestamp and was hoping to setup a cron job to have it check the temp every 5-15 mins.

Thanks

---

### Post by nick_h on 2007-11-27
hddtemp is a utility that reads the drive temperature from the SMART data.  You can then use the sensors applet to display the temperature as an applet in a panel.  By default this reads the data every 2 seconds.  You can install it with:
```
sudo apt-get install hddtemp
```
The sensors-applet package should already be installed.

hddtemp also has an option to write the data to the syslog at a specified interval.  You could then obtain the data with a simple grep of the syslog.

My understanding is that the SMART data is read from the interface and not the actual disk.  I haven't seen any bad effects of monitoring the drive temperature every 2 seconds.

---

### Post by kilroy423 on 2007-11-28
Thanks Nick_h

I will try out hddtemp and see how it works for me

thanks

---

