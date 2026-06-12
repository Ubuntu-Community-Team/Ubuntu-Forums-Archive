---
title: "RAID1, what just happend?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2008-03-29
I was logged in, (actually working on my smb.conf) and I noticed that there was no /media/md3/shares. In fact there was no /media/md3. And ls /media reported that there were several sda1, sda2 etc. But no sdb* at all. First thought that popped into my head was " WHAT THE  F&$K, These are new disks!". But I restarted ubuntu holding my breath until it came back up. I then sighed relief when /media/md3 was back.

What just happend?

How can I better monitor these disks? Any handy apps for RAID monitoring?

I was under the impression that some pop up window would jump out at me and tell me a disk failed. Is this not true?

Thanks

Tony

Also, this isn't an "Absolute Beginner Question" but I couldn't find a better place to post. There should be an intermediate or advanced section.

---

### Post by DBrocks on 2008-03-29
Well, I've done some poking around. It seems like there are loads of apps for monitoring RAID software, but nothing for hardware. I'll keep you posted though!

---

### Post by ant2ne on 2008-03-29
This IS a software RAID set up.

---

### Post by DBrocks on 2008-03-29
Oh, sorry. Try using mdadm

---

### Post by dsauxier on 2008-03-29
Here's a script I use (this has a little more than just raid monitoring in it : 

I have this running in the root crontab : 
```

crontab -l 
45 16 * * * /sysadm/status_rpt.sh

```

The status_rpt.sh looks like this (note the commented lines... it turns out that was generating way more detail than I was interested in) : 
```

outputfile="/sysadm/status_rpt.log"
echo "STATUS OF RAID SET(s) : " > $outputfile
cat /proc/mdstat >> $outputfile
# echo "REPORT OF mdadm --detail /dev/md0 : ">> $outputfile
# mdadm --detail /dev/md0 >> $outputfile
echo "STATUS OF MEMORY (and swap) USAGE : " >> $outputfile
free >> $outputfile

echo "FILESYSTEM STATUS : " >> $outputfile
df -h | grep -v tmpfs | grep -v "/boot" | grep -v "/ubuntu" >> $outputfile

/sysadm/mailtxt.sh "somaddress@cox.net,somaddress@gmail.com" "Linux Server Status Report" /sysadm/status_rpt.log

```

The mailtxt.sh script.
```

# Parameters :
# 1 - To
# 2 - Subject
# 3 - File to send
FROM="user@place.org"
REPLYTO="user@place.org"
ERRORSTO="user@place.org"
SENDTO="$1"
SUBJECT="$2"
SENDFILE="$3"
(echo "From: $FROM
To: $SENDTO
Subject: $SUBJECT
Reply-To: $REPLYTO
Errors-To: $ERRORSTO"; cat $SENDFILE) | /usr/sbin/sendmail -olTrue -t $SENDTO

```

