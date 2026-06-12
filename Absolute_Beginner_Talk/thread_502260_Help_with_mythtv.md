---
title: "Help with mythtv"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by mikeyandmary on 2007-07-16
Hi all,

I have mythtv set up and working and can control it using my remote but there's one last hurdle I want to overcome. The following script is meant to turn mythtv on and off. It works fine turning mythtv on but won't turn it off. 

Is there something wrong with the script or is there a better script to do this job. 

#!/bin/bash
PROG=mythfrontend
STATUS=`ps -e | grep $PROG | grep -v grep | wc -l | awk '{print $1}'`

if [ `echo $DISPLAY | grep -c ":0"` -ge 1 ]
then
    if [ $STATUS -eq 0 ]
    then
        ( $PROG & )
    else
        killall $PROG
    fi
fi
exit 0 

Thanks in advance...
Michael

---

