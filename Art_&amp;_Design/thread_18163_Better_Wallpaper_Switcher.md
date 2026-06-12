---
title: "Better Wallpaper Switcher"
date: 2005-03-05
forum: Art &amp; Design
---

### Post by dash on 2005-03-05
After downloading so many awesome backgrounds here, I decided I needed to switch between them hourly. I found a shell script to do it on [Michel's page](http://mysite.mweb.co.za/residents/clasqm/ubuntu.html) but it gave me errors occasionally and only scanned one directory, so i wrote a new one in Python. I figured someone else might find it useful, so here it is. 
(To make it run hourly, run "crontab -e" and put "01 * * * * python /path/to/ranwp.py" on a new line in it, then save)

[http://divmod.org/users/washort/ranwp.py](http://divmod.org/users/washort/ranwp.py)

---

### Post by kassetra on 2005-03-05
[QUOTE=dash]After downloading so many awesome backgrounds here, I decided I needed to switch between them hourly. I found a shell script to do it on [Michel's page]("http://mysite.mweb.co.za/residents/clasqm/ubuntu.html") but it gave me errors occasionally and only scanned one directory, so i wrote a new one in Python. I figured someone else might find it useful, so here it is. 
(To make it run hourly, run "crontab -e" and put "01 * * * * python /path/to/ranwp.py" on a new line in it, then save)

[http://divmod.org/users/washort/ranwp.py]("http://divmod.org/users/washort/ranwp.py")[/QUOTE]

Oh wow!  I can't wait to try this!  I have tons of great ubuntu wallpapers I want to switch between often!  Thank you so much!  :)

---

### Post by Zootropo on 2005-03-05
[QUOTE=dash]After downloading so many awesome backgrounds here, I decided I needed to switch between them hourly. I found a shell script to do it on [Michel's page](http://mysite.mweb.co.za/residents/clasqm/ubuntu.html) but it gave me errors occasionally and only scanned one directory, so i wrote a new one in Python. I figured someone else might find it useful, so here it is. 
(To make it run hourly, run "crontab -e" and put "01 * * * * python /path/to/ranwp.py" on a new line in it, then save)

[http://divmod.org/users/washort/ranwp.py](http://divmod.org/users/washort/ranwp.py)[/QUOTE]
 quite useful. as kassetra i have a lot of cool wallpapers and i'm unable to choose beetwen them

---

### Post by rickympl on 2006-06-15
hi, is there any way to get this script to work in xfce?

Thanks in advance.

---

### Post by BlackTopBum on 2007-03-17
Sweet work dash - thanks much. Is better than the other scripts found on the forums. I did have to figure out the "no gconf module" error - I put the Ubuntu server edition on board and built up X, etc. from there. All was needed to add is python-gconf and away we go! Thanks again.

---

### Post by davbren on 2007-03-23
Sorry I'm a n00b how do I use this?

---

### Post by BlackTopBum on 2007-03-23
You should follow the instructions "dash" posted,
"To make it run hourly, run "crontab -e" and put "01 * * * * python /path/to/ranwp.py" on a new line in it, then save".

If there are other questions you have, and I'll guess at some here, please say so.

Here are the steps I undertook to make it work:

1) edited ranwp.py for my system. Read it to see how I changed the path:

#!/usr/bin/env python

BACKGROUND_DIRS = ['/home/cmo/Multimedia/wallpapers/']

2) made a text file I called cron.txt by doing in a terminal

touch cron.txt

vim cron.txt (use your favorite editor)

I entered this to the text file:

# change wallpaper interval
*/10 * * * * python /home/cmo/Multimedia/wallpapers/ranwp.py

and I saved it.

3) I put ranwp.py in /home/cmo/Multimedia/wallpapers/

4) Again in a terminal:

crontab cron.txt

crontab -l (to check it).

5) Found I had to add python-gconf to the system and did so. How did I discover that? I read the local system mail I set up to alert me. That mail listed the error.

6) I continue to enjoy "dash"'s work <g>.

---

### Post by titan3169 on 2007-03-26
Hey blacktop would you be able to pm me or msg me on aim at hawks864 and possibly help me out with this?

---

### Post by BlackTopBum on 2007-03-27
titan3169, I'll do PM.

---

### Post by hofa on 2008-04-18
Thanks! This helped a lot!

---

### Post by Dalif on 2009-02-11
Anybody have a mirror or something for the py file? I seem to get a 404 on it.

---

### Post by Krydahl on 2009-02-11
> **rickympl said:**
> hi, is there any way to get this script to work in xfce?

Thanks in advance.

There's no real need. If you go into the settings manager -> desktop you'll see you can create lists of wallpapers for XFCE to switch between. 

Once a file as has been set up, adding the command "DISPLAY=:0.0 /usr/bin/xfdesktop --reload" to your crontab as often as you want the wallpaper to change will do the trick. So, for example, the line:

```
*/20 * * * * DISPLAY=:0.0 /usr/bin/xfdesktop --reload >/dev/null 2>&1
```

will select a wallpaper at random from your list every 20 minutes.

---

