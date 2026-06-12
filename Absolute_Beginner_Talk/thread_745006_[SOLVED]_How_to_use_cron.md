---
title: "[SOLVED] How to use cron?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by GoCool on 2008-04-04
I have a simple request. Every day at 6.58  am I want a music to be played automatically. But not sure how to write a cron for it. This is what I did and nothing happened

>  
58 06 * * * "/media/DRV2_VOL1/My Music/01Med-01/003-AntarmanMeJyoti-Meditation-1.mp3"


I know what my problem is, 
1. I did not specify any program with which I want this mp3 to be opened. But not sure how to specify it.
2. There is a space in the path "My Music", would it be a problem?

Any help on this would be highly appreciated.

---

### Post by kpkeerthi on 2008-04-04
Does mplayer play when you put this command in a terminal?
```

mplayer /media/DRV2_VOL1/My\ Music/01Med-01/003-AntarmanMeJyoti-Meditation-1.mp3

```

*Note there is **\ **between **My** and **Music**

If it plays from command line, put the whole line in your crontab

Open crontab
```
crontab -e
```

and add this line
```

58 06 * * * mplayer /media/DRV2_VOL1/My\ Music/01Med-01/003-AntarmanMeJyoti-Meditation-1.mp3

```

---

### Post by GoCool on 2008-04-04
From the command prompt its playing but when I put in the cron its not.

I am doing something silly but not able to figure out.

When I give "crontab -l" this is what I get

> 
11 10 * * * mplayer /media/DRV2_VOL1/My\ Music/01Med-01/003-AntarmanMeJyoti-Meditation-1.mp3


PS: For testing purpose I have asked it to play at 10:11 am (my time here)

---

### Post by Oldsoldier2003 on 2008-04-04
> **GoCool said:**
> From the command prompt its playing but when I put in the cron its not.

I am doing something silly but not able to figure out.

When I give "crontab -l" this is what I get



PS: For testing purpose I have asked it to play at 10:11 am (my time here)

