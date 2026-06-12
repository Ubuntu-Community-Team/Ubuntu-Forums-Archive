---
title: "How do I disable all log file creation, rotation, etc.?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by tommy2888 on 2007-05-01
I have googled, and searched linux forums for an answer and have not found a good one yet.

I agree that log files are invaluable in troubleshooting problems, tuning systems, and much more.

However, I'd like to turn them on only when needed. In fact I'd like to disable all logging for day to day computer use.

Sound crazy? Yep, I can hear sysadmins groaning from here.

Even optimized logging Daemons do take some cpu cycles, right?

Logfile rotation minimizing with daily, monthly settings is not for newbies, these files start to add up, imagine a neat freak's reaction upon looking into his /var/log directory.

Most people I get to try Linux would run the other way if they saw their logs. Some do not trust those things they cannot understand and also have (unfounded) worries that their info will "leak" from the log to the internet, etc. Root access isn't exactly unobtainable. I mention all this to save time and filter out any replies that say logs are harmless, just leave them.

These solutions have been tried and failed:
Editing syslog.conf to log everything to /dev/null (other processes continue logging)
Setting file permissions on the actual logs to Owner-ReadOnly. (new RW ones appear upon reboot)
Linking /var/log to /dev/null (xorg refuses to launch because of the missing xorg.0.conf)
Setting scripts such as /etc/init.d/klogd permissions to not executable (this one doesn't seem to stop anything?)

Does anyone have a simple solution that doesn't require a notebook to keep tabs on in case a person wants to re-enable logging easily?

thx

---

### Post by LaurelLynn on 2007-05-01
I wouldn't worry to much about "newbies". They are not likely to know where to find the logs.
I've come across people who have used Linux for years without even knowing there were logs.

The problem your going to run into, is that unix/linux are distributed OSes.  As such no
one program controls log writing. Each program writes their own entries.

To stop them you would probably have to track them all down and recompile them without
the logging. Also, the kernal does logging so you would probably need to rebuild that too.

Simply blocking their access to the log files might actually break some important
system programs.

Since log entries are made by the individual programs though, there is nothing running
in the background, eating up addition clock cycles, just for log entries. So overhead is
very minimal.

---

### Post by tommy2888 on 2007-05-03
Thanks LaurelLynn,

Yeah tracking and finding configs for all those processes doing their own logging is the tedious part. I can config a lot of them with syslog.conf, since syslogd takes care of many processes' log options, but then there's the big issue with xorg.conf using xorg.0.log along with many others.

So far the only background process that refuses to run without a logfile is xorg.conf, and it should be configurable?

---

### Post by LaurelLynn on 2007-05-03
I would think so too!  The method will be in Xorgs documentation probably, not Ubuntus.  I'm impressed, sounds like you've made a lot of progress!

You probably don't need this warning, but remember to make a backup of xorg.conf before changing it. Being stuck without a GUI is a bit like finding yourself in the stone ages. ;)

---

### Post by tommy2888 on 2007-05-11
That's good advice LaurelLynn, I have a library of working xorg.conf files in a backup folder. Some for dual monitor setups, some for hdtv drivers (for a non standard HDTV setup), and then one or two for 3D features to work in my Radeon and nVidia, they can be valuable in terms of time to get the right setup to work.

I'd still love to see a working answer to this thread...now there's a need for USB stick based OS, and all the repetitive log file and swap file writes would kill the USB stick prematurely. 

So I'd install a bootable linux to a USB stick, remove log file writing, and run the swap in RAM, that's a new goal.

---

