---
title: "Crontab help"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by TokenBad on 2006-09-21
I have a python script that changes my background wallpaper...but want crontab to run it every hour...so every hour have a new wallpaper...but I have no idea how to setup crontab to do that...Please any info on this would be great...

Thanks

TokenBad

---

### Post by sagibson on 2006-09-21
I've always created a text file with my crontab entries and issued the command 'crontab #filename#' to get those entries into crontab.

---

### Post by andypaxo on 2006-09-21
A quick google reveals many tutorials.
This one looks to be the most straight forward of the ones that I saw: [http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)

Hope this helps

---

### Post by chrisfay on 2006-09-22
I know for running bash scripts you can just copy them right into the /etc/cron.hourly folder. They will then be ran obviously every hour. 

I'm not sure if its that easy for python scripts.

---