thats because mplay is a graphical program. see this link: [http://ubuntujourney.wordpress.com/2008/03/25/graphic-applications-in-cronjobs/](http://ubuntujourney.wordpress.com/2008/03/25/graphic-applications-in-cronjobs/)

basically you need to star the command with DISPLAY=:0

---

### Post by GoCool on 2008-04-04
No luck. This is what I have in my crontab now

> 
38 11 * * * DISPLAY=:0 mplayer /media/DRV2_VOL1/My\ Music/01Med-01/003-AntarmanMeJyoti-Meditation-1.mp3


I removed the space between  "DISPLAY=:0" and "mplayer" but still no luck.

---

### Post by Oldsoldier2003 on 2008-04-04
> **GoCool said:**
> No luck. This is what I have in my crontab now



I removed the space between  "DISPLAY=:0" and "mplayer" but still no luck.

put mplayers path in there. by default it's /usr/bin/mplayer 

often issues in cronjobs are caused by the app not being found correctly. Making a habit of using the full path will save you headaches in the future.

---

### Post by Oldsoldier2003 on 2008-04-04
looking ove the thread i just realized you are also using a directory name with a space in it. 

try using "/long/path/with spaces in filenames" instead of a slash delimiter. One of the reasons people use the underscore instead of spaces is becuase spaces can still cause problems from time to time

also you can test this by running a cron job on a file stored elsewehere in a dr that has no spaces in the name.

---

### Post by mtbeedee on 2008-04-04
Also try checking /var/log/syslog to see what the output from cron is.  It probably has some meaningful error message there.

---

### Post by GoCool on 2008-04-04
No luck.
1. I put the file in a separate directory without spaces
2. I checked the syslog but it's giving me only the edit info

This is what my crontab -l shows

> 
# m h  dom mon dow   command
# 33 11 * * * DISPLAY=:0 mplayer /media/DRV2_VOL1/My\ Music/01Med-01/003-AntarmanMeJyoti-Meditation-1.mp3
20 14 * * * DISPLAY=:0 /usr/bin/mplayer /home/administrator/Music/tc/AntarMan.mp3


This is what my syslog is showing
> 
Apr  4 13:32:25 sound-room crontab[12771]: (root) BEGIN EDIT (root)
Apr  4 13:33:30 sound-room crontab[12771]: (root) REPLACE (root)
Apr  4 13:33:30 sound-room crontab[12771]: (root) END EDIT (root)
Apr  4 13:33:34 sound-room crontab[12775]: (root) LIST (root)
Apr  4 13:34:01 sound-room /USR/SBIN/CRON[12777]: (root) CMD (mplayer /home/administrator/Music/tc/AntarMan.mp3)
Apr  4 13:51:07 sound-room -- MARK --
Apr  4 14:11:07 sound-room -- MARK --
Apr  4 14:13:01 sound-room crontab[12825]: (root) LIST (root)
Apr  4 14:13:39 sound-room crontab[12827]: (administrator) LIST (administrator)
Apr  4 14:13:55 sound-room crontab[12828]: (administrator) BEGIN EDIT (administrator)
Apr  4 14:17:01 sound-room /USR/SBIN/CRON[12833]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  4 14:18:54 sound-room crontab[12828]: (administrator) REPLACE (administrator)
Apr  4 14:18:54 sound-room crontab[12828]: (administrator) END EDIT (administrator)
Apr  4 14:19:00 sound-room crontab[12835]: (administrator) LIST (administrator)
Apr  4 14:19:01 sound-room /usr/sbin/cron[6563]: (administrator) RELOAD (crontabs/administrator)
Apr  4 14:19:01 sound-room /USR/SBIN/CRON[12837]: (administrator) CMD (DISPLAY=:0 /usr/bin/mplayer /home/administrator/Music/tc/AntarMan.mp3)
Apr  4 14:19:14 sound-room crontab[12840]: (administrator) BEGIN EDIT (administrator)
Apr  4 14:19:26 sound-room crontab[12840]: (administrator) REPLACE (administrator)
Apr  4 14:19:26 sound-room crontab[12840]: (administrator) END EDIT (administrator)
Apr  4 14:19:27 sound-room crontab[12843]: (administrator) LIST (administrator)
Apr  4 14:20:01 sound-room /usr/sbin/cron[6563]: (administrator) RELOAD (crontabs/administrator)
Apr  4 14:20:01 sound-room /USR/SBIN/CRON[12846]: (administrator) CMD (DISPLAY=:0 /usr/bin/mplayer /home/administrator/Music/tc/AntarMan.mp3)


---

### Post by Oldsoldier2003 on 2008-04-04
give me a moment i'll try setting up a cronjob on my box and paste what works

---

### Post by FuturePilot on 2008-04-04
You need to use the DISPLAY and the Mplayer command as two separate commands.
Try this for the command
```
export DISPLAY=:0 && /usr/bin/mplayer /home/administrator/Music/tc/AntarMan.mp3
```
Also this is assuming your display is in fact Display :0

---

### Post by Oldsoldier2003 on 2008-04-04
```
39 * * * *	DISPLAY=:0 /usr/bin/exaile /home/chuck/test.mp3
```
worked for me. let me seeif i can get mplayer to work

---

### Post by Oldsoldier2003 on 2008-04-04
> **FuturePilot said:**
> You need to use the DISPLAY and the Mplayer command as two separate commands.
Try this for the command
```
export DISPLAY=:0 && /usr/bin/mplayer /home/administrator/Music/tc/AntarMan.mp3
```
Also this is assuming your display is in fact Display :0

Display 0 is the default desktop. So far exporting and && have both failed to run the command from the crontab. pasting the commands into a terminal window works though (as they should)

---

### Post by Oldsoldier2003 on 2008-04-04
**GoCool**: Is there any particular reason you want the mp3 to play in mplayer? if you could get it to play in audacious or another player would it be acceptable?

there is something odd about mplayer, i can get audacious and exaile to run fine on a cronjob...

---

### Post by FuturePilot on 2008-04-04
Actually ```
mplayer
``` is not the graphical mplayer. So you don't need to export the display. If you were using the graphical mplayer it would be
```
gmplayer
```
Anyways I just got it working. Here's my crontab
```
05 15 * * * export DISPLAY=:0 && /usr/bin/mplayer /home/nick/Music/Dance.mp3 >/dev/null 2>&1 # Something, 

```
Despite the export DISPLAY it still worked

---

### Post by Oldsoldier2003 on 2008-04-04
> **FuturePilot said:**
> Actually ```
mplayer
``` is not the graphical mplayer. So you don't need to export the display. If you were using the graphical mplayer it would be
```
gmplayer
```
Anyways I just got it working. Here's my crontab
```
05 15 * * * export DISPLAY=:0 && /usr/bin/mplayer /home/nick/Music/Dance.mp3 >/dev/null 2>&1 # Something, 

```
Despite the export DISPLAY it still worked

good catch futurepilot. for somereason it didnt click that mplayer was the cli interface not the graphical one. makes sense to redirect to /dev/null in that context

---

### Post by GoCool on 2008-04-04
I got it working with another player called "audacious".

From another forum I came to know that the output should be redirected to /dev/null for "mplayer". But I don't know what it means, I think it is to add "> /dev/null" at the end of the line in crontab. 

Any way I am impessed with you all for your excellent and prompt response, true to the word Ubuntu.

******
Sorry...after posting I saw the responses from OldSoldier and FuturePilot. Please accept my thanks and sincere gratitude for being with me till the end. Once again my heart felt thanx.

---

