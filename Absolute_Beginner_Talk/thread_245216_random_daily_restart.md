---
title: "random daily restart"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by toddles on 2006-08-27
Hi folks, 

I wonder if anyone has any idea what might be causing this. Once a day at about 7:30 am my machine (which I keep going to all the time b/c of azureus) restarts for no reason that I can discern. I don't know how to use cron, so if there is a cron job running I don't know about it.

Here is what I found in the logs:
______
Aug 27 07:36:04 salamander exiting on signal 15
Aug 27 07:36:05 salamander syslogd 1.4.1#17ubuntu7: restart.

Aug 26 07:36:01 salamander exiting on signal 15
Aug 26 07:36:02 salamander syslogd 1.4.1#17ubuntu7: restart.

Aug 25 07:36:11 salamander exiting on signal 15
Aug 25 07:36:12 salamander syslogd 1.4.1#17ubuntu7: restart.

Aug 24 07:41:46 salamander exiting on signal 15
Aug 24 07:41:47 salamander syslogd 1.4.1#17ubuntu7: restart.

Aug 23 07:41:49 salamander exiting on signal 15
Aug 23 07:41:50 salamander syslogd 1.4.1#17ubuntu7: restart.
______

If anyone has idea I would appreciate it.

---

### Post by Pragmatist on 2006-08-27
Let see if salamander is started everytime you start your machine.

Restart your machine, then type this at a terminal:

```
ps -ef |grep salamander
```

Post the output here.

---

### Post by toddles on 2006-08-27
hey,

Salamander is the name of the machine so the only things that show are:

avahi     4696     1  0 Aug21 ?        00:00:00 avahi-daemon: running [salamander.local]
todd     20392 20167  0 15:00 pts/0    00:00:00 grep salamander


Sorry for the confusion.

---

### Post by Pragmatist on 2006-08-27
> **toddles said:**
> hey,

Salamander is the name of the machine so the only things that show are:

avahi     4696     1  0 Aug21 ?        00:00:00 avahi-daemon: running [salamander.local]
todd     20392 20167  0 15:00 pts/0    00:00:00 grep salamander


Sorry for the confusion.

Does the restart occur if your not running Azureus?  In other words, instead of leaving it on all night running Azureus and then finding that it restarted in the morning, what happens if you leave the machine on all night without azureus running?

---

### Post by toddles on 2006-08-28
> **Pragmatist said:**
> Does the restart occur if your not running Azureus?  In other words, instead of leaving it on all night running Azureus and then finding that it restarted in the morning, what happens if you leave the machine on all night without azureus running?

I tried this last night, and there was no difference. I read the man pages on anacron which is installed and running, but I do not see anything that looks like it calls for a restart. 

Is anacron a default installed package for Dapper? I did not install it unless it had something to do with a dependency.

---

### Post by Pragmatist on 2006-08-28
> **toddles said:**
> I tried this last night, and there was no difference. I read the man pages on anacron which is installed and running, but I do not see anything that looks like it calls for a restart. 

Is anacron a default installed package for Dapper? I did not install it unless it had something to do with a dependency.

You could check the config files for Cron.  However, unless you fiddled with it, I don't see why there would be some default to shut the machine off everyday ~7:30 am  Also, if it did, you could be sure there would be lots of other posts about it! :)  If you really want to eliminate cron as a possibilty, stop the cron daemon from running the night before.

If it were me, I'd try a liveCD.  First I'd try Ubuntu's liveCD.  I'd restart the system with the liveCD, login, then let it run all night and see if the same thing happens.  If it doesn't, then you know it is your specific Ubuntu system.  If it does the same thing, I'd then use another distro's liveCD the next night. I'd probably use Knoppix  for the other liveCD.  If the same thing happens with Knoppix, then it likely is a hardware issue and has nothing to do with your Ubuntu system.

---

### Post by Yosho121 on 2006-08-29
running as a live CD won't restart the machine the next morning. thats how I'm running my machine to be able to connect to the internet. BTW can some one help with that? Ubuntu is installed .

---

### Post by Pragmatist on 2006-08-30
> **Yosho121 said:**
> running as a live CD won't restart the machine the next morning. thats how I'm running my machine to be able to connect to the internet. 

My computer doesn't restart with a liveCD either.  My suggestion is to find out if toddles' system would restart with a liveCD ;)

> **Yosho121 said:**
> BTW can some one help with that? Ubuntu is installed .

I'm not sure what your question is.  Help with what?  Your more likely to get the help you need by posting a seperate thread with plenty of details.

---

### Post by handy on 2006-08-30
Do you mean that when you boot from the liveCD you can't connect to the internet?

If so?  Try turning of ipv6 in firefox, I have to before I can browse the web!

