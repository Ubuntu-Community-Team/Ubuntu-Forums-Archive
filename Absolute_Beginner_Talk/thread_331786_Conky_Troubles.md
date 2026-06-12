---
title: "Conky Troubles"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by willskills on 2007-01-05
I have it running okay at the moment, but I want 2 things, to run it without a terminal, and for it to "squash" to the desktop, if possible. Atm when I do a ctrl+alt +d - it disappears too.

Any tips? :)

I use Ubuntu 6.06, here is my config

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

own_window_colour brown
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
background no

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

---

### Post by m.musashi on 2007-01-07
There are a couple ways to run without the terminal. One is to use alt-f2 and type conky. A slightly more elegant way is to add a custom app launcher. For this, right click the panel and choose add to panel. In the window that opens, click the custom app launcer tab (I use edgy and I can't remember if it's different in Dapper). For type leave application, for name "conky" or whatever you want and for command "conky" (no quotes) and then okay. That will add an icon on the panel that when clicked runs conky. I chanced the icon to be the conky mascott.

To keep conky "squashed" (if by that you mean so it doesn't minimize) add an own_window_type option. For example, mine looks like this...
```
own_window_type overide
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
If that doesn't work try desktop instead of overide. There are probably other options but hopefully one will work.

---

### Post by kerry_s on 2007-01-07
You want to start conky after the desktop so it's on top. First you need to make a delayed startup than add that to the session start up. Here's for the start script->

gedit ~/.conky-on

put->

#!/bin/sh
sleep 10
conky &

then make it executable->

chmod +x ~/.conky-on

Now just add the full path to the session start, would look like this->

/home/(user)/.conky-on

Replace (user) with account name.

You can adjust the time accordingly, i just put 10 sec's for now. I don't know how long your desktop takes to start.

---

### Post by fredster001 on 2007-01-07
don't have an answer, but was just wondering what 'conky' was?

Thanks

---

### Post by kerry_s on 2007-01-07
> **fredster001 said:**
> don't have an answer, but was just wondering what 'conky' was?

Thanks

Conky is a light weight system monitor you can grab from the repos-> [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

Here's what mine looks like->

---

