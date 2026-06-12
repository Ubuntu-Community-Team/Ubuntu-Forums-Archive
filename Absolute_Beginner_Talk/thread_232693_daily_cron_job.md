---
title: "daily cron job"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-08-09
I have placed this script called update in my /etc/cron.daily and made sure it is with chmod 755.
does it look ok/
i have to insert the urls i know about this


lex1

#!/bin/bash
cd /home/mixmaster/Mix
# Get Stats
wget -O - [http://www](http://www).
mlist.tmp
 
if [ -s mlist.tmp ]
then
cp mlist.tmp mlist.txt
fi
 
# Get Keys
wget -O - [http://www](http://www).
pubring.tmp
 
if [ -s pubring.tmp ]
then cp pubring.tmp pubring.mix
fi

---

