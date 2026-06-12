---
title: "[SOLVED] Need a script to run  ntpdate at boot-up of Gutsy"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by bw44 on 2007-12-12
A problem with ntpdate in earlier versions of Ubuntu has been reported and discussed in other threads, but I haven't found an answer for Gutsy Gibbon.  Can anyone help?

I would like to have ntpdate run at boot-up and set the time on my machine.  I don't need any of the more advanced time synchronization facilities for my standalone system.

According to the Ubuntu community documentation at [https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=NTPTimeSynchronisation#head-7ce84659ce7371da7976d6527d1e0263297e90ff](https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=NTPTimeSynchronisation#head-7ce84659ce7371da7976d6527d1e0263297e90ff)   > Ubuntu comes with ntpdate as standard, and will run it once at boot time to set up your time according to Ubuntu's NTP server. I don't know if this was true on my Feisty system, but when I upgraded to Gutsy ntpdate was not installed.  I used the package manager to install it, and it runs fine from the command line using the time signals from Canada's two NRC servers to correct the system clock.

From other threads, I learned that a startup script is needed to cause ntpdate to run at boot-up. Back in February there was a discussion I didn't understand about ntpdate and something called hwclock (I think) wrestling for control of the time at different "run levels".  I have the feeling that ntpdate lost the match, but one poster said it helped him solve the problem.  I couldn't figure it out.  (I tried posting to those threads, but maybe the people who worked on it then aren' subscribed any more.)  

I haven't ever written a start-up script (or any script) and only have a vague idea of how to put one where it would run ntpdate at boot-up.  Does anyone have such a script working for Gutsy with a "how-to" install it?  I'd really appreciate it.

Thanks in advance.

---

### Post by perce on 2007-12-12
Have you tried right-clicking on the clock, then choosing "Adjust data and time" and then set 
configuration to "keep synchronized with internet servers"?

---

### Post by bw44 on 2007-12-12
> **perce said:**
> Have you tried right-clicking on the clock, then choosing "Adjust data and time" and then set 
configuration to "keep synchronized with internet servers"?

I tried that, just to see what the options were.  The configuration box gives the options "Manual" and "Keep synchronized with Internet servers"  If I chose the second and click "synchronize now" it tells me that "NTP support is not installed."  which is not surprising since I haven't installed it.  Clicking "synchronize now" in the manual setting does not appear to change the time but gives me no messages.

But the whole point of having ntpdate run at boot-up time is to make it unnecessary to manually adjust the time.  I can always run the ntpdate command manually in terminal mode.

Thanks for your input, though.

---

### Post by yabbadabbadont on 2007-12-13
Try calling /etc/network/if-up.d/ntpdate in your /etc/rc.local file.  (Before the "exit 0" at the bottom  ;))

---

### Post by bw44 on 2007-12-13
> **yabbadabbadont said:**
> Try calling /etc/network/if-up.d/ntpdate in your /etc/rc.local file.  (Before the "exit 0" at the bottom  ;))
There is an /etc/init.d/rc.local file, and an  /etc/network/if-up.d/ntpdate script (attached) but I haven't a clue how to determine if and when the script will run at boot-up and how to specify the  time server addresses I want to sync to. I can't see the name of the default time server anywhere in the script. 

I'll try what you suggested if I can figure out how to do it, but I need a bit more guidance, if someone can help.  (There is no "exit 0" at the bottom of the rc.local file; the last line is "esac")

Thanks.

---

### Post by yabbadabbadont on 2007-12-13
Maybe they have changed things up in Gutsy, but in Fiesty it looks like this:
```
/home/daffy $ cat /etc/default/ntpdate 
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# Set to "yes" to take the server list from /etc/ntp.conf, from package ntp,
# so you only have to keep it in one place.
NTPDATE_USE_NTP_CONF=no

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
NTPSERVERS="time-ext.missouri.edu"

# Additional options to pass to ntpdate
NTPOPTIONS=""
/home/daffy $ cat /etc/rc.local
#!/bin/bash
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

/etc/network/if-up.d/ntpdate

exit 0

```
Note: I have changed the /etc/rc.local to explicity use /bin/bash in the first line as I had issues with the previous setting.

