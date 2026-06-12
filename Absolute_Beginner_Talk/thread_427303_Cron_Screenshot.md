---
title: "Cron Screenshot"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-04-29
I'm attempting to set up a cron job to take a screenshot of everything on my screen at a certain interval. I know how to set the "when" part of the job (I've tested that). For the "what" part, I've attempted using scrot and the import command in imagemagick. Neither will work. However, both work if I enter them in a terminal window. Does anyone know how I could set this up?

---

### Post by Happy_Man on 2007-04-29
Try using "gnome-screenshot."

---

### Post by nhandler on 2007-04-29
> **Happy_Man said:**
> Try using "gnome-screenshot."

I can't. gnome-screenshot launched a dialog window. I need this to be 100% automatic so it will work even while I am not at my computer.

---

### Post by nanotube on 2007-04-29
> **Cheater said:**
> I'm attempting to set up a cron job to take a screenshot of everything on my screen at a certain interval. I know how to set the "when" part of the job (I've tested that). For the "what" part, I've attempted using scrot and the import command in imagemagick. Neither will work. However, both work if I enter them in a terminal window. Does anyone know how I could set this up?

did you put in the full path to the executable in your cron job? cron jobs generally don't have the full set of environment variables that you get in a regular shell, including the PATH var.

---

### Post by nhandler on 2007-04-29
> **nanotube said:**
> did you put in the full path to the executable in your cron job? cron jobs generally don't have the full set of environment variables that you get in a regular shell, including the PATH var.

I just tried running it with the full path.
* * * * * /usr/bin/scrot /home/cheater/test.png
* * * * * /usr/bin/import -window root -display :0 /home/cheater/screenshot.png

That's what is in my crontab file. It is in the crontab for cheater not for root. Neither of them are working. They should be getting run every minute.

---

### Post by nhandler on 2007-04-29
Well, I have sort of accomplished my goal. I got the end result I wanted, I just went about it in a different manner.
I made a small script called screenshot which I placed in /usr/bin. I then used chmod to make it executable. The script looks like this:
```
while true ; 
do
import -window root -display :0 /home/cheater/screenshot.png
sleep 300
done
```
The 'sleep 300' part tells it to wait 5 minutes before taking a new screenshot. You can modify the delay by replacing the 300 with the new delay (in seconds). I then went to System->Preferences->Sessions and added my new screenshot command.
Name: Screenshot
Command: screenshot &

I don't believe you need hte & at the end when you are running it like this, but I put it on for good measures.

---

### Post by nanotube on 2007-04-30
> **Cheater said:**
> Well, I have sort of accomplished my goal. I got the end result I wanted, I just went about it in a different manner.
I made a small script called screenshot which I placed in /usr/bin. I then used chmod to make it executable. The script looks like this:
```
while true ; 
do
import -window root -display :0 /home/cheater/screenshot.png
sleep 300
done
```
The 'sleep 300' part tells it to wait 5 minutes before taking a new screenshot. You can modify the delay by replacing the 300 with the new delay (in seconds). I then went to System->Preferences->Sessions and added my new screenshot command.
Name: Screenshot
Command: screenshot &

I don't believe you need hte & at the end when you are running it like this, but I put it on for good measures.

so out of curiosity... why do you need a screenshot every 5 min? and write it to the same filename, too? :)

---

### Post by nhandler on 2007-04-30
I might change it to not overwrite old screenshots. I didn't post the entire script. The rest of it copies it to a protected directory on my server. That way, I can keep an eye on what is going on at my computer remotely. I know I can use vnc or some other protocol (which I do as well). I just wanted to do this to try it.

---

### Post by jordanmthomas on 2007-08-24
I realize it's like 2 and a half months later now, but I was trying to do the exact same thing as you tonight and was having troubles (mine appear to be different than yours...I had trouble with the "when" part but not the script itself.  It turned out I had a - at the front of the line in my crontab for some reason). 

If you're still interested in getting a cron job to do this for you instead of what you came up with here's what worked for me:
in my crontab:
```
*/5 * * * * /home/jordan/bin/scrot_current
```
and here's the scrot_script I had (not much of a script and you'd need to change the filename, but you get the point):
```
#!/bin/bash
DISPLAY=:0.0 scrot '$HOME/screenshots/CURRENT/current.png' -q 100

```

---

### Post by nhandler on 2007-08-24
I ended up using a script to accomplish that. Here the contents of it

```
while true ; 
do
import -geometry 50%x50% -window root -display :0 /home/cheater/screenshot.png
sleep 300
done

```

Then I set it up so that this script is run on startup.

---

### Post by jordanmthomas on 2007-08-24
> I ended up using a script to accomplish that. 
I know, I just thought you might be interested in a working cron job for it.  :)

---

