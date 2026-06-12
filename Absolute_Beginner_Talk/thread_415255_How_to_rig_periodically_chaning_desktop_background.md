---
title: "How to rig periodically chaning desktop background?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Cheese Sandwich on 2007-04-20
** (Sorry, typo: "chaning"==>"changing")

I like good desktop imagery, and would like my machine to periodically update it from a directory of image files.

If someone could supply the command-line way of setting the desktop, I could run something like:

foreach x (<wallpaper image dir>/*)

   <set $x as wallpaper>
   sleep 86400 // 24 hrs

end

The above runs in tcsh, would it also run in bash? Would I run this in a minimized terminal window, or would there be a way to implement this as a system service?

-Thx

---

### Post by jfinkels on 2007-04-20
> **Cheese Sandwich said:**
> I like good desktop imagery, and would like my machine to periodically update it from a directory of image files.

If someone could supply the command-line way of setting the desktop, I could run something like:

foreach x (<wallpaper image dir>/*)

   <set $x as wallpaper>
   sleep 86400 // 24 hrs

end

The above runs in tcsh, would it also run in bash? Would I run this in a minimized terminal window, or would there be a way to implement this as a system service?

-Thx

Once you find a program that sets your background, save this as a shell script, make it executable, and then go to "System > Preferences > Sessions" and add the script to your startup processes list. Then it will start when you log in to your graphical Desktop Environment.

---

### Post by Cheese Sandwich on 2007-04-20
Ah, look what I found:

[http://ubuntu.wordpress.com/2005/12/01/random-wallpaper-in-gnome/](http://ubuntu.wordpress.com/2005/12/01/random-wallpaper-in-gnome/)

8)

---

### Post by brennydoogles on 2007-04-20
I'm having a hard time figuring out how to configure this script... would anyone be willing to give me a few pointers?? Thanks!!

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

# Copyright (c) Daniel Lombraña González.
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# ( at your option) any later version.
#             
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#                            
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA)

import os
import random
from os import system
from os import path

# Changes de wallpaper for Gnome. You only have to select the soft link: Wallpaper that this script generates. Each time you enter in your gnome session, you will see the soft link as the background.
# The best way for see the effect is adding one line like this in cron:
# @reboot /home/user/Wallpapers/cambiar.py
# If you want to have the wallpapers in other location, change the next variable to another Folder in your Home folder.

Folder = "Wallpapers"   # Where it sould be the wallpapers and this script

# Generation of the path of Wallpapers
Wallpapers= os.path.join(os.path.expanduser( "~"), Folder)

# We get the different files in the folder, and choose one randomly
files = os.listdir(Wallpapers)
# We remove the script and the soft link from the candidates to be selected
files.remove('cambiar.py')
if os.path.isfile(os.path.join(Wallpapers,'Wallpaper')):
    files.remove('Wallpaper')
background = random.choice(files)
# Here we change the old softlink to the newer one
os.remove(os.path.join(Wallpapers,'Wallpaper'))
os.symlink(os.path.join(Wallpapers,background), os.path.join(Wallpapers,'Wallpaper'))


``` 

Do I need to put the pictures I want to be candidates for my wall paper in the folder containing the script, or do I want to change the script to be pointing to the folder that contains the pictures I want to use?? Also, how will it download new pictures for me??

---

### Post by Cheese Sandwich on 2007-04-21
Ok, I got it to work. Here's the deal:

The python script to change the background image:

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

backgrounds = "images/backgrounds"

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

So I put all the images I want as candidates for the desktop in

/home/<login_name>/images/backgrounds

and the above script will randomly choose one of them & set it to background. The above script does not reside in ~/images/background, but rather in ~/bin, a directory I made for scripts.

Now to do that background-changing periodically, I have the following script:

```

#!/bin/bash
while true
do
   python /home/<login_name>/bin/background_change
   sleep 1000
done

```

The file containing the above is set to be executable via "chmod +x <script_filename>". "/home/<login_name>/bin/background_change" is the above python script. The "sleep 1000" tells it to pause for 1000 seconds (of course this can be adjusted to whatever).

I then "System"->"Preferences"->"Sessions" to set the above script to run automatically at the beginning of the session (thanks **jfinkels**).

Works great! 8)

---

### Post by brennydoogles on 2007-04-22
> **Cheese Sandwich said:**
> Ok, I got it to work. Here's the deal:

The python script to change the background image:

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

backgrounds = "images/backgrounds"

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

So I put all the images I want as candidates for the desktop in

/home/<login_name>/images/backgrounds

and the above script will randomly choose one of them & set it to background. The above script does not reside in ~/images/background, but rather in ~/bin, a directory I made for scripts.

Now to do that background-changing periodically, I have the following script:

```

#!/bin/bash
while true
do
   python /home/<login_name>/bin/background_change
   sleep 1000
done

```

The file containing the above is set to be executable via "chmod +x <script_filename>". "/home/<login_name>/bin/background_change" is the above python script. The "sleep 1000" tells it to pause for 1000 seconds (of course this can be adjusted to whatever).

I then "System"->"Preferences"->"Sessions" to set the above script to run automatically at the beginning of the session (thanks **jfinkels**).

Works great! 8)

The script works well for what it does, but I have noticed that GAIM and AMAROK no longer run when the script is active... is there any way to change that? Also, the name in the python script for itself does not match up with the name for it in the BASH script. Not a big deal, but if anyone is having problems and can't figure out why that may be the cause. Very nice though.

If you figure out what's blocking my other programs i would greatly appreciate it!!

---

### Post by Teddy_P on 2007-05-02
Bump

I want to try this and want to know if every one will have a problem with GAIM opening?



Teddy

---

### Post by brennydoogles on 2007-05-02
> **Teddy_P said:**
> Bump

I want to try this and want to know if every one will have a problem with GAIM opening?



Teddy

Just to let you know, the problem fixed itself after a few days... I just forgot to update that here. Hope everything works great for you!

---