---

### Post by bw44 on 2007-12-13
> **yabbadabbadont said:**
> Maybe they have changed things up in Gutsy, but in Fiesty it looks like this:
```
/home/daffy $ cat /etc/default/ntpdate 
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# Set to "yes" to take the server list from /etc/ntp.conf, from package ntp,
# so you only have to keep it in one place.
NTPDATE_USE_NTP_CONF=no

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
NTPSERVERS="time-ext.missouri.edu"

# Additional options to pass to ntpdate
NTPOPTIONS=""
/home/daffy $ cat /etc/rc.local
#!/bin/bash
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

/etc/network/if-up.d/ntpdate

exit 0

```
Note: I have changed the /etc/rc.local to explicity use /bin/bash in the first line as I had issues with the previous setting.

Thanks very much for this -- it's gotten me further, but I'm still not there yet!   I didn't even know about the /etc/default/ntpdate file (Is any of of this documented anywhere?!?!)  Anyway, I modified my default based on yours:```
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# Set to "yes" to take the server list from /etc/ntp.conf, from package ntp,
# so you only have to keep it in one place.
NTPDATE_USE_NTP_CONF=no

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
NTPSERVERS="time.nrc.ca"

# Additional options to pass to ntpdate
NTPOPTIONS=""
```That was easy, though I don't really understand what the first two comment lines are saying.  But now for the tricky bit:  as I mentioned, there's no /etc/rc.local file in my Gutsy system.  There's a /etc/init.d/rc.local file which looks like this: ```
PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
``` which doesn't look (to me, anyway) much like your /etc/rc.local, though maybe it serves a similar function in the Gutsy context.  What's weird is it seems to be testing whether /etc/rc.local is executable, but the file doesn't seem to exist!!

At this point I'm pretty confused about when these initialization scripts get run, about run levels, and about how the scripts actually work.  I really appreciate your trying to help, but I'm getting the feeling that something has changed in Gutsy.  You would probably be able to sort it out pretty quickly, but I'm just floundering.  I have a copy of the  _Ubuntu Linux Bible_ which must describe how it was under Feisty, because it doesn't seem to match the scripts in Gutsy.

I'm giving myself a crash course in bash scripting and studying all the ntpdate-related scripts I can find, but how many more, like the default, have I missed? 

I'll post a more specific question when I know a bit more (or actually figure it out!)  Wish me :lolflag:

Cheers.

---

### Post by qpieus on 2007-12-13
I think this is what you're looking for. This is the method I use and my clock is right on the money. I'm not sure if it runs at boot time though, at a minimum it runs daily. 

Unpack the attached file and place the ntpdate file (a script) in the /etc/cron.daily directory. This script will be run daily and have the ntpdate program contact the ntp.ubuntu.com time server to get the time and set your clock. You can change the time server of course.

Here's the script text if you'd rather make your own.```
#!/bin/bash
#
# cron script to update time
# place in /etc/cron.daily


ntpdate ntp.ubuntu.com
```
If you want it run more frequently, put the script in etc/cron.hourly instead.

---

### Post by bw44 on 2007-12-14
> **qpieus said:**
> I think this is what you're looking for. This is the method I use and my clock is right on the money. I'm not sure if it runs at boot time though, at a minimum it runs daily. 

Unpack the attached file and place the ntpdate file (a script) in the /etc/cron.daily directory. This script will be run daily and have the ntpdate program contact the ntp.ubuntu.com time server to get the time and set your clock. You can change the time server of course.

Here's the script text if you'd rather make your own.```
#!/bin/bash
#
# cron script to update time
# place in /etc/cron.daily


