---
title: "Changing Desktop"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-05-07
My friend has a Mac and this has a brilliant function where the desktop background changes every couple of seconds.

I was wondering whether there is a piece of software that can do this on Ubuntu?

Many thanks.

---

### Post by gondilon on 2006-05-07
if you go into the desktop mananger, I believe there is asetting to have a slideshow on the desktop.

---

### Post by Dr Von Bon Bon on 2006-05-07
Where is the desktop manager please?

---

### Post by sailor2001 on 2006-05-07
system/preference/backdrop

---

### Post by Dr Von Bon Bon on 2006-05-07
I don't have that. The only thing I have is just the desktop background thing that just lets me choose the pictures and doesn't give me the option of having a slideshow.

---

### Post by uzi09 on 2006-05-07
i believe this is what you're looking for...
[http://easylinux.info/wiki/Ubuntu#How_to_set_up_automatic_background_change_.28GNOME.29](http://easylinux.info/wiki/Ubuntu#How_to_set_up_automatic_background_change_.28GNOME.29)

---

### Post by Dr Von Bon Bon on 2006-05-07
Thanks very much.

I have the background thing done but nothing is happening.

The thing is I'm not sure how to tell it to change every ten seconds or something.

This is what the thing in the .backgrounds folder says.

```
#!/usr/bin/python
#
# change-background.py
#
# A script to change to a random background image
#
# (c) 2004, Davyd Madeley <davyd@madeley.id.au>
#
#   This program is free software; you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation; either version 2, or (at your option)
#   any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program; if not, write to the Free Software Foundation,
#   Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
#

backgrounds = ".backgrounds"

import gconf
import os
import random
import mimetypes

class GConfClient:
        def __init__ (self):
                self.__client__ = gconf.client_get_default ()
        def get_background (self):
                return self.__client__.get_string ("/desktop/gnome/background/picture_filename")
        def set_background (self, background):
                self.__client__.set_string ("/desktop/gnome/background/picture_filename", background)

client = GConfClient ()


dir_items = os.listdir (os.path.join (os.environ["HOME"], backgrounds))
items = []

for item in dir_items:
        mimetype = mimetypes.guess_type (item)[0]
        if mimetype and mimetype.split ('/')[0] == "image":
                items.append (item)

item = random.randint (0, len (items) - 1)
current_bg = client.get_background ()

while (items[item] == current_bg):
        item = random.randint (0, len (items) - 1)

client.set_background (os.path.join (os.environ["HOME"], backgrounds, items[item]))


```

Could you please tell me what I have to do to make it change please?

Thanks.

---

### Post by Rinzwind on 2006-05-07
I got it working as it is intended.

The line edited into crontab states it needs to start this python script on REBOOT.
Ie. every time you reboot it changes background.

BUT changing crontab to do this every 10 minutes can't be too hard!


edit: to make it crystal clearV on Bon Bon: leave the script as it is.
The line in  crontab needs changing!

edit2:
export EDITOR=gedit && crontab -e
0-59 * * * * ~/.backgrounds/change_background.py


this should execute it every 1 minute (?) I HOPE.
Gonna reboot and test it now BRB

---

### Post by Rinzwind on 2006-05-07
Works

:)

---

### Post by uzi09 on 2006-05-07
hey, i've come across the link before which is why i gave it to u, i actually just tried it out for the first time myself.

i guess all it does is change to a random background once (or take a loong time to change). if u want to change over and over again after a certain time interval, you could probably just create a small shell script to do that for ya.

okay...lol, i guess i'm not the programmer i thought i was :S. lol, i wrote a script at school to do this, and some how it worked. lol, for some reason it isn't working here. i'm sure there other people there that can whip up a quick script to do that for ya. in the mean time, i'll try to figure it out.

good luck

edit: sorry, took so long to reply, that u already got it working o_O. mind filling us in on what u did?

---