If you don't know how, search the forums, I know I've written it up atleast 20 times... :)

---

### Post by Pragmatist on 2006-08-30
Posting a problem in the forums is not just about getting your particular problem solved.  It is also about helping others solve the same or similar problem.

If you mix your problem into an unrelated thread you minimize both of the above goals!

1.) Your less likely to find the help you need.  When you make a seperate thread, you are more visible.  Some people just search by the header line.  Some people just search for unanswered threads (i.e. threads with 0 replies)

2.) Others are less likely to find the help they need.  If somebody has your internet problem and uses keywords "internet" and "liveCD" and "firefox" they'll get this thread too.  Why, among the hundreds of hits they get, would they read a thread labled "random daily restart".  

So, you won't get the responses and others won't find the answers even if you do.

Please post a new thread for a different problem.  Please don't respond to people who ignore this and jump into another's thread.

Thanks.

---

### Post by handy on 2006-08-30
> **Pragmatist said:**
> Posting a problem in the forums is not just about getting your particular problem solved.  It is also about helping others solve the same or similar problem.

If you mix your problem into an unrelated thread you minimize both of the above goals!

1.) Your less likely to find the help you need.  When you make a seperate thread, you are more visible.  Some people just search by the header line.  Some people just search for unanswered threads (i.e. threads with 0 replies)

2.) Others are less likely to find the help they need.  If somebody has your internet problem and uses keywords "internet" and "liveCD" and "firefox" they'll get this thread too.  Why, among the hundreds of hits they get, would they read a thread labled "random daily restart".  

So, you won't get the responses and others won't find the answers even if you do.

Please post a new thread for a different problem.  Please don't respond to people who ignore this and jump into another's thread.

Thanks.

I'm sorry I should have been more specific, I have posted the **solution** to the very common **ipv6** problem over 20 times. :rolleyes: 

Many of us can not access the internet without turning **ipv6** off in firefox.  I am one of those.  Be it **LiveCD** or hard disk drive install, makes no difference.

**The solution:**

Do the following to remove **IPv6** from your Ubuntu system, **IPv6** can cause your internet connection to be slow, or, as in my case, not work at all!!

Type **about:config** no quotes into the address field in Firefox.

Then type **ipv6** into the new **Filter:** field.

Double left click on the one & only line left to change it's boolean value to **True**

Close & re-open FireFox, then browse the web!

That's it!  & when it is the problem this easy fix works like a charm, & nothing else will do the job!!

I hope this helps you? :KS

---

### Post by Pragmatist on 2006-08-30
> **handy said:**
> I'm sorry I should have been more specific, I have posted the **solution** to the very common **ipv6** problem over 20 times. :rolleyes: 

Many of us can not access the internet without turning **ipv6** off in firefox.  I am one of those.  Be it **LiveCD** or hard disk drive install, makes no difference.

Your not understanding.  This ipv6 problem is not the problem of the Original Poster (OP) of this thread.  It doesn't even appear to be related!  Please don't post different problems within another's thread.  And, please don't give solutions to people who do.

---

### Post by handy on 2006-08-30
> **Pragmatist said:**
> Your not understanding.  This ipv6 problem is not the problem of the Original Poster (OP) of this thread.  It doesn't even appear to be related!  Please don't post different problems within another's thread.  And, please don't give solutions to people who do.

Sorry if I've offended your sense of order. :( 

But, I will continue to post wherever I think I can help someone!

Also, if you look back at my initial response I was directing them to search the forum's!

cya! :rolleyes:

---

### Post by rakotolavasanga on 2006-08-31
I too have noticed this message in the /var/log/messages file.  I'm no expert, but as nearly as I can tell this is not an error.  It also doesn't seem to coincide with a system reboot.  My machine shows this message everyday at 6:30 am, but the system uptime shows 30 days.  I would be interested to know if you have been at the machine to see if it really reboots.  Anyway, it seems that this is really just the sysklog daemon restarting according to the /etc/cron.daily/sysklogd file on the last line.  I don't think it's anything to worry about.  Let me know if that helps any or if you have discovered a better explanation.

---

### Post by dejanb on 2006-09-03
Yes, I saw same thing in a log file, 

Sep  3 06:25:11 pc exiting on signal 15
Sep  3 06:25:12 pc syslogd 1.4.1#17ubuntu7: restart.

It occurs every day at 6:35, for some one at 7:35 (probably depends on system time ofset)

uptime shows 4 days, that is ok, because I have rebooted server 4 days ago. 

This is not really restart of whole system.

Dean

---

