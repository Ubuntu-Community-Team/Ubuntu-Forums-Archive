---
title: "cron - driving me crazy!"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Lutherian on 2007-05-15
Hi all

Trying to do a very simple experiment with cron as follows:

First, checking if cron is loaded, should be by default anyway, so I type
================
sudo /etc/init.d/cron start
================
next I type
=======
crontab -e
======
and I enter this simple command
===============
14 21 * * * /usr/bin/vi
===============

If I'm not mistaken, then at 21:14 the vi editor should launch, but it doesn't.
I've tried this one two different machines (Ununtu 5.10 and Ubuntu 6.10)
Any help would be GREATLY appreciated.

---

### Post by echo $USER on 2007-05-15
Try this as a test to see if its working... add this to /etc/crontab...

30 *   * * * root /etc/init.d/gdm restart

So say at 3.30 your graphical interface should restart if its working.

---

### Post by Bachstelze on 2007-05-15
cron launches it's processes in the background so no wonder ou can't see vi launching... What would the use of having vi launched automatically each day at 21:14 be, anyway ?

---

### Post by Lutherian on 2007-05-17
RE: HymnToLife >It's just a test. To see if it's working. 
Thanks echo $USER I'll give it a try tonight. 
Restart of the gdm would give me visible confirmation that cron is working, which realates to what HymToLife said about the processes being executed in the background.

BTW - is there a method to make processes execute on the foreground? "con -f" or "cron -fg" ??

---

### Post by hyper_ch on 2007-05-17
I normally use a text file for cron stuff

```

nano cron.txt

```

Then I add my cron stuff
```

# Reload Background Image
0,5,10,15,20,25,30,35,40,45,50,55 * * * * sh /home/hyper/wallpaperchanger.sh

# Run chkrootkit
0 1,7,13,19 * * * (cd /usr/sbin; ./chkrootkit 2>&1 | mail -s "chkrootkit output local" email@domain.com)

```

Then of course save it and add it to the user's cron:
```

crontab cron.txt

```

To display whether it's activated:
```

crontab -l

```

That way I can conveniently just edit my cron.txt :)

---

### Post by Lutherian on 2007-05-20
Hey ! hyper_ch , that is a very nice way of working thanks for that tip. Very efficient and smooth.
Thanks to everyone, with your help I managed to get cron working,
essentially I ran the tests with GUI programs for visual confirmation now I feel more confident.

---

### Post by kentpend on 2007-09-02
I've been trying to use cron to start mplayer, but it doesn't at the appointed time nothing happens.
I tried using the gui restart test, with the same result: nothing.

Also, I've seen references to the MAILTO setting for output, but I don't know how to use it.  How do I access the output from cron?

---

### Post by Dr Small on 2007-09-02
Check out the attachment for use of GUI applications with Crontab.

Dr Small

---

### Post by kentpend on 2007-09-03
Thanks, but that wasn't quite what I was looking for.  I should have been more specific when I asked.  I'm using cron to call a script which starts mplayer on a shuffled playlist.

The script works fine when I test it on its own, and I have the path correct for its entry into cron.
However, nothing happens at the time I set it to run.

My crontab looks like this:
```
# m h  dom mon dow   command
25 21 * * * /usr/local/bin/alarm

```

and the script (alarm) looks like this:
```
#!/bin/sh

/usr/bin/X11/xterm -display :0 -bg black -fg white \
-e /usr/bin/mplayer -shuffle -playlist ~/.playlist

```

Somewhere else (I don't recall where right now) I read that the cron daemon is called crond in the process list, and to check if it was running use
```
ps aux | grep crond
```
I did that, and it wasn't there.  I did the same for cron however, and it was.  Is that a fluke, problem, or dated info?

I also tried the gui restart posted by echo $USER, and again, nothing at all happened.

I repeated all of this both as a user and as root, with no change in the results.
I was following a tutorial  at [http://www.federicopistono.org/Set_up_an_MP3_OGG_Alarm_Clock_Using_Linux]("http://www.federicopistono.org/Set_up_an_MP3_OGG_Alarm_Clock_Using_Linux")
as an intro to both cron and scripting, as I don't yet know much about either.

---

### Post by keithacole on 2007-09-03
im watching for answers also..

i need cron to open vlc, start capturing a raw dump, save the dump, then close vlc

i wrote some scripts to do this.. btw i have no idea how to write scripts, so...

```

#!/bin/bash

ivtv-tune -c 69 -d /dev/video1

/usr/bin/vlc pvr:// :pvr-device="/dev/video1" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 :pvr-caching=300 :pvr-width=-1 :pvr-height=-1 :pvr-framerate=-1 :pvr-keyint=-1 :pvr-bframes=-1 :pvr-bitrate-peak=-1 :pvr-bitrate-mode=0 :pvr-audio-bitmask=-1 :pvr-audio-volume=-1 :pvr-channel=0 :demux=dump :demuxdump-file="/home/keith/Desktop/testdump.mpg"


```

and then i have another script to kill vlc
```

#!/bin/bash

pkill vlc

```

with all of this.. the one code that runs is the last script, the firs script never runs.. i know, because if i have vlc open, its killed at the time of the second script.

---