ntpdate ntp.ubuntu.com
```
If you want it run more frequently, put the script in etc/cron.hourly instead.

That's great -- and so simple!  I'll definitely install this on my system. Any idea when daily cron scripts run? Also, what happens to any error codes returned from the script, like if the time server is unavailable?

I'm still going to try and figure out how to get ntpdate to run at boot-up since it's turned out to be a great learning experience.  (If I get it working I'll post the results, though with your cron solution and fancier ntp syncing available, I'm not sure anyone will want to implement it.)

Thanks very much!

---

### Post by bw44 on 2007-12-14
qpieus,

When I put my script file into /etc/cron.daily I noticed that the other files there had their permission set to -rwxr-xr-x so I chmod-ed my script file to be the same.  Was this necessary and correct?

Thanks.

---

### Post by qpieus on 2007-12-14
> **bw44 said:**
> qpieus,

When I put my script file into /etc/cron.daily I noticed that the other files there had their permission set to -rwxr-xr-x so I chmod-ed my script file to be the same.  Was this necessary and correct?

Thanks.
That probably wasn't necessary, but there's no harm in it either. As long as it is executable it should work fine.

---

### Post by qpieus on 2007-12-14
> **bw44 said:**
>  Any idea when daily cron scripts run? Also, what happens to any error codes returned from the script, like if the time server is unavailable?
Not sure on when the daily crons run. They are set to a specific time (as all cron jobs are), but there's also an interaction between cron.daily and the system anacron program that might affect when they are run. So, while cron.daily has a set time to run, anacron might cause the cron.daily jobs to run at a different time. I'm a little confused on the subject, as you can tell :) I looked into it a little bit last night when I replied with the script, but couldn't figure out the interaction. I'll look into it some more later because I'm curious now. If anyone else knows, please let us know.

As far as error code output goes, I think that the ntpdate output goes to the system mail. I used to have my system mail set up to forward the mail to my gmail account, and I would get a daily email that said the time was changed by x seconds. So I guess error messages are sent to the system mail too. Again, not sure on this - I have since reinstalled and I don't have the system mail forwarded anymore (and I do not routinely check it).

---

### Post by bw44 on 2007-12-14
qpieus,

Thanks for the additional information.  I'm glad you mentioned the "System Mail" because I was checking the system log and saw this message: ```
Dec 14 07:37:18 DELL2 anacron[16099]: Job `cron.daily' terminated (mailing output)
Dec 14 07:37:18 DELL2 anacron[16099]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Dec 14 07:37:18 DELL2 anacron[16099]: Normal exit (1 job run)
```and wondered if it had something to do with error messages.  I'll look into it too, since I didn't know about the system sendmail facility. (From the message it looks like mine isn't set up.)

---

### Post by tech0007 on 2007-12-14
Hi,

I just add this one-liner to /etc/rc.local before "exit 0" and it works!

.....
/usr/sbin/ntpdate -u time.nist.gov
exit 0

---

### Post by spiderbatdad on 2007-12-14
why not put the script in your /home/hostname directory and enable it as a startup program with an order of 99?

---

### Post by bw44 on 2007-12-14
> **tech0007 said:**
> Hi,

I just add this one-liner to /etc/rc.local before "exit 0" and it works!

.....
/usr/sbin/ntpdate -u time.nist.gov
exit 0

I'm running Gutsy and there isn't an /etc/rc.local file and the only thing close to that name is /etc/init.d/rc.local and this script doesn't have an "exit 0" line  in it. (see attached copy of file)  Someone else suggested a similar addition to /etc/rc.local but I don't understand how the attached script works and if and where to add the code you mentioned. 

Any thoughts on this? :confused:

Thanks for the help.

---

### Post by bw44 on 2007-12-14
> **spiderbatdad said:**
> why not put the script in your /home/hostname directory and enable it as a startup program with an order of 99?

Thanks for the suggestion, but this looks (to this noob) like a completely different approach.  I haven't any idea what the /home/hostname directory is for, and am not sure how to enable startup programs (with Bootup-Manager,  maybe?), and how to give one an order of 99.

I think I'll try to get the stuff about the init process sorted out, and try to get ntpdate to run at boot-up in that way. (Of course your suggestion may boil down to the same thing, but I can't tell!)