### Post by endlesssnowfall on 2006-09-03
I'm having the same problem, at around the same time as well.  It always says something about receiving a "signal 15"
```

Sep  3 07:36:47 localhost exiting on signal 15
Sep  3 07:36:48 localhost syslogd 1.4.1#17ubuntu7: restart.

Sep  3 08:42:25 localhost gconfd (endlesssnowfall-29752): Received signal 15, shutting down cleanly
Sep  3 08:42:33 localhost gconfd (endlesssnowfall-29752): Exiting
```

---

### Post by delphinen on 2006-09-04
Im having the same... problem? this is very weird.

...
Sep  3 07:37:18 oasis exiting on signal 15
Sep  3 07:37:19 oasis syslogd 1.4.1#17ubuntu7: restart.
Sep  3 07:40:04 oasis exiting on signal 15
Sep  3 07:40:05 oasis syslogd 1.4.1#17ubuntu7: restart.
Sep  4 07:37:28 oasis exiting on signal 15
Sep  4 07:37:29 oasis syslogd 1.4.1#17ubuntu7: restart.
...

---

### Post by delphinen on 2006-09-05
Bump

---

### Post by endlesssnowfall on 2006-09-05
I've noticed that this happens everyday, for at least a week already...does anyone have a clue what is going on?  I tried searching for "signal 15" but I could not find anything of consequence.

```
Aug 25 07:36:46 localhost exiting on signal 15
Aug 25 07:36:47 localhost syslogd 1.4.1#17ubuntu7: restart.

Aug 26 07:36:49 localhost exiting on signal 15
Aug 26 07:36:50 localhost syslogd 1.4.1#17ubuntu7: restart.

Aug 27 07:36:46 localhost exiting on signal 15
Aug 27 07:36:47 localhost syslogd 1.4.1#17ubuntu7: restart.

Aug 28 05:05:12 localhost exiting on signal 15
Aug 28 05:05:13 localhost syslogd 1.4.1#17ubuntu7: restart.

Aug 29 07:36:21 localhost exiting on signal 15
Aug 29 07:36:22 localhost syslogd 1.4.1#17ubuntu7: restart.

Aug 30 07:36:29 localhost exiting on signal 15
Aug 30 07:36:30 localhost syslogd 1.4.1#17ubuntu7: restart.

Aug 31 07:36:45 localhost exiting on signal 15
Aug 31 07:36:46 localhost syslogd 1.4.1#17ubuntu7: restart.
Aug 31 07:40:07 localhost exiting on signal 15
Aug 31 07:40:08 localhost syslogd 1.4.1#17ubuntu7: restart.

Sep  1 07:37:54 localhost exiting on signal 15
Sep  1 07:37:55 localhost syslogd 1.4.1#17ubuntu7: restart.

Sep  2 07:41:04 localhost exiting on signal 15
Sep  2 07:41:05 localhost syslogd 1.4.1#17ubuntu7: restart.

Sep  3 07:36:47 localhost exiting on signal 15
Sep  3 07:36:48 localhost syslogd 1.4.1#17ubuntu7: restart.

Sep  4 07:36:25 localhost exiting on signal 15
Sep  4 07:36:26 localhost syslogd 1.4.1#17ubuntu7: restart.
```

---

### Post by delphinen on 2006-09-11
bump.

---

### Post by Grey on 2006-09-14
bump for me too.  I am having a similar problem.

