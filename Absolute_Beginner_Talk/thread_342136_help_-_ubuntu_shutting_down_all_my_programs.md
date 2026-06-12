---
title: "help - ubuntu shutting down all my programs?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Cabldevil on 2007-01-19
ok im lost.  I left work today with my new install of 6.10 running on my server with gaim xchat aMSN and firefox running.   I come home just now and when i login not one of the programs is running.  This is the 3rd day in a row.  Im confused.

I have a UPS so it snot a power outage from what i can tell.  Is it a power save setting im missing. I checked it and its set to NEVER turn puter off or go into hiber.

Any info would help im lost!
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
CD

---

### Post by bodhi.zazen on 2007-01-19
I don't understand, did you logout ?

If so, all your programs will be closed ;)

If not, Cat, Dog, Children, Woof ?

Gremlins ?

---

### Post by Cabldevil on 2007-01-20
I dont understand either I just logged back in this morning the computer was running all night and again all the programs are closed.   I dont logout  just let it go to screen saver   this is odd.  I guess I will try to change the bios to not reboot of there is a power or hardware shutdown / reboot  and see what happens.

I m lost

---

### Post by Cabldevil on 2007-01-20
Jan 20 07:40:19 server exiting on signal 15 
Jan 20 07:40:20 server syslogd 1.4.1#18ubuntu6: restart.

everyday about 7:30 to 7:40 am it looks like the system just reboots?  why would that be ?  What other log can I check ? This is message log



Ok this is from my System log  same time frame

Jan 20 07:40:20 server syslogd 1.4.1#18ubuntu6: restart.
Jan 20 07:40:20 server anacron[14838]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Jan 20 07:40:20 server anacron[14838]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jan 20 07:40:20 server anacron[14838]: Normal exit (1 job run)
Jan 20 08:00:20 server -- MARK --

Also I sure this may be nothing but I see : Jan 20 00:17:01 server CRON[14787]: (pam_unix) session opened for user root by (uid=0)
Jan 20 00:17:01 server CRON[14787]: (pam_unix) session closed for user root 
Every hour  Im sure its just a cron job running  no harm.

Anyone read into these logs?  Every day since my install at 7:30 - 7:40  it reboots

Thanks
Confused

---

### Post by old jet driver on 2007-03-21
I am seeing the same type activity.  Being very new to ubuntu I have no idea what it is doing.

Tom

---

