---
title: "Cron problems"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Mortuis on 2005-12-20
Does crond run out of the box?  I logged in under my user account and typed:
crontab -e

and in the editor I added the line:
59 11 * * 1-7 wget [http://url/file](http://url/file)

I ran crontab -l afterwards to verify that the line was saved, but it didn't run last night. I don't see crond as a running process.

Is there something I'm supposed to do to get crond to start?  Is there a way I can get it to start on bootup?

---

### Post by amohanty on 2005-12-20
System->Administration->BootUp Manager
check cron in the list of services that comes up.

HTH
AM

---

### Post by ertai on 2005-12-20
Doesn't cron use 0-6 to point to the day's??

I would make the cron-line

59 11 * * * wget [http://url/file](http://url/file)

that should also run the command every day

---

### Post by amohanty on 2005-12-20
> Doesn't cron use 0-6 to point to the day's??

From the crontab [manual]("http://unixhelp.ed.ac.uk/CGI/man-cgi?crontab+5")

> The time and date fields are:

	      field	     allowed values
	      -----	     --------------
	      minute	     0-59
	      hour	     0-23
	      day of month   1-31
	      month	     1-12 (or names, see below)
	      day of week    0-7 (0 or 7 is Sun, or use names)

       A field may be an asterisk (*), which always stands for ``first-last''.

       Ranges of numbers are allowed.  Ranges are two numbers separated with a
       hyphen.	 The  specified	 range is inclusive.  For example, 8-11 for an
       ``hours'' entry specifies execution at hours 8, 9, 10 and 11.

       Lists are allowed.  A list is a set of numbers (or ranges) separated by
       commas.	Examples: ``1,2,5,9'', ``0-4,8-12''.

       Step  values can be used in conjunction with ranges.  Following a range
       with ``/<number>'' specifies skips of the number's  value  through  the
       range.  For example, ``0-23/2'' can be used in the hours field to spec-
       ify command execution every other hour (the alternative in the V7 stan-
       dard  is ``0,2,4,6,8,10,12,14,16,18,20,22'').  Steps are also permitted
       after an asterisk, so if you want to say ``every two hours'', just  use
       ``*/2''.

So I guess 1-7 _would_ be ok, however I think goin ertai's way would be wise...

AM

---

### Post by Mortuis on 2005-12-21
[QUOTE=amohanty]System->Administration->BootUp Manager
check cron in the list of services that comes up.

HTH
AM[/QUOTE]
I'm sorry, I neglected to mention I'm running Ubuntu Server, and don't have a graphical environment.  How would I check for this on the command line?

I tried using google, but I can only find vague inforamation about doing something called linking files in /etc/init.d/, or modifying /etc/inittab.  Looking in /etc/init.d/ shows me what look like a bunch of file pointers, I'm not sure.  Looking at the contents of /etc/inittab didn't show me anything that looked like it had to do with cron.  This is all a little above me.


In the meantime, I switched the crontab to be 
59 11 * * * wget [http://url/file](http://url/file)
as suggested.

Thanks for the help so far.

---

### Post by patrick295767 on 2005-12-21
I got too troubles with cron ....
I installed kcron
```
apt-get -f install kcron
```
  And make & set it easily with this kcron
  
then, I went in /etc/crontab
and added the root between time and the script to start 
(like lines above)...

---

### Post by patrick295767 on 2005-12-21
(It is working perfectly this way in my case)

---

### Post by amohanty on 2005-12-21
> I'm sorry, I neglected to mention I'm running Ubuntu Server, and don't have a graphical environment. How would I check for this on the command line?

I have not used kcron, so cant say how that works. But the easiest way to make sure that cron fires up is to to use the sysv-rc-conf tool.

Install it via:
> sudo apt-get install sysv-rc-conf

thenfire it up and mark an x in front of it for runlevels 2-6.

HTH
AM

---

### Post by bscbrit on 2005-12-21
Perhaps an easier way to do it, in keeping with Ubuntu's current methodology, is to use the /etc/cron* directories.

In Ubuntu, crontab is reponsible for calling each of the scripts in cron.hourly, cron.daily or cron.weekly as appropriate.

In this case, a simple script in cron.daily (making sure that you make it executable!) will be called at the time that the cron.daily scripts are actioned.

Ubuntu specifically says that running crontab is not required and, in my case, it cocked up the entire cron system.  Similar, I suspect, to what you are now seeing.
I would remove any personal crontabs that you have created and rely on the sytem version in /etc/crontab.

---

### Post by cwaldbieser on 2005-12-21
[QUOTE=Mortuis]Does crond run out of the box?  I logged in under my user account and typed:
crontab -e

and in the editor I added the line:
59 11 * * 1-7 wget [http://url/file](http://url/file)

I ran crontab -l afterwards to verify that the line was saved, but it didn't run last night. I don't see crond as a running process.

Is there something I'm supposed to do to get crond to start?  Is there a way I can get it to start on bootup?[/QUOTE]

Could it be that you set it to run slightly before noon, rather than slightly before midnight?

---

### Post by patrick295767 on 2005-12-22
My crontab:

```
 This file also has a username field, that none of the other crontabs do.
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h dom mon dow user	command
17 * * * *	root	run-parts --report /etc/cron.hourly
# 
25 6 * * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
# 
47 6 * * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
# 
52 6 1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
# Please be informed tthat I am stopping gdm
0,30,55 0,23 * * *	          root	/etc/init.d/gdm	stop
# I start the gdm
0 2,3,4 * * *	root	/etc/init.d/gdm	start
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.
```   working !

---