Cheers.

---

### Post by qpieus on 2007-12-14
> **bw44 said:**
> qpieus,

Thanks for the additional information.  I'm glad you mentioned the "System Mail" because I was checking the system log and saw this message: ```
Dec 14 07:37:18 DELL2 anacron[16099]: Job `cron.daily' terminated (mailing output)
Dec 14 07:37:18 DELL2 anacron[16099]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Dec 14 07:37:18 DELL2 anacron[16099]: Normal exit (1 job run)
```and wondered if it had something to do with error messages.  I'll look into it too, since I didn't know about the system sendmail facility. (From the message it looks like mine isn't set up.)
yep, mine says that too. I don't think it necessarily has anything to do with errors. My clock is exact so I know ntpdate is working ok. This is where is saw that there's some interaction between anacron and cron.daily.

---

### Post by bw44 on 2007-12-14
> **qpieus said:**
> yep, mine says that too. I don't think it necessarily has anything to do with errors. My clock is exact so I know ntpdate is working ok. This is where is saw that there's some interaction between anacron and cron.daily.

Good to know there's some consistency in all  this stuff !

---

### Post by spiderbatdad on 2007-12-14
/home/hostname  was intended to represent your home directory. and enabling a startup program is a simple gui found in System-->Preferences-->Sessions.

---

### Post by bw44 on 2007-12-14
> **spiderbatdad said:**
> /home/hostname  was intended to represent your home directory. and enabling a startup program is a simple gui found in System-->Preferences-->Sessions.

Thanks for that clarification.  My script is:```
#!/bin/sh
exec /usr/sbin/ntpdate -u time.nrc.ca
```
I added it to the Sessions "Additional startup programs" list, but how do I give it an order of 99? I can see under the Current Session tab a list of currently running programs with their order set, but my script isn't listed there.  Even if it executes at boot-up it won't be running when I go to open the Session manage: it'll be over and done with.  What have I missed?

---

### Post by spiderbatdad on 2007-12-14
add to start up programs. change order number under current sessions, then "remember currently running applications" under sessions options. note: you may have to close and reopen sessions to see it added to current sessions. I did a similar script to run espeak and have my computer say, "Hello, Bill" after boot up. It took several tries to finally stick.

---

### Post by yabbadabbadont on 2007-12-14
> **bw44 said:**
> I'm running Gutsy and there isn't an /etc/rc.local file

Then **create** one...  ;)

I posted the complete contents of mine earlier.  Your /etc/init.d/rc.local quite clearly (well, at least for anyone who understands shell scripts ;)) looks for the existence of an executable /etc/rc.local file and will run it if it finds one.

This is the part of the script that you posted that does it:
```
do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

```
It says, "If /etc/rc.local exists, and is executable, then run it.  ;)

---

### Post by Duck2006 on 2007-12-14
Have you looked in synaptic package manager for NTP.

---

### Post by bw44 on 2007-12-14
> **spiderbatdad said:**
> add to start up programs. change order number under current sessions, then "remember currently running applications" under sessions options. note: you may have to close and reopen sessions to see it added to current sessions. I did a similar script to run espeak and have my computer say, "Hello, Bill" after boot up. It took several tries to finally stick.

