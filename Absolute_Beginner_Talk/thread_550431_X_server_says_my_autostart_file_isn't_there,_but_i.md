---
title: "X server says my autostart file isn't there, but it is..."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-09-13
I'm following the HowTo: OpenBox customization guide and when I made the autostart.sh, I did exactly what the guide said and I chmodded it via "chmod +x ~/.config/openbox/autostart.sh" and went to log and back in with the new session and it says it can't be found.  The guide I was following is: [http://ubuntuforums.org/showthread.php?t=192106&highlight=openbox+howto+options](http://ubuntuforums.org/showthread.php?t=192106&highlight=openbox+howto+options) and the section that says to make an autostart file is:

> First, make the file ~/.config/openbox/autostart.sh. In it modify the following to fit your needs.
Code:

gedit ~/.config/openbox/autostart.sh

Panels usually cooperate better if you let them load after the WM, so this is a bit different from others.

Code:

#!/bin/sh 
# Auto-mounting drives 
# gnome-volume-manager & 
# GTK themes... this is just one method 
# gnome-settings-daemon & 
# feh stores the last background in .fehbg 
eval `cat $HOME/.fehbg` &
pypanel & 
# This prevents the panel from failing if it loads too fast 
if pgrep pypanel 
then exec openbox 
else pypanel && exec openbox 
fi

*Rauble's note* I commented out gnome-volume-manager and gnome-settings-daemon. These are not necessary but can be very useful. If you cannot use CDs, uncomment the gnome-volume-manager line. For me, my extra harddrive and CD-ROM drives work without it. **

Panels are finicky... the little thing at the end should help.

OK, here's for gdm:

First,
Code:

chmod +x ~/.config/openbox/autostart.sh

Now, edit the session file:
Code:

sudo gedit /usr/share/xsessions/openbox-autostart.desktop

and insert the following into the file:

Code:

[Desktop Entry] 
Encoding=UTF-8 
Name=Openbox Autostart 
Comment=Openbox with autostart goodness 
Exec=/home/dapper/.config/openbox/autostart.sh 
Icon= 
Type=Application

Note: Edit the Exec line to match your user account

finally,
Code:

sudo chmod +x /usr/share/xsessions/openbox-autostart.desktop

(i'm not sure if that's required, but it can't hurt)

Now you must restart and log into the OpenBox Autostart session


Right now, I must run the file manually everytime I login to Openbox.

---

### Post by kevstar31 on 2007-09-15
replace:
if pgrep pypanel
then exec openbox
else pypanel && exec openbox
fi
with:
(sleep 2 && fbpanel) &
openbox

---

