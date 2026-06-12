---
title: "autostart rtorrent/screen in Openbox"
date: 2009-01-14
forum: Arch and derivatives
---

### Post by SnakeHips on 2009-01-14
I have rtorrent running in 'screen' following this awesome guide.
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

Openbox is my stand-alone WM (cant see me going back to a DE for a long while :-)

I'm trying to launch 'screen' at startup (xstart) and have 'googled' and tried to work
some solutions but I cant get it to auto-start...

~/.config/openbox/autostart.sh
```

# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

# run the system-wide support stuff
#. $GLOBALAUTOSTART

# programs to run 'before openbox' has started
eval `cat $HOME/.fehbg` &

# programs that will run after Openbox has started
(sleep 5 && conky) &
(sleep 10 && screen) &   <<<<< dont work

```

~/.xinitrc
```

#!/bin/sh
#
# ~~/.xinitrc
#
# Executed by startx (run your window manager from here)
#
# exec ion
# exec wmaker
# exec startkde
# exec icewm
# exec blackbox
# exec gnome-session
# exec startfluxbox
# exec startxfce4
exec openbox-session
# exec startlxde
#exec (sleep 10 && screen) &
exec screen       <<<< dont work

```

any help much appreciated...

---

### Post by hrod beraht on 2009-01-14
> **SnakeHips said:**
> 
~/.config/openbox/autostart.sh
```

(sleep 10 && screen) &   <<<<< dont work

```



Screen is a terminal program, so you have to run the terminal and have it open screen. For example, with xterm it would be:
```
(sleep 10 && xterm -e screen) &
```

Bob

---

### Post by SnakeHips on 2009-01-14
> **hrod beraht said:**
> Screen is a terminal program, so you have to run the terminal and have it open screen. For example, with xterm it would be:
```
(sleep 10 && xterm -e screen) &
```

Bob

That fixed it!

Cheers

---

