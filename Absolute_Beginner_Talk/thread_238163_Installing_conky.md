---
title: "Installing conky"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by brotakul on 2006-08-17
i tried to install conky with apt-get. i use ubuntu 6.06 dapper
[[IMG]http://img207.imageshack.us/img207/7648/screenshotiq8.th.png[/IMG]](http://img207.imageshack.us/my.php?image=screenshotiq8.png)

you ca see the low quality graphics and the errors in the terminal. what should i do to fix it?

---

### Post by LadyDoor on 2006-08-18
It looks like it's working, right? Were you trying to turn it off with conky --off? A lot of programs spit out error messages while they're working, even if they do work. It looks like you're using GNOME, so you might try pressing <alt>F2 and then typing **conky** in that prompt. See if it works.

---

### Post by LadyDoor on 2006-08-18
*adding any parameters you want to add, of course.

---

### Post by kpkeerthi on 2006-08-18
1. Enable double buffering:
Edit xorg.conf and add
```

Section "Module"
   Load "glx"
   **Load "dbe"**
   ...
EndSection

``` to enable double buffering extension. That helps reducing flickering when conky 'refreshes'.

2. Checkout [http://conky.sourceforge.net/](http://conky.sourceforge.net/) for sample conkyrc files and customize the way you want. Do refer to conky manual there. Choices are virtually unlimitted.

---

### Post by brotakul on 2006-08-20
thanks. it worked :D

---

### Post by RudolfMDLT on 2006-08-20
Hi,

The biggest graphical change I made to my system in breezy was with Gnome art... Please tell me, just in a nutshell, what you did/used to get such a cool menu system!

Thnx,

admiring noob:D

---

### Post by brotakul on 2006-08-20
i am using vista theme with vista icons. get some from [www.gnome-look.org](www.gnome-look.org)

ps: where can i get some .conkyrc configuration scripts which has screenshots with, so i can see how they look before i use them?

---

### Post by Perfect Storm on 2006-08-20
Have you tried their homepage?

---

### Post by brotakul on 2006-08-20
i will try it. anyway, i found a script that i like.

i have another problem now. if i set conky to run "in" background, all my shortcuts and icons on the background dissapear. i can see them only if i select the background space with my mouse but they dissapear again in a minute or so. this is not happening if i set conky to run in it's own window. 
how can i make it work running in background? or maybe just hide its process from the taskbar?

---

### Post by kerry_s on 2006-08-20
You should check out the making conky beautiful guide in the tips and tricks section, there's also a updated conky you can download and install.heres my conkyrc->
```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans:style=Bold:size=12

# Text alpha when using Xft
xftalpha 1

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 5

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 200
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
 ${color black}              Conky
${color black}CPU:${color black} ${freq} ${color black}mhz / Temp:${color black}$acpitemp ${color black}C 
${color black}Disk I/O:${color black} ${diskio}    ${color black}Uptime:${color black} $uptime 
${color black}Processes:${color black} $processes  ${color black}Running:${color black} $running_processes
${color black}CPU Usage:${color black} $cpu% ${color black}${cpugraph  20, 125 ffffff 0000ff}

${color black}RAM Usage:${color black} $mem of $memmax ${color black}- ${color black}$memperc% 
${color black}Swap Usage:${color black} $swap of $swapmax ${color black}- ${color black}$swapperc% 
${color black}File systems: ${color black}${fs_used /} of ${fs_size /}

${color black}Name                     PID     CPU%   MEM%
${color red} ${top name 1}         ${top pid 1} ${top cpu 1} ${top mem 1}
${color red} ${top name 2}         ${top pid 2} ${top cpu 2} ${top mem 2}
${color red} ${top name 3}         ${top pid 3} ${top cpu 3} ${top mem 3}
${color red} ${top name 4}         ${top pid 4} ${top cpu 4} ${top mem 4}
${color red} ${top name 5}         ${top pid 5} ${top cpu 5} ${top mem 5}

${color black}IN:${downspeed eth0} k/s ${color black}${downspeedgraph eth0 20,125 ff0000 0000ff}
${color black}OUT:${upspeed eth0} k/s ${color black}${upspeedgraph eth0 20,125 0000ff ff0000}
${color black}Netstat
${color red}${execi 12 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}

```

---

### Post by RudolfMDLT on 2006-08-20
Thnx brotakul, very nice!

 Artificial Intelligence, could you please put a link somewhere?

Thanks guys!

---

### Post by Perfect Storm on 2006-08-20
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by RudolfMDLT on 2006-08-20
> **Artificial Intelligence said:**
> [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

Thanks a lot! Really!:-D

---

### Post by brotakul on 2006-08-21
i still have a problem with conky. i installed lm-sensors and my CPU has about 32-34grd Celsius. in terminal, "sensors" command sais the same thing. but conky indicates me a temperature equal to 22grd Celsius, which is wrong. do i have to install any other sensors?

---

