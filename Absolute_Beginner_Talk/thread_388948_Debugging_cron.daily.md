---
title: "Debugging cron.daily"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by ssn on 2007-03-20
Hi,

I'm trying to run a daily script on a Ubuntu Edgy box but it is not working.

I created a script in /etc/cron.daily. The script runs without problems if I call it directly, either as root or as a user. Nevertheless, it is not being run daily like the other scripts at /etc/cron.daily are.

```

#ls -lut /etc/cron.daily

-rwxr-xr-x 1 root root 1924 2007-03-20 10:03 backup.cron
-rwxr-xr-x 1 root root  383 2007-03-20 09:48 samba
-rwxr-xr-x 1 root root 1307 2007-03-20 07:35 sysklogd
-rwxr-xr-x 1 root root  766 2007-03-20 07:35 tetex-bin
-rwxr-xr-x 1 root root 5566 2007-03-20 07:35 apt
-rwxr-xr-x 1 root root  314 2007-03-20 07:35 aptitude
-rwxr-xr-x 1 root root  502 2007-03-20 07:35 bsdmainutils
-rwxr-xr-x 1 root root   89 2007-03-20 07:35 logrotate
-rwxr-xr-x 1 root root  946 2007-03-20 07:35 man-db
-rwxr-xr-x 1 root root  189 2007-03-20 07:35 slocate
-rwxr-xr-x 1 root root 3227 2007-03-20 07:35 standard
-rwxr-xr-x 1 root root  311 2007-03-20 07:35 0anacron
-rwxr-xr-x 1 root root  191 2007-03-20 07:35 apport
-rwxr-xr-x 1 root root  419 2007-02-13 17:23 find.notslocate.dpkg-new
-rwxr-xr-x 1 root root  419 2006-03-20 06:25 find.notslocate

```

My script is the "backup.cron", and it was manually run.

I would like to know what's the problem but I don't get any error messages.
Where can I find more information to start debugging this? Where to look?

Thanks in advance for any help!

---

### Post by kidders on 2007-03-20
Hi there,

If you post your script, there may be something obvious going on that I (or someone else) may spot quickly. Otherwise, liberal redirection of debug output to a temporary file would be an easy way of establishing where things start to go wrong.

---

### Post by ssn on 2007-03-20
Thanks for your answer.
Please note that I am able to run the script from the shell without problems, both as root and as 'user'.
Nevertheless, I present below the contents of the script I'm using:

```

#!/bin/sh
# full and incremental backup script
# created 07 February 2000
# Based on a script by Daniel O'Callaghan <danny@freebsd.org>
# and modified by Gerhard Mourani <gmourani@videotron.ca>

#Change the 5 variables below to fit your computer/backup

COMPUTER=olivia                                 # name of this computer
DIRECTORIES="/home"                             # directoris to backup
BACKUPDIR=/backups/olivia                       # where to store the backups
TIMEDIR=/backups/olivia/last-full               # where to store time of full backup
TAR=/bin/tar                                    # name and locaction of tar

#You should not have to change anything below here

PATH=/usr/local/bin:/usr/bin:/bin
DOW=`date +%a`                          # Day of the week e.g. Mon
DOM=`date +%d`                          # Date of the Month e.g. 27
DM=`date +%d%b`                 # Date and Month e.g. 27Sep

# On the 1st of the month a permanet full backup is made
# Every Sunday a full backup is made - overwriting last Sundays backup
# The rest of the time an incremental backup is made. Each incremental
# backup overwrites last weeks incremental backup of the same name.
#
# if NEWER = "", then tar backs up all files in the directories
# otherwise it backs up files newer than the NEWER date. NEWER
# gets it date from the file written every Sunday.


# Monthly full backup
if [ $DOM = "01" ]; then
        NEWER=""
        $TAR $NEWER -cf $BACKUPDIR/$COMPUTER-$DM.tar $DIRECTORIES
fi

# Weekly full backup
if [ $DOW = "Sun" ]; then
        NEWER=""
        NOW=`date +%d-%b`

        # Update full backup date
        echo $NOW > $TIMEDIR/$COMPUTER-full-date
        $TAR $NEWER -cf $BACKUPDIR/$COMPUTER-$DOW.tar $DIRECTORIES

# Make incremental backup - overwrite last weeks
else

        # Get date of last full backup
        NEWER="--newer `cat $TIMEDIR/$COMPUTER-full-date`"
        $TAR $NEWER -cf $BACKUPDIR/$COMPUTER-$DOW.tar $DIRECTORIES
fi

```

---

### Post by kidders on 2007-03-20
Hey again,

The script looks nice and clean. No problems there. :-) From your first post, I am curious about whether **run-parts** will even *attempt* to execute your script...

> If the --lsbsysinit option is not given then the names [of files] must consist entirely of upper and lower case letters, digits, underscores, and hyphens.(From the man page)

Additionally, you should check that the script is in fact executable. While checking that, you should verify that nobody but root is able to modify your script. (Write permission has nothing to do with your problem, but is worth mentioning, as it would have _disasterous_ consequences!)

---

### Post by justleen on 2007-03-20
hmhmmmmm so, what your saying (kidders), is that changing the name to backupcron (without the dot) should solve this?

---

### Post by kidders on 2007-03-20
> **justleen said:**
> hmhmmmmm so, what your saying (kidders), is that changing the name to backupcron (without the dot) should solve this?

Yeah, provided the script is executable in the first place. It's a bit of a stab in the dark, but it would certainly explain this bit ...> **ssn said:**
> I don't get any error messages.

What do you think?

**Edit:** Another issue I considered was permissions-related. I did a quick check by throwing **whoami** into a cron script, just to verify that root is in fact the user these scripts run as. (That's why I commented about write permissions before.)

---

### Post by ssn on 2007-03-21
Removing the dash in the script's name worked! "backup-cron" > "backupcron".
Would never thought of this since one of Ubuntu's default script has a dash and seems to be working just fine - "man-db".

Thanks!

---

### Post by kidders on 2007-03-21
Dashes are allowed... judging from your o/p, dots were causing your problem, I'd say.

Anyhow, glad you fixed your problem. :-)

---

### Post by ssn on 2007-03-21
Off-course, dots were the problem :)

---

