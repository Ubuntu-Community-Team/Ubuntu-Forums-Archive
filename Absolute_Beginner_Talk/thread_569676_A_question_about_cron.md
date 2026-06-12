---
title: "A question about cron"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by baja munda on 2007-10-07
I wanted to create an alarm using cron, so I wrote a script which I hoped would open a youtube video every morning.

So I wrote this script:

~/scripts$ cat alarm.sh
#!/bin/bash
/usr/bin/firefox "http://www.youtube.com/watch?v=PEN75yBGlNs"

Then I did 
~/scripts$ chmod a+x alarm.sh

Then I added a line to my crontab:

~/scripts$ crontab -l
# m h  dom mon dow   command
45 7 * * * /home/bb/scripts/alarm.sh

/home/bb/scripts/alarm.sh is the full path 

Now, running alarm.sh by itself does open up the browser and the music starts playing, but the cron thing does not work.

---

### Post by sumguy231 on 2007-10-07
Did you edit crontab normally or with the 'crontab -e' command? If you do the latter, cron should recognize the new entry right away.

Also, if you already have a MTA set up, then cron will mail you a lot of information which you could check either by looking in /var/mail or using a mail client which uses that. I never figured out where cron logged its stuff, so I always just did it that way. I'm sure it logs its output somewhere though.

---

### Post by derred on 2007-10-07
did you try doing a reboot or at least a "sudo /etc/init.d/cron restart"?

---

### Post by baja munda on 2007-10-07
> **sumguy231 said:**
> Did you edit crontab normally or with the 'crontab -e' command? If you do the latter, cron should recognize the new entry right away.

Also, if you already have a MTA set up, then cron will mail you a lot of information which you could check either by looking in /var/mail or using a mail client which uses that. I never figured out where cron logged its stuff, so I always just did it that way. I'm sure it logs its output somewhere though.

Yes, I added that line using crontab -e. I will look up the mta stuff, I don't know much about it.

---

### Post by baja munda on 2007-10-25
Found out what the problem was, I wish I had better googling skills.

Anyway, in case anyone is interested : for running a gui app one has to specify a display,  an example  from [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

00 06 * * * **env DISPLAY=:0.** gui_appname

---

