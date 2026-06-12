---
title: "crontab mistakes"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by leetcharmer on 2008-03-26
Hi, I want my script to run on the first and third week of the month:
```
[root@VMServer root]# crontab -l
# Monday's backup
0 0 1-7,15-21 * Mon /root/shutdownvm.sh 2003_Server >> /root/backup.log 2>&1
0 6 1-7,15-21 * Mon /root/startupvm.sh 2003_Server >> /root/backup.log 2>&1
# Tuesday's backup
0 0 1-7,15-21 * Tue /root/shutdownvm.sh PSK-PFX >> /root/backup.log 2>&1
0 6 1-7,15-21 * Tue /root/startupvm.sh PSK-PFX >> /root/backup.log 2>&1
# Wednesday's backup
0 0 1-7,15-21 * Wed /root/shutdownvm.sh PSK-Creative >> /root/backup.log 2>&1
0 6 1-7,15-21 * Wed /root/startupvm.sh PSK-Creative >> /root/backup.log 2>&1
# Thursday's backup
0 0 1-7,15-21 * Thu /root/shutdownvm.sh PSK-Peach >> /root/backup.log 2>&1
0 6 1-7,15-21 * Thu /root/startupvm.sh PSK-Peach >> /root/backup.log 2>&1
# Sunday's backup
0 0 1-7,15-21 * Sun /root/shutdownvm.sh PSK-QB >> /root/backup.log 2>&1
0 6 1-7,15-21 * Sun /root/startupvm.sh PSK-QB >> /root/backup.log 2>&1
```
This is my crontab.

I checked my backup.log and it says that it was executed on the 25th and 26th of March.  I want to know what I'm doing wrong, can you help me?

Thanks

---

### Post by Oldsoldier2003 on 2008-03-26
> **leetcharmer said:**
> Hi, I want my script to run on the first and third week of the month:
```
[root@VMServer root]# crontab -l
# Monday's backup
0 0 1-7,15-21 * Mon /root/shutdownvm.sh 2003_Server >> /root/backup.log 2>&1
0 6 1-7,15-21 * Mon /root/startupvm.sh 2003_Server >> /root/backup.log 2>&1
# Tuesday's backup
0 0 1-7,15-21 * Tue /root/shutdownvm.sh PSK-PFX >> /root/backup.log 2>&1
0 6 1-7,15-21 * Tue /root/startupvm.sh PSK-PFX >> /root/backup.log 2>&1
# Wednesday's backup
0 0 1-7,15-21 * Wed /root/shutdownvm.sh PSK-Creative >> /root/backup.log 2>&1
0 6 1-7,15-21 * Wed /root/startupvm.sh PSK-Creative >> /root/backup.log 2>&1
# Thursday's backup
0 0 1-7,15-21 * Thu /root/shutdownvm.sh PSK-Peach >> /root/backup.log 2>&1
0 6 1-7,15-21 * Thu /root/startupvm.sh PSK-Peach >> /root/backup.log 2>&1
# Sunday's backup
0 0 1-7,15-21 * Sun /root/shutdownvm.sh PSK-QB >> /root/backup.log 2>&1
[COLOR="DarkRed"]0 6 1-7,15-21 * Sun /root/startupvm.sh PSK-QB >> /root/backup.log 2>&1[/COLOR]
```
This is my crontab.

I checked my backup.log and it says that it was executed on the 25th and 26th of March.  I want to know what I'm doing wrong, can you help me?

Thanks
 your format is apparently confusing cron because there are errors in the format:
using the highlighted cronjob this is what you are asking cron to do:

```
at 6:00 on the 1-7th **and** the 15th-21st of each month **ON sunday** every month execute  /root/startupvm.sh PSK-QB >> /root/backup.log 2>&1
```

Part of the problem being cron my not interpret Sun as being valid input the day of the week is supposed to be passed as  0-6.


> 
*     *   *   *    *  command to be executed
-     -    -    -    -
|     |     |     |     |
|     |     |     |     +----- day of week (0 - 6) (Sunday=0)
|     |     |     +------- month (1 - 12)
|     |     +--------- day of month (1 - 31)
|     +----------- hour (0 - 23)
+------------- min (0 - 59)

---

### Post by which_chick on 2008-03-26
I found the problem.

