---
title: "Uptime formating"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-03-03
I'm trying to format my uptime to display in the following format: Day/ Hour/ Minutes. I have this script:

#!/bin/bash
#
#   upt - show just the system uptime, days, hours, and minutes

let upSeconds="$(cat /proc/uptime) && echo ${temp%%.*})"
let secs=$((${upSeconds}%60))
let mins=$((${upSeconds}/60%60))
let hours=$((${upSeconds}/3600%24))
let days=$((${upSeconds}/86400))
if [ "${days}" -ne "0" ]
then
   echo -n "${days}d"
fi
echo -n "${hours}h${mins}m"

But it's not working. Does anyone have any ideas?

---

