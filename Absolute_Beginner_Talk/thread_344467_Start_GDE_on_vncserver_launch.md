---
title: "Start GDE on vncserver launch"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by moneal on 2007-01-23
Hi,

I am new to Linux configuration and am having difficulty getting GDE to launch when I start a new vncserver session.  

Below is my /etc/vnc.conf file listing:

[COLOR="Blue"] $vncClasses = "/usr/share/vncserver";

 $XFConfigPath = "/etc/X11/XF86Config";


 $colorPath = "/usr/X11R6/lib/X11/rgb";

 $vncUserDir = "$ENV{HOME}/.vnc";

 $vncPasswdFile = $vncUserDir . "/passwd";

 $vncStartup = "$ENV{HOME}/.vnc/xstartup";

$geometry = "950x700"

$ depth = "24"

$fontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
$fontPath .= "/usr/share/X11/fonts/misc,";
$fontPath .= "/usr/share/X11/fonts/cyrillic,";
$fontPath .= "/usr/share/X11/fonts/100dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/75dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/Type1,";
$fontPath .= "/usr/share/X11/fonts/CID,";
$fontPath .= "/usr/share/X11/fonts/100dpi,";
$fontPath .= "/usr/share/X11/fonts/75dpi,";
# paths to defoma fonts
$fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,";
$fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID";[/COLOR]

and /home/moneal/.vnc/xstartup:

[COLOR="Blue"]#!/bin/sh

# Uncomment the following two lines for normal desktop:
 unset SESSION_MANAGER
 exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startx &[/COLOR]

Any help would be greatly appreciated, I'm thinking that this script in xstartup is not correct, I'll admit it's a cut and paste job.

Mark

---