### Post by Biltong (Dee) on 2006-05-07
Sometimes it is easier just to right click and add the desktop background launcher to the panel. I reboot rarely, but have a huge number of sci-fi wallpapers I change whenever it takes my fancy. If you are interested the wallpapers can be found here:
[http://wittswallpapers.com/Planetscapes/planet000008.htm](http://wittswallpapers.com/Planetscapes/planet000008.htm)

---

### Post by Rinzwind on 2006-05-07
Ok rundown on the installation:

1. Make a directory .backgrounds in your home directory:
**mkdir ./backgrounds**

2. Change to that directory with
**cd ./backgrounds**

3. Download this file with:
**wget -c [http://easylinux.info/uploads/change_background.py](http://easylinux.info/uploads/change_background.py)**

4. change the permissions:
**chmod +x change_background.py**

5. Create a startup file (it's called crontab in Linux):
**export EDITOR=gedit && crontab -e**
Change gedit for any editor you like to use.

6. Add this line as the LAST line in this file:
**0-59 * * * * ~/.backgrounds/change_background.py**
Save the file. If you made a typo there will be a notice in  your terminal and the change is NOT accepted.

7. Reboot to activate this program.

0-59 means every minute
0-59/2 means every 2 minutes
1 means 1 minute after every hour.
0,10,20,30,40,50 every 10 minutes

---

### Post by Biltong (Dee) on 2006-05-07
Sorry. The above link is for page 8. The home page is as follows:
[http://wittswallpapers.com/Planetscapes/indexplan.html](http://wittswallpapers.com/Planetscapes/indexplan.html)

---

### Post by Rinzwind on 2006-05-07
[QUOTE=Biltong (Dee)]Sorry. The above link is for page 8. The home page is as follows:
[http://wittswallpapers.com/Planetscapes/indexplan.html](http://wittswallpapers.com/Planetscapes/indexplan.html)[/QUOTE]
Very nice :) :)

Got a gzip-file with all of them? *whistles innocently*

---

### Post by Biltong (Dee) on 2006-05-07
[QUOTE=Rinzwind]Very nice :) :)

Got a gzip-file with all of them? *whistles innocently*[/QUOTE]

I wish!! 
Save em one by one like the rest of us :D

---

### Post by Rinzwind on 2006-05-07
[QUOTE=Biltong (Dee)]I wish!! 
Save em one by one like the rest of us :D[/QUOTE]

:D :D I got 9 and am allready fed up

---

### Post by Rinzwind on 2006-05-07
Here's alot of Tuxes

[http://www.easylinuxcds.com/wallpapers/thumbs7.shtml](http://www.easylinuxcds.com/wallpapers/thumbs7.shtml)

---

### Post by Biltong (Dee) on 2006-05-07
Thanks, but if we continue with this thread we will be kicked to the cafe - and rightly so.

---

### Post by Dr Von Bon Bon on 2006-05-08
Hi again,

I followed your instructions and installed it as you said but nothing has happened.

Do you have any ideas?

The only thing that I can think of that's stopping it will be that I use InitNG.

Could this be the reason? And if it is please could you help me sort it out?

Many thanks.

---

### Post by Rinzwind on 2006-05-08
If you stopped CRON in initng you should switch it on again. You need that  :)

Just to make sure:
- you created .backgrounds in your home dir?
-> **ls -a** shows you hidden dir's.
- copied wallpapers to that directory?
- copied the script into that directory?
-> **ls -l .backgrounds**  shows you content inside the dir

**crontab -l**
-> shows you the content of your crontab.


And it's working perfectly overhere. :)

---

### Post by Dr Von Bon Bon on 2006-05-09
Okay, everything seemed fine when I checked those thingys.


Hmmm, how do I turn Cron on on InitNG pleasE?

---

### Post by Rinzwind on 2006-05-09
[http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)
That's the how-to to it.

Short version:
sudo sysv-rc-conf

find 'cron' 
and
2,3,4 and 5 should be 'x'-ed.

---

### Post by Dr Von Bon Bon on 2006-05-09
I somehow got it to work (it's sooooo cool) but I how would I alter and what would I alter so it changes every ten seconds please?

---

### Post by Rinzwind on 2006-05-09
[QUOTE=Dr Von Bon Bon]I somehow got it to work (it's sooooo cool) but I how would I alter and what would I alter so it changes every ten seconds please?[/QUOTE]

Sorry, but that's not possible with cron :( 
1 minute is the smallest amount of time.

WTH do you want it every 10 seconds? :D

---