Source:  [http://linux.die.net/man/5/crontab](http://linux.die.net/man/5/crontab)

"A field may be an asterisk (*), which always stands for "first-last".

Ranges of numbers are allowed. Ranges are two numbers separated with a hyphen. The specified range is inclusive. For example, 8-11 for an "hours" entry specifies execution at hours 8, 9, 10 and 11.

Lists are allowed. A list is a set of numbers (or ranges) separated by commas. Examples: "1,2,5,9", "0-4,8-12".

Step values can be used in conjunction with ranges. Following a range with "<number>" specifies skips of the number's value through the range. For example, "0-23/2" can be used in the hours field to specify command execution every other hour (the alternative in the V7 standard is "0,2,4,6,8,10,12,14,16,18,20,22"). Steps are also permitted after an asterisk, so if you want to say "every two hours", just use "*/2".

Names can also be used for the "month" and "day of week" fields. Use the first three letters of the particular day or month (case doesn't matter). Ranges or lists of names are not allowed.

The "sixth" field (the rest of the line) specifies the command to be run. The entire command portion of the line, up to a newline or % character, will be executed by /bin/sh or by the shell specified in the SHELL variable of the cronfile. Percent-signs (%) in the command, unless escaped with backslash (\), will be changed into newline characters, and all data after the first % will be sent to the command as standard input.

**Note: The day of a command's execution can be specified by two fields - day of month, and day of week. If both fields are restricted (ie, aren't *), the command will be run when either field matches the current time.** For example,
"30 4 1,15 * 5" would cause a command to be run at 4:30 am on the 1st and 15th of each month, plus every Friday."

Your code says the following:

0 0 1-7,15-21 * Mon /root/shutdownvm.sh 2003_Server >> /root/backup.log 2>&1
0 6 1-7,15-21 * Mon /root/startupvm.sh 2003_Server >> /root/backup.log 2>&1

Run at 0:00 and 6:00 on 1-7, 15-21, AND EVERY MONDAY

# Tuesday's backup
0 0 1-7,15-21 * Tue /root/shutdownvm.sh PSK-PFX >> /root/backup.log 2>&1
0 6 1-7,15-21 * Tue /root/startupvm.sh PSK-PFX >> /root/backup.log 2>&1

Run at 0:00 and 6:00 on 1-7, 15-21, AND EVERY TUESDAY

(etc.)

The way you have it written, the code will run every single day of the week... and it is doing so.

---

### Post by leetcharmer on 2008-03-26
So, how could I get it to do a monday within the range of the date 1-7?  Or is there another way to make sure it does the first and third monday of the month?

---

### Post by which_chick on 2008-03-26
I'd do it every day 1-7 and every day 15-21.  One of the days from 1-7 is going to be a Monday.  One of the days from 15-21 is going to be a Monday.  That should give you full coverage.

Do you *just* want it to run on Mondays?  Your original example was set to run every day of the week and I believe you intended to run every day of the 1-7 week and every day of the 15-21 week, so I didn't figure you wanted just Mondays.

If, for some reason, I wanted files named 7-Mon-Apr-08.bak  and 16-Wed-Apr-08.bak (or similar) so that I could find the "Monday" or Wednesday backup without looking through old calendars, I'd use a shell script to pull "date" and then parse it into arguments for the filenaming convention I wanted to use.  Probably I'd parse using awk -- it's not a huge job you're looking at, here.  Sed might work, too.

---

### Post by which_chick on 2008-03-26
And, if I wanted it to run JUST on the first and third mondays of the month (but that's totally not how your crontab entries were written), I would do the following.

1.  Set up the crontab to run a script every day 1-7 and 15-21, just like you have.

2.  Contents of the script FIRST THING is see-what-day-it-is.  If Monday, do backup.  If Not-Monday, do nothing.

I don't see a good way to set up crontab so that it just runs on the Monday that falls in the 1-7 date range and the Monday that falls in the 15-21 date range.

It'd be dead easy to make it do the first and the fifteenth of the month... but those would not necessarily be Mondays.

For real, I'd go with the shell-script-for-the-range and have the shell script only do stuff if it's Monday.

---

### Post by leetcharmer on 2008-03-26
> **which_chick said:**
> And, if I wanted it to run JUST on the first and third mondays of the month (but that's totally not how your crontab entries were written), I would do the following.

1.  Set up the crontab to run a script every day 1-7 and 15-21, just like you have.

2.  Contents of the script FIRST THING is see-what-day-it-is.  If Monday, do backup.  If Not-Monday, do nothing.

I don't see a good way to set up crontab so that it just runs on the Monday that falls in the 1-7 date range and the Monday that falls in the 15-21 date range.

It'd be dead easy to make it do the first and the fifteenth of the month... but those would not necessarily be Mondays.

For real, I'd go with the shell-script-for-the-range and have the shell script only do stuff if it's Monday.

Thanks, this is moreso what I'm looking for.  I'm just going to hardcore which *date* to do each one, that's prolly my easiest bet.  Thanks again!

---

