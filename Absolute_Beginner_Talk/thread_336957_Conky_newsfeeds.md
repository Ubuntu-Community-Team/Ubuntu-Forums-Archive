---
title: "Conky newsfeeds"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by mells on 2007-01-12
I notice some people have RSS newsfeed from the BBC on their conky panel. I have tried playing with the config file '.conkyrc' but cant get it working. 

Here is my .conkyrc

> # UBUNTU-CONKY
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

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}Computer ${hr 2}$color
$nodename $sysname $kernel on $machine
System Uptime: $uptime

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar

${color orange}System Resources ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Ubuntu :  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
Windows:  ${fs_free_perc /media/windows}%   ${fs_bar 6 /media/windows}$color

${color orange}Wireless Network (${addr wlan0}) ${hr 2}$color
Wireless Signal Quality: $alignr${linkstatus wlan0}  %
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0 
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}System Logging ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}My Fortune ${hr 2}$color
${execi 120 fortune -s | fold -w50}

${color orange}UK News ${hr 2}$color

Any Ideas. I have pulled others who have posted theirs but to no avail.

---

### Post by mells on 2007-01-12
anyone?

---

### Post by kiccioni on 2007-01-15
Maybe this can help... [http://www.suseforums.net/lofiversion/index.php/t24679.html]("http://www.suseforums.net/lofiversion/index.php/t24679.html")
Or try conky main page: [http://conky.sourceforge.net]("http://conky.sourceforge.net")

Good luck!!!

---