Well, I got the script set up as you suggested in Sessions with order 99, but it doesn't correct the time on boot-up.  I don't know if it doesn't work, or simply doesn't run.  One thing I noticed though, is that when I simply execute the script:```
#!bin/sh
/usr/sbin/ntpdate time.nrc.ca
``` it doesn't work either. I have to put a sudo in front and run in terminal, which requests I enter my password:```
#1bin/sh
sudo /usr/sbin/update time.nrc.ca
``` so it probably has something to do with permissions. The script is marked executable, but I guess that's not good enough.  How do I tell the system it's OK to run the script at boot-up without requiring the password?

Thanks for all your efforts.  (As you can see from other posts there are competing ideas about how to solve this riddle!)

---

### Post by spiderbatdad on 2007-12-14
thats why i suggested putting the .sh script in your /home/ directory or```
sudo chmod a+x /usr/sbin/ntpdate time.nrc.ca
```

---

### Post by bw44 on 2007-12-15
To all the folks who have taken the time to give me help (yabbadabbadont, spiderbatdad, qpieus, tech0007, and any others who've contributed to this thread) I feel I owe you an apology.  Early on, yabba suggested I add a line to /etc/rc.local and I insisted there was no such file in Gutsy.  Well, I was dead wrong!  There is a such a file, and I'm now going to go back and make sure I understand  what yabba recommended and test it.  I'll also test, or retest the suggestions the rest of you made, which will probably also work! ( I can't test them yet since I'm away from my own computer.)  I'll post the results, in case anyone's still curious.

Thanks so much for all your help.  I've learned a whole lot from this exercise already. (Your time wasn't wasted -- really!!)

Cheers.

---

### Post by bw44 on 2007-12-17
Yabbadabbadont,
Starting with the vanilla version of the Gutsy files, I modified /etc/default/ntpdate as per your suggestion.  The modified file looks like this:```
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# Set to "yes" to take the server list from /etc/ntp.conf, from package ntp,
# so you only have to keep it in one place.
# (Package ntp not installed on my system: /etc/ntp.conf is present but empty.)

# NTPDATE_USE_NTP_CONF=yes

NTPDATE_USE_NTP_CONF=no

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.

# NTPSERVERS="ntp.ubuntu.com"

NTPSERVERS="time.nrc.ca"

# Additional options to pass to ntpdate

NTPOPTIONS=""
```
This change alone produces the desired result: the system time is sycn-ed at system start-up with the ntpserver I specify.  The following record is written to the log and from the time stamp it's clear that it's been run right after the network is started.

```
Dec 17 19:29:25 DELL2 ntpdate[5618]: step time server 132.246.168.148 offset -42.016938 sec
```

If I also modify /etc/rc.local (the script I insisted didn't exist!) as you suggested:```
#!/bin/bash 
# above changed at suggestion of yabbayabbadont from #!/bin/sh -e
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

/etc/network/if-up.d/ntpdate

exit 0
```This causes the first two of the following log records to be written during the boot-up process.  From the entry following them it looks as though the network is not yet fully intialized, so it can't find the host.

```
Dec 17 19:30:00 DELL2 ntpdate[5316]: can't find host time.nrc.ca 
Dec 17 19:30:00 DELL2 ntpdate[5316]: no servers can be used, exiting
Dec 17 19:30:01 DELL2 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction.
```

Including both modified scripts does not prevent the time being correctly sync-ed at(network) start-up though.

I'm not sure what the relationship is between /etc/rc.local and /etc/default/ntpdate. I think that when the network comes up initailly or is re-enabled, the script /etc/network/if-up/d/ntpdate is run; it checks for and runs /usr/sbin/ntpdate-debian which in turn checks for the presence of /etc/default/ntpdate and uses the values there to set options and servers to execute /usr/bin/ntpdate.  This seems consistent with the results anyway.

I think the solutions that were posted by qpieus (sync with cron.daily rather than at boot-up), and spiderbatdad (using the facilities of the Sessions preferences to launch ntpdate) and tech007, will also get the job done, but I haven't fully tested them.  I'll post those results later.

Thanks again for your help.  If my understanding of what's going on is wrong, please correct it!

---

### Post by bw44 on 2007-12-17
> **Duck2006 said:**
> Have you looked in synaptic package manager for NTP.

Thanks for the suggestion.  I only installed ntpdate, since I  really don't need the facilities of the full ntp package.  I'm sure it would allow me to time sync in a more precise way, and with ntp I probably  wouldn't have needed to do anything special at system start-up time. But why incur the overhead if it's not needed?

Cheers.

---

### Post by bw44 on 2007-12-17
> **tech0007 said:**
> Hi,

I just add this one-liner to /etc/rc.local before "exit 0" and it works!

.....
/usr/sbin/ntpdate -u time.nist.gov
exit 0

I tried your suggestion, but it didn't cause the time to be sync-ed at boot-up on my system.  There must be something else in place on your system but not mine. Do you have the ntp package installed, or just the ntpdate (which is all I have)?

Thanks anyway, though.

---

### Post by bw44 on 2007-12-17
> **spiderbatdad said:**
> thats why i suggested putting the .sh script in your /home/ directory or```
sudo chmod a+x /usr/sbin/ntpdate time.nrc.ca
```
I'm not sure I understood what your suggestion was saying.  The "or " sort of confused me and the command didn't look right with the "time.nrc.ca" at the end.  I tried: ```
$sudo chmod a+x /usr/bin/ntpdate
``` and got no errors.  The file permissions are: ```
 -rwxr-xr-x 1 root root 45652 2007-10-04 16:59 /usr/sbin/ntpdate

