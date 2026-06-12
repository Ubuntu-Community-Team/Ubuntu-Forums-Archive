---
title: "[SOLVED] UBUNTU 7.10 stops after Running local boot scripts"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by miklund on 2007-12-28
As a absolut beginer of using LINUX on my computer I have installed 7.10 and the installation process went OK. When restarting I got the UBUNTU start picture and then the following:
Starting anac(h)ronistic cron anacron [OK]
Starting deferred execution scheduler atd [OK]
Starting periodic command scheduler ...  [OK] 
Checking battery state [OK]
Running local boot scripts (/etc/rc.local) [OK]

and then nothing happens, no error message. I can type characters, type enter and so on but no real respons. What is wrong.

I have a Dell config (Dimension e521) with AMD Athlon 64 X2-processor 5000 (2.60 GHz, 512 K)
2GB RAM. The partition used only for this installation is 15 GB (No swap partition allocated).

Under the installation process I was not sure about the partition settings (for example bootable flag on or off).

---

### Post by tgilber1 on 2007-12-28
If the bootup process got to the rc.local script, then your system is finding the active boot partition.  Additionally, it may not be the rc.local file that is giving you the problem, even though it is the last line you see before it hangs up.  Furthermore, it is usually empty,except for commented text.  Try booting up using the recovery method, which will dump you out to root to conduct further investigation.

1. Hit ESC key at GRUB menu prompt
2. Select with the Recovery option
3. At root, check out the following files for errors /var/log/boot, /var/log/dmesg, /var/log/daemon, /var/log/message.  Type ls -l /var/log/* to see all files
4.  Note:  there are up to four log files for each log name (e.g., dmesg.1.gz, dmesg.2.gz, etc.).  Additionally, some are compressed, which requires a reader that is able to convert them to plain text for viewing.  Programs like nano are unable to do this, to my knowledge.  Hence, you need to use a program like vi or zmore to view the files.  The vi program is more cumbersome for new people to Linux, which is why zmore may be more suitable to a new user.
5.  Use your favorite viewer (e.g., vi) to check for errors in the files
6.  Check /etc/rc.local file for uncommented lines.  The files should only have one line, see below

rc.local dump - between dashed lines
-------------------------------------------------------------------------------------
!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
--------------------------------------------------------------------------------

Hopefully, this info gives you a good start to solving your problem

---

### Post by miklund on 2007-12-29
Thank you for answer!
teh file messages says: Exiting on signal 15. The other files do not contain any relevant errors (except that Network Manager seems to have some problem).

---

### Post by miklund on 2008-01-16
Solved by swedish forum message: Howto: AMD/ATI Catalyst Proprietary Linux Display Driver (text in swedish, link to AMD/ATI drivers)

---

