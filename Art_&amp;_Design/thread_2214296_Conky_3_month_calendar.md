---
title: "Conky 3 month calendar"
date: 2014-03-31
forum: Art &amp; Design
---

### Post by mick8 on 2014-03-31
Hello people.
I'm after a 3 month calendar (previous, current, next). I found a 5 month one on these forums, so I edited that but it comes out wrong. when I checked the original that came out wrong as well. current month is march, previous month is march, next month is may.
So I was wondering if one of you nice techies could have a look.    


TEXT
${color4}${execpi 3600 YEAR=`date --date='1 month ago' +%_Y`; MONTH=`date --date='1 month ago' +%_m`; cal -m $MONTH $YEAR}
${hr}
${alignc}${color6}${time %B %G}
${color2}${execpi 3600 DJS=`date +%_d`; cal -h | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/ /' | sed /" $DJS "/s/" $DJS "/" "'${color5}'"$DJS"'${color2}'" "/}
${hr}
${color4}${execpi 3600 YEAR=`date --date='1 month' +%_Y`; MONTH=`date --date='1 month' +%_m`; cal -m $MONTH $YEAR}
${hr}

---

### Post by mick8 on 2014-04-01
turned pc on today 1st april, months changed and it's working now :) don't know why. so, sorry if I put anyone to any trouble.

---