``` which was what I expected.

The script is in my home directory: ```
#!/bin/sh
# tried both:
sudo /usr/sbin/ntpdate time.nrc.ca
# /usr/sbin/ntpdate time.nrc.ca
exit 0
``` which works fine and re-syncs the clock when run from the terminal line.  The Session seems to be correctly set up to run ntpdate at start-up with an order 99. But at boot-up the time is not sync-ed and I cannot see any messages in the system log that would indicate what the problem is.  Can you suggest anything else?

Thanks.

---

### Post by spiderbatdad on 2007-12-17
i was suggesting to make the .sh file executable...the actual bash script

---

### Post by spiderbatdad on 2007-12-17
does your filename end in .sh?

---

### Post by bw44 on 2007-12-17
> **spiderbatdad said:**
> i was suggesting to make the .sh file executable...the actual bash script

I had given it these permissions:```
-rwxr-xr-x 1 bob bob    103 2007-12-17 22:15 ntpdate
``` Still no joy.:(

(Or did you mean something else by make the .sh file executable?  I'm really kind of new to all this, so what might be obvious to a more experienced Linux person, may not be to me.)

Thanks.

---

### Post by spiderbatdad on 2007-12-17
the file should now be a program in your home directory you should see the file with a blue diamond shape inside it. If not, I believe you need to change the filename to include .sh at the end.

---

### Post by bw44 on 2007-12-17
> **spiderbatdad said:**
> the file should now be a program in your home directory you should see the file with a blue diamond shape inside it. If not, I believe you need to change the filename to include .sh at the end.

Yes, that's what the file icon looks like and it has permissions:```
-rwxr-xr-x 1 bob bob 52 2007-12-17 23:21 ntpdate.sh
```

The Sessions utility is a bit tempermental:  I changed the entry for running ntpdate at start-up to point to ntpdate.sh, but then it disappeared from the current session list. After a reboot it returned but with order=50, not 99, but I corrected all that. But it still doesn't sync the time at re-boot ](*,)

You don't have the ntp package installed, do you?

---

### Post by spiderbatdad on 2007-12-17
remember the current session option under the sessions options tab after you change and before you rebbot...and yes it is tempermental...and sometimes takes multiple attempts before sticking](*,)

---

### Post by bw44 on 2007-12-18
> **spiderbatdad said:**
> remember the current session option under the sessions options tab after you change and before you rebbot...and yes it is tempermental...and sometimes takes multiple attempts before sticking](*,)

I give up!  I don't understand the Session Preferences manager, and the only thing (I think) it did was cause a terminal session to launch automatically on the desktop when I restarted my system (which isn't really what I was after! )

Maybe I'll figure it out someday, but in the meantime between the /etc/default/ntpdate file settings and a script in the /etc/cron.daily (or /etc/ cron.hourly) directory, I think I'll be close enough to on time!

Cheers.

---

