---
title: "how to properly edit a .vnc file for vncserver?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-09
here is acopy of the current .vnc/xstart file

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &

What do i have to change to get a screen size of 1186x860 depth 24
and for it to start the xbuntu desktop? No matter what i try i keep getting a small screen and a tan screen with the X curser and some writing in the upper left corner about a clipboard

---