Sample output : 
I've bolded the important parts to look at.
There are actually two mirrors here, md0 and md1.
Each of those has a line with a "UU" in it (I've added the bolding for this post). There are exactly 2 "U's" because there are exactly 2 disks in the raid set.  If it were a raid set with 3 disks, it would be [UUU].
Anyway, if you ever see an underscore in place of a U then one of your disks is bad.  This has happened a few time to me and so far I've been able to successfully rebuild.
I'll post instructions on that in a followup post (If you have to rebuild, you must take great care because specifying the wrong one to destroy will kill the only good copy of your data).
Also, my memory is hazy on this, but I think the "active" line will say something like "failed" or "failure" if this happens too. ```

STATUS OF RAID SET(s) : 
Personalities : [raid1] 
md1 :** active** raid1 sda3[0] sdb3[1]
      70308352 blocks [2/2] **[UU]**
      
md0 :** active **raid1 sda1[0] sdb1[1]
      6835520 blocks [2/2] **[UU]**
      
unused devices: <none>
STATUS OF MEMORY (and swap) USAGE : 
             total       used       free     shared    buffers     cached
Mem:        766460     760308       6152          0       5672     622216
-/+ buffers/cache:     132420     634040
Swap:      1959912     106420    1853492
FILESYSTEM STATUS : 
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              6.5G  4.6G  1.6G  75% /
varrun                375M  560K  374M   1% /var/run
varlock               375M  4.0K  375M   1% /var/lock
udev                  375M  100K  375M   1% /dev
devshm                375M     0  375M   0% /dev/shm
lrm                   375M   19M  356M   5% /lib/modules/2.6.15-28-386/volatile
/dev/md1               66G   50G   14G  80% /mnt/md1r1

```

---

### Post by dsauxier on 2008-03-29
This is the document that I created with instructions on fixing this problem.
I've removed the name of the nonprofit simply because I don't want to take the time to get permission to use their name.

In this example, the "bad" disk is sda - it is crucial to correctly determine which disk is bad.
Check it and then recheck it before you start to make sure you rebuild the correct one since there is nothing you can do about it if you blow away the good data.
I keep this documentation about the raid array just as a double-check for myself.
If what I find does not match up, then it's one extra red flag for me.
cat disk_failure.txt[INDENT]
INFO : (this info is as of 5/12/2007 - please verify that it has not changed)
       md0 is the 6.5GB root partition (sda1 and sdb1)
       md1 is the 66 GB data partition (sda3 and sdb3)

At the time that these notes were written,
md1 is tied to sda3 and sdb3
md0 is tied to sda1 and sdb1[/INDENT]
===============================================================
  BEGIN DOCUMENTATION
===============================================================
Let's become root for this : 
```
sudo su - root 
```
First, determine which disk has failed :
```
cat /proc/mdstat
```
[INDENT]************************ OUTPUT *****************
Personalities : [raid1]
md1 : active raid1 sda3[2](F) sdb3[1]
      70308352 blocks [2/1] [_U]

md0 : active raid1 sda1[2](F) sdb1[1]
      6835520 blocks [2/1] [_U]

unused devices: <none>
************************ END OUTPUT *****************
[/INDENT]
This tells me that sda is the failed disk
It also tells me that md0 is tied to sda1 and md1 is tied to sda3
(this will be important later)

mdadm --detail /dev/md1
provides more detailed information, corroborates what /proc/mdstat told you

This is how to rebuild the array (assuming the disk is not physically bad)...
BE SURE to

   1. VERIFY which disk(s) you want to remove from the array... removing the wrong one means ALL DATA WILL BE LOST!
   2. Do the Adds exactly in the order below
   3. I USED MDADM TO CREATE THE ARRAY IN THE FIRST PLACE.  IF YOU USED SOMETHING ELSE, YOU PROBABLY DON'T WANT TO USE THESE INSTRUCTIONS
   4. THIS IS A MIRRORED SET WITH NO HOT-SPARE.  IF YOUR CONFIGURATION IS DIFFERENT, YOU MAY HAVE TO MODIFY THE STEPS

(md0 is smaller, so it should be first, it only takes a few minutes... the other will take over an hour)

# BEGIN FIX
# Remove the bad disk from the raid groups (this is a destructive action - be SURE you're removing the disk that's marked as bad) :
```
mdadm -r /dev/md0 /dev/sda1
mdadm -r /dev/md1 /dev/sda3
```

# Add the disk back into the raid groups :
```
mdadm -a /dev/md0 /dev/sda1
```
#NOW WAIT FOR THIS TO FINISH (monitor by doing: cat /proc/mdstat )
```
mdadm -a /dev/md1 /dev/sda3
```
# END FIX

ADDITIONAL NOTES : [http://tldp.org/HOWTO/Software-RAID-HOWTO-8.html](http://tldp.org/HOWTO/Software-RAID-HOWTO-8.html)

---

### Post by ant2ne on 2008-03-29
Great info, thanks!

That is an awesome script. I will probably use it. Did you write it? I don't notice an if/then so I assume it e-mails you periodically with the drive(s) status regardless if it is up or down. I wonder if I can tweak it to e-mail only on a down drive. Cool either way.

I set up the software RAID using these instructions here [http://advosys.ca/viewpoints/2007/0/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/0/setting-up-software-raid-in-ubuntu-server/) and it does discuss techniques on how to recover a failed drive.

Is there anyway to figure out exactly what happened? Why I lost the RAID drives in the first place?

---

### Post by dsauxier on 2008-03-30
Thanks for the kudos.
Yes, I did write it myself.  And yes, it does e-mail me every day regardless.
Sticking an if condition in there is a good idea, but I chose not to because there is the possiblity that the e-mail doesn't make it to me for whatever reason. ISP marks it as SPAM / server down (though I'd find out about that with a phone call).
Anyway, it's really easy to glance at the UU part and just delete the e-mail.

A check could be added to the script so that it puts a status indication in the subject line "STATUS GOOD" vs "RAID FAILURE" or something and then we'd both be served well.

If you do modify the script, (wethor or not you use the status indicator I suggested) then I would appreciate it very much if you'd post your changes... I would likely incorporate them in some fashion into my version.

As far as the source of the errors, I haven't found any good reason for it happening.  At first I took it as a sign that the drive might be going bad.  After the 2nd time that it happened, I bought a new drive to have on hand for quick replacement (we never installed the new drive).  That was about a year ago and it has not happened since. (now that I say that it wil fail tonight)

I also set up a software raid (raid5 this time) for a buddy of mine that has his own single-employee business.  The same thing happened to him, but only once (I advised that he replace the drive since it was still under warranty).  Eventually he went to hardware raid.

---

### Post by dsauxier on 2008-03-31
I work with a sysadm (Thom Harrison) who already modified my script for a project he was working on (his script is much better than mine, but I can write better Oracle scripts, so take that, Thom :) ) 

You'll notice that he keeps email and pager information in a file.
 
```

#!/bin/sh
#^^^^^^^^-------------------------------------- Defines the shell.  Never use csh!
#=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
# These security measures are primarily to help protect an SUID Shell Script.  However,
#    it's a good idea to use them anyway in case a scripts is given SUID rights later.
#    If at all possible, avoid SUID Shell Scripts altogether.  Even with the steps taken
#    below, most Scripts are hackable.
#
#    You should use either:
#
#        1) a wrapper written in C,
#        2) a Perl Script
#   -or- 3) a program like sudo
#
#=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
#---------------------------------------------- Specify any directories needed
PATH='/bin:/usr/bin'
#---------------------------------------------- Prevents a / as being the cmd separator
IFS=' '
#---------------------------------------------- Define an exact number of parms
PARMS=0
#---------------------------------------------- Exit if the actual parms do not match
if [ $# != $PARMS ]
then
   echo Incorrect number of parameters. There should a total of $PARMS
   exit 1
fi
#=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
# Configurable Variables
#=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
MIRRORS=4
 
EMAILFILE="/sysadm/emails/sysadm.email"
PAGERFILE="/sysadm/emails/sysadm.pager"
#=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
read -r EMAIL < $EMAILFILE
read -r PAGER < $PAGERFILE
 
UUcount=`cat /proc/mdstat | grep \[UU\] | wc -l`
if [ ${UUcount} -eq ${MIRRORS} ]
then        # All is well
   exit 0;
else        # Problems
   echo "RAID ${UUcount} of $MIRRORS on `hostname`" | mailx -s "`hostname` RAID problem" $PAGER
   HIGHESTMIRROR=`echo $MIRRORS-1|bc`
   for i in 0 1 2 3
   do
     echo "md${i}"
     /sbin/mdadm --detail /dev/md${i}
     echo
     echo
   done | mailx -s "`hostname` RAID problem" $EMAIL
fi

```

---