[http://ubuntuforums.org/showthread.php?t=257174](http://ubuntuforums.org/showthread.php?t=257174)

---

### Post by toddles on 2006-09-16
> **Grey said:**
> bump for me too.  I am having a similar problem.

[http://ubuntuforums.org/showthread.php?t=257174](http://ubuntuforums.org/showthread.php?t=257174)

Mine is an athalon 64 too. I have a newbon in the house so I neglected this post. Aplogies to all. 

So, here is what I did/discoverd. I tourned off thefollowing services on mu machiine (System>Admin>Services):
Ancron 
Cron
ATD

This stopped the signal from being sent and stopped many (but not all) of the restarts. 

What I discovered after some searching  and messing arou nd is that (1)the computer restarts when there is a high sustained load on the processor, and (2) there is a bug that dates back to Ubuntu 5 that causes this. Unfortunetly, I lost the bug number when I was inturupted by a 1AM bout with colic. IF anyone can find it I would be apreciative. I belive the original bug reporter was running an athalon 64 3200+ but I could be wrong.

My solution so far has benn to leave cron off until I can figure out what is knocking everything out and fix it. 

If anyone cares to regute my theory, go to. I am not proud. If this sounds like BS, pin me to the wall.

---

### Post by endlesssnowfall on 2006-09-17
This has been happening to me on two computers, first my Pentium M Thinkpad, then my Athlon 64 3200+ homebuilt desktop as well.

---

### Post by bbukh on 2006-09-17
I have a similar problem. However, unlike the previous poster the reboot does not happen immediately after receiving signal 15, but some time later. Here is /var/log/message fragment

Sep 17 07:16:50 my-desktop -- MARK --
Sep 17 07:35:54 my-desktop exiting on signal 15
Sep 17 07:35:55 my-desktop syslogd 1.4.1#17ubuntu7: restart.
Sep 17 07:55:55 my-desktop -- MARK --
Sep 17 08:15:55 my-desktop -- MARK --
Sep 17 08:35:55 my-desktop -- MARK --
Sep 17 08:55:55 my-desktop -- MARK --
Sep 17 09:15:56 my-desktop -- MARK --
Sep 17 09:35:56 my-desktop -- MARK --
Sep 17 09:54:56 my-desktop syslogd 1.4.1#17ubuntu7: restart.
Sep 17 09:54:57 my-desktop kernel: Inspecting /boot/System.map-2.6.15-26-386
Sep 17 09:54:57 my-desktop kernel: Loaded 23037 symbols from /boot/System.map

-Boris

---

### Post by endlesssnowfall on 2006-09-18
I wonder why this is happening to everyone at very similar times?  I couldn't think of anything that could explain this.

---

### Post by bbukh on 2006-09-18
Today, I woke up at 9am, and I found my keyboard not responding, and the window selector in KDE not responding even to mouse. Shut down the computer using mouse only, and then looked at logs, and there is this mysterious

Sep 18 07:35:52 my-desktop exiting on signal 15
Sep 18 07:35:54 my-desktop syslogd 1.4.1#17ubuntu7: restart.

at exactly the same time, down to a minute.

-Boris

---

### Post by bbukh on 2006-09-18
Ok, basically what happens is that file /etc/cron.d/anacron instructs cron to boot anacron at 7:30am. The cron diligently does its thing, and reads /etc/anacrontab which tells it to go through through cron.daily jobs in five minutes. The result: at 7:35 everyday cron.daily is executed. Then something goes awfully wrong...

If someone figures out what goes awfully wrong before I manage to, please tell me!

Boris

---

### Post by endlesssnowfall on 2006-09-19
I've been finding that sometimes it's a full kernel restart, and sometimes only Gnome has restarted.

---

### Post by bbukh on 2006-09-19
Can you be more specific? How do you tell one from the other?

I start to doubt whether the "exiting on signal 15" has anything to do with it. It seems reasonable behavior for log rotation: shut the logger, rotate the logs, and start it again. 

-Boris

---

### Post by endlesssnowfall on 2006-09-20
Sometimes, when I come back to my computer, it is as if my session has been logged off, and I am at the GDM screen again.  I know it is not a full kernel restart because I am not asked for my WPA password.

I'm not sure what this "signal 15" has to do with anything either, but fortuntately, this problem has not been occuring for me as of late.

---

### Post by bbukh on 2006-09-21
Today it happened again. This time things get so bad that oom-killer (a kernel program that kills processes when there is not enough memory; for information, I have 512Mb of physical RAM and 500Mb of swap space) was invoked by the kernel. 

This time it was around 5am.

Anyone has any idea of what it might be?

--Boris

---

### Post by bbface on 2006-09-27
disable the 7:30 invoke anacron solved the problem.

---

### Post by bbukh on 2006-09-29
It is not a solution. By disabling anacron you turn off daily (and weekly) maintenance tasks such as log rotation. This might cause problems later on.

Moreover, the root of the problem seems to be not in the cron jobs, but in something else. However, this sporadic bug is essentially impossible to trace.

-Boris

---

### Post by mnewton@eou.edu on 2006-10-09
This is my first time posting so be gentle with me.  I have the same problem, expect mine seems to only restart the gnome.  I know this because I've watched it do it several times.  Here is the snippit from the /var/log/syslog file:
Oct  6 15:17:01 localhost /USR/SBIN/CRON[14469]: (root) CMD (   run-parts --report /etc/cron.hourly)
Oct  6 15:40:04 localhost -- MARK --
Oct  6 16:00:04 localhost -- MARK --
Oct  6 16:13:03 localhost gconfd (jclever-14308): Received signal 15, shutting down cleanly
Oct  6 16:13:03 localhost gdm[11063]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Oct  6 16:13:03 localhost gconfd (jclever-14308): Exiting
Oct  6 16:13:05 localhost kernel: [4644781.142000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct  6 16:13:05 localhost kernel: [4644781.142000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct  6 16:13:05 localhost kernel: [4644781.142000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Oct  6 16:13:06 localhost kernel: [4644781.753000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct  6 16:13:06 localhost kernel: [4644781.753000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct  6 16:13:06 localhost kernel: [4644781.753000] ag

I'm not sure what's going on, but I do see a cron job executing just before the gdm restarts.  The machine in question is running Breezey and is used as a presentation machine.  This means it has a dual monitor video card and one goes to an lcd for the desktop and the other goes to a projector.  This machine has been in my lab running this version for almost one year, but only recently has been showing this problem.  I'm kinda stumped here.  Any help would be great.
Thanks!!!

---

### Post by bbukh on 2006-10-15
For completely mysterious reason the problem disappeared about a week and a half ago. I have absolutely no idea why.

-Boris

---

### Post by Grey on 2006-10-17
It's still present for my girlfriend.  She has X crash routinely, once per day.  And it seems to be related to a cron job of some sort.  In desperation, I even upgraded to Edgy, with no effect.

I am seriously considering a reformat, and starting over again.  It wouldn't take THAT long, but it would still be a pain in the butt.  But before I do that, does anyone have any better ideas?  Other than to disable anacron?  Has ANYONE solved this problem?

---

### Post by demijohn on 2006-11-16
First time posting (be gentle) --

I never had this problem on Breezy but have been struggling with
it since going to 6.10 Edgy.  I don't believe it has anything to
do with syslog rotation (as has been previously stated) ... the
'restart' refers to normal restart of the syslog daemon.

I'm not sure it has anything to do with a cron job either, at least
I can't correlate it with any on my sys.

Has anyone seen any correlation (possibly) with gnome screensaver?
I was getting nightly restarts of my gdm session ... until I disabled
the screen saver (2 nights ago -- I previously had it on random ...
changed it to "Blank") and no restarts.  On a whim, while working, I
re-enabled it hoping to catch a crash, stepped away for a bit and
-Poof-! down she went.  

Of course I still have cron (anacron) enabled and some jobs were 
running but there were several minutes between the jobs and the
gdm restart.  Here's output from my auth.log, daemon.log and syslog
files that show the crash.
Anyone see anything I don't?
> 

  A U T H . L O G

/var/log/auth.log:Nov 16 15:40:01 tingy CRON[16604]: (pam_unix) session opened for user smmsp by (uid=0)
/var/log/auth.log:Nov 16 15:40:02 tingy CRON[16604]: (pam_unix) session closed for user smmsp
/var/log/auth.log:Nov 16 15:48:29 tingy gdm[23611]: (pam_unix) session closed for user moorejd

  D A E M O N . L O G

/var/log/daemon.log:Nov 16 14:32:56 tingy gdm[3898]: Handling user message: 'CLOSE'
/var/log/daemon.log:Nov 16 15:48:27 tingy gdm[3898]: Handling message: 'XPID 23611 0'
/var/log/daemon.log:Nov 16 15:48:27 tingy gdm[3898]: Got XPID == 0
/var/log/daemon.log:Nov 16 15:48:27 tingy gdm[3898]: Handling message: 'SESSPID 23611 0'
/var/log/daemon.log:Nov 16 15:48:27 tingy gdm[3898]: Got SESSPID == 0
/var/log/daemon.log:Nov 16 15:48:28 tingy gdm[23611]: slave_waitpid: done_waiting
/var/log/daemon.log:Nov 16 15:48:28 tingy gdm[23611]: Session: start_time: 1163518495 end_time: 1163710108
/var/log/daemon.log:Nov 16 15:48:28 tingy gdm[23611]: Sending SESSPID == 0 for slave 23611
/var/log/daemon.log:Nov 16 15:48:28 tingy gdm[3898]: Handling message: 'SESSPID 23611 0'
/var/log/daemon.log:Nov 16 15:48:28 tingy gdm[3898]: Got SESSPID == 0
/var/log/daemon.log:Nov 16 15:48:28 tingy gdm[23611]: gdm_slave_session_stop: moorejd on :0
/var/log/daemon.log:Nov 16 15:48:28 tingy gdm[23611]: [COLOR="Red"]Fatal X error detected.  Ignoring same during session shut down.[/COLOR]
/var/log/daemon.log:Nov 16 15:48:28 tingy gdm[23611]: gdm_slave_session_stop: back here from xioerror
/var/log/daemon.log:Nov 16 15:48:28 tingy gdm[23611]: gdm_slave_session_stop: Running post session script
/var/log/daemon.log:Nov 16 15:48:29 tingy gdm[23611]: gdm_auth_user_remove: Removing cookie from /home/moorejd/.Xauthority (0)
/var/log/daemon.log:Nov 16 15:48:29 tingy gdm[23611]: gdm_auth_purge: :0
/var/log/daemon.log:Nov 16 15:48:29 tingy gdm[23611]: Running gdm_verify_cleanup and pamh != NULL
/var/log/daemon.log:Nov 16 15:48:29 tingy gdm[23611]: Running pam_close_session
/var/log/daemon.log:Nov 16 15:48:29 tingy gdm[23611]: Running pam_setcred with PAM_DELETE_CRED
/var/log/daemon.log:Nov 16 15:48:29 tingy gdm[23611]: gdm_slave_session_start: Session ended OK (now all finished)

  S Y S L O G

/var/log/syslog:Nov 16 15:40:01 tingy /USR/SBIN/CRON[16605]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
/var/log/syslog:Nov 16 15:48:27 tingy gdm[3898]: Handling message: 'XPID 23611 0'
/var/log/syslog:Nov 16 15:48:27 tingy gdm[3898]: Got XPID == 0
/var/log/syslog:Nov 16 15:48:27 tingy gdm[3898]: Handling message: 'SESSPID 23611 0'
/var/log/syslog:Nov 16 15:48:28 tingy gdm[3898]: Got SESSPID == 0
/var/log/syslog:Nov 16 15:48:28 tingy gdm[23611]: gdm_slave_session_stop: moorejd on :0
/var/log/syslog:Nov 16 15:48:28 tingy gdm[23611]: [COLOR="Red"]Fatal X error detected.  Ignoring same during session shut down.[/COLOR]
/var/log/syslog:Nov 16 15:48:28 tingy gdm[23611]: gdm_slave_session_stop: back here from xioerror
/var/log/syslog:Nov 16 15:48:28 tingy gdm[23611]: gdm_slave_session_stop: Running post session script
/var/log/syslog:Nov 16 15:48:29 tingy gdm[23611]: gdm_auth_user_remove: Removing cookie from /home/moorejd/.Xauthority (0)
/var/log/syslog:Nov 16 15:48:29 tingy gdm[23611]: gdm_auth_purge: :0
/var/log/syslog:Nov 16 15:48:29 tingy gdm[23611]: Running gdm_verify_cleanup and pamh != NULL
/var/log/syslog:Nov 16 15:48:29 tingy gdm[23611]: Running pam_close_session
/var/log/syslog:Nov 16 15:48:29 tingy gdm[23611]: Running pam_setcred with PAM_DELETE_CRED
/var/log/syslog:Nov 16 15:48:29 tingy gdm[23611]: gdm_slave_session_start: Session ended OK (now all finished)


  Does ANYONE have ANY suggestions for getting gdm to give up an answer
as to WHY it's crashing?  ](*,)

---

### Post by Pragmatist on 2006-11-17
Have you tried upgrading to the latest version of gdm?

---

### Post by demijohn on 2006-11-17
Already at latest stable ... gdm-2.16.1 (running Ubuntu 6.10 Edgy Eft)

Left screensaver enabled last night and gdm crased with xioerror at
20:34 (EST) last night.

I'm going to leave screensaver disabled this weekend and see if
my x session survives.

---

### Post by demijohn on 2006-11-20
Hmm...OK, my X session managed to survive the weekend.
Anyone else think it might be related to a screen-hack gone
awry?

:-k

---

### Post by sailor2001 on 2006-11-20
do you have a cpu desklet installed to watch it? I increased the ram to 1gig and never had anymore problems..

---

### Post by demijohn on 2006-11-20
Assuming your reply is for me ...

What (g?) desklet are you referring to?  to watch *what*?  :-? 
And what would that tell me, especially if my X session
went away?

Upgrading to 1gig is not an option .. it's a work computer
with 512meg and I don't have any spare parts lying around.

Could be a memory leak in one of the screensaver hacks??
I'm grabbing at straws

Anyone scouring the bugs db to see if anything relates? I've
looked but didn't find anything promising.  This seems like
it's been a problem across several releases ... hard to believe
no one has stumbled onto an explanation let alone a fix.

---

### Post by dave_ottawa on 2006-12-21
Hi Everyone,

I am seeing this issue as well.  My experience is as follows:

My /var/log/messages shows this:

Dec 21 05:55:47 tvputer -- MARK --
Dec 21 06:15:47 tvputer -- MARK --
Dec 21 06:35:47 tvputer -- MARK --
Dec 21 06:55:48 tvputer -- MARK --
Dec 21 07:15:48 tvputer -- MARK --
[COLOR="Red"]Dec 21 07:35:33 tvputer exiting on signal 15
Dec 21 07:35:34 tvputer syslogd 1.4.1#18ubuntu6: restart.[/COLOR]
Dec 21 07:55:34 tvputer -- MARK --
[COLOR="Red"]Dec 21 08:11:15 tvputer syslogd 1.4.1#18ubuntu6: restart.[/COLOR]  <------------------------------------ mysqld_safe starts at the same time!
Dec 21 08:11:15 tvputer kernel: Inspecting /boot/System.map-2.6.17-10-generic
Dec 21 08:11:15 tvputer kernel: Loaded 22826 symbols from /boot/System.map-2.6.17-10-generic.
Dec 21 08:11:15 tvputer kernel: Symbols match kernel version 2.6.17.
Dec 21 08:11:15 tvputer kernel: No module symbols loaded - kernel modules not enabled. 


The times at which this happens seems to be random.  I thought at first it was related to the time when people were posting it was around 7:30 but now it seems to be later in the morning.  I've disabled my screen saver as one person suggested but it still seems to be restarting.   One thing I have noticed is that /var/log/daemon.log is starting mysqld_safe at the same time the restart occurs:

[COLOR="Red"]Dec 21 08:11:18 tvputer mysqld_safe[4253]: started[/COLOR]   <------------------------------------------- System restarts at the same time
Dec 21 08:11:18 tvputer mysqld[4256]: 061221  8:11:18  InnoDB: Started; log sequence number 0 43655
Dec 21 08:11:18 tvputer mysqld[4256]: 061221  8:11:18 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
Dec 21 08:11:18 tvputer mysqld[4256]: 061221  8:11:18 [Note] Starting crash recovery...
Dec 21 08:11:18 tvputer mysqld[4256]: 061221  8:11:18 [Note] Crash recovery finished.
Dec 21 08:11:18 tvputer mysqld[4256]: 061221  8:11:18 [Note] /usr/sbin/mysqld: ready for connections.
Dec 21 08:11:18 tvputer mysqld[4256]: Version: '5.0.24a-Debian_9-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution


Has anyone else seen this.  I've uninstalled mysql-server to see if the problem goes away.

Cheers,
Dave

---

### Post by boulderbum on 2007-01-09
Well gang, seems I have run into a similar problem with ubuntu 6.06 Dapper and 6.10 Edgy.

Jan  9 07:31:28 kuma exiting on signal 15
Jan  9 07:31:29 kuma syslogd 1.4.1#17ubuntu7: restart.
Jan  9 07:51:29 kuma -- MARK --
Jan  9 08:11:30 kuma -- MARK --

With similar behavior as you all are describing (Gnome restarts, System freeze in the night, etc)  However, I have also discovered that I have bad memory.  I noticed that ubuntu installs a bootable version of memtest86+ (not sure what the plus is about), which I had used at my old job with great success.  Anyway, I have bad memory.  Now this is with a new Shuttle XPC P4 2G RAM, yadda yadda.... I never had this issue with Dapper on my old Dell Precision 410 - 400 MHz PC.  Maybe the system was too damn slow to trigger the bugs, or maybe this bug is related to some newer technology in PC's these days... Odin and Olypus both know there is a big gap between my two machines...  I'm going to debug the memory issue, then see if this is still a problem.  I certainly don't see turning off cron as a valid option.

That's my two pesos... keep the info flowing, we'll find a solution eventually.

-Boulder Bum (stranded on the unclimbable Rock)

---

### Post by dimbulb1024 on 2007-02-16
To those of you on page 1 and 2 of this thread ...

I have been noticing the same thing on my computer for the last few days. What was interesting to me today was - within minutes of the background reboot I was notified of updates available for my system. Like you, my computer doesn't actually reboot and I am thinking it has something to do with the system checking itself for possible updates.

Well, sounds good to me.

---

### Post by mnorayr on 2007-02-16
Hi, I have the same problem on two Edgy machines, Thinkpad with 2GB ram and a dell PC with 1 GB. 
 
 Has anyone found a solution?

---

### Post by zds2 on 2007-02-18
FWIW I just was looking through my logs, saw the same message, thought WTF and that's what directed to this thread.  

This is nothing to be worried about, this is just syslogd restarting (hence the log message  [COLOR="Red"]syslogd[/COLOR] 1.4.1#18ubuntu6: restart).  Which is what occurs when 
/etc/init.d/sysklogd reload-or-restart > /dev/null is called at the end of /etc/cron.daily/sysklogd


-Z

---

### Post by n0mer on 2007-02-20
Cross-reference to the same problem: [http://ubuntuforums.org/showthread.php?p=2183204#post2183204](http://ubuntuforums.org/showthread.php?p=2183204#post2183204)

---

### Post by mcartmel on 2007-02-25
Hi, I am getting this problem as well where Apache2 restarts at the same time as the syslogd restart message appears. Does anyone have a solution to this?

---

### Post by theQmaster on 2008-01-02
So anyone got a verdict on what's happening at 7:35am and why, is Ubuntu Doomed  at that time ?

```

Jan  2 07:02:01 srv /USR/SBIN/CRON[25919]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Jan  2 07:15:01 srv /USR/SBIN/CRON[26644]: (root) CMD (/usr/local/awstats/tools/awstats_updateall.pl now >> /var/log/awstats.log)
Jan  2 07:17:01 srv /USR/SBIN/CRON[26653]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan  2 07:30:01 srv /USR/SBIN/CRON[26673]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Jan  2 07:30:01 srv anacron[26697]: Anacron 2.3 started on 2008-01-02
Jan  2 07:30:01 srv anacron[26697]: Will run job `cron.daily' in 5 min.
Jan  2 07:30:01 srv anacron[26697]: Jobs will be executed sequentially
Jan  2 07:35:01 srv anacron[26697]: Job `cron.daily' started
Jan  2 07:35:01 srv anacron[26710]: Updated timestamp for job `cron.daily' to 2008-01-02
Jan  2 07:35:08 srv exiting on signal 15
```

---

### Post by MJN on 2008-01-03
As I explained in your other thread your system is not restarting - what makes you think it is? Read the log - it is *syslogd* that is restarting and it needs to do this in order to rotate the logs. The 7:35am is the time your system is configured to execute its daily cron jobs - see /etc/crontab.
 
Mathew

---

### Post by julipanno on 2008-03-07
I suddenly started having the same issues as described in this thread a few days ago; a daily crash at around 7:30 in the morning. This was a crash of the X server; no input or output was possible, which left the machine running but inoperable. My log files showed no related errors, but the last report was from cron starting. I assumed, like others that have posted here, that some cron job was involved, and started running the different scripts in /etc/cron.daily/ as root. After running the script called [FONT="Courier New"]find.notslocate[/FONT] the symptoms were revealed. The next script to run returned an I/O error immediately and I noticed that my root partition had been remounted as read-only, something it should do whenever there's a serious error with the file system. Looking at the contents of the script, it seems that its main purpose is to update the database that the file locating utility [FONT="Courier New"]locate[/FONT] uses, and it does so by reading every file on the harddisk. The crash of X was therefore most likely due to [FONT="Courier New"]updatedb[/FONT] discovering a seriously damaged file and promptly commanding a read-only-fication of the system. This also explained why there were no errors in the log files; they couldn't be written to the disk.

To fix a filesystem error on the root partition, you would have to run [FONT="Courier New"]fsck[/FONT], the file system checking utility, from either a Live-CD or an operating system on a different partition. The root partition (that you wish to fix) has to be unmounted. I ran [FONT="Courier New"]fsck[/FONT] with the badblocks (read/write) option -cc (as well as the force option -f), like this:
```
fsck /dev/hda1 -ccf
```
and, after three hours of block scanning, followed by a few hundred questions on whether I wanted to repair this and that (which you can skip by including the yes option -y), I could again use my Ubuntu installation as normal, even after doing a test run of [FONT="Courier New"]updatedb[/FONT].

---

### Post by Nevell on 2008-05-19
So, anyone fix this problem? Maybe its not a error?

*/var/log/messages*
> Apr 21 06:25:12 server exiting on signal 15
Apr 22 06:27:16 server exiting on signal 15
Apr 23 06:27:32 server exiting on signal 15
...
May 12 06:25:10 server exiting on signal 15
May 13 06:25:23 server exiting on signal 15
May 14 06:27:47 server exiting on signal 15
May 15 06:27:48 server exiting on signal 15
May 16 06:27:44 server exiting on signal 15
May 17 06:27:42 server exiting on signal 15
May 18 06:26:13 server exiting on signal 15
May 18 06:47:01 server exiting on signal 15

*/var/log/syslog*
> May 11 06:47:02 server exiting on signal 15
May 12 06:25:10 server exiting on signal 15
May 13 06:25:23 server exiting on signal 15
...
May 18 06:26:13 server exiting on signal 15
May 18 06:47:01 server exiting on signal 15

The same time on the every day. My time is GTM +3:00 (Moscow time). 

**P.S.** What is the -- MARK -- ?
> May 18 06:47:02 server syslogd 1.4.1#17ubuntu7: restart.
May 18 07:07:03 server -- MARK --
May 18 07:27:03 server -- MARK --
May 18 07:47:03 server -- MARK --
...
May 19 09:47:25 server -- MARK --
May 19 10:07:25 server -- MARK --
May 19 10:28:23 server syslogd 1.4.1#17ubuntu7: restart.

**P.P.S.** Ubuntu 6.06.01 LTS server

---

### Post by MJN on 2008-05-19
Nevell, please see my response to your duplicate post [here](http://ubuntuforums.org/showthread.php?p=4994189#post4994189).
 
Unless you are observing failures other than what look like system restarts in your logs then all you are probably seeing are syslog dameon restarts.
 
Mathew

---

