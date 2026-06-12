---
title: "where is store  .conkyrc"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2007-01-08
Hi i am use ubuntu 6.10 with kde3.5. i want to open my conky configuration script file where is store the file.

---

### Post by johnnymac on 2007-01-08
It goes in your home directory.  So save it to:

/home/<your_user_name>/.conkyrc

---

### Post by RichJacot on 2007-01-08
Or you can save it anywhere and then use the conky -c <file/location/here> 
to start conky.  If you don't use the -c option, your home directory is the default.

---

### Post by lucky_chouhan on 2007-01-08
i am not find any folder and file .conky

[IMG]http://www.freeimagehosting.net/uploads/5901b82f6c.png[/IMG]
please help

---

### Post by lucky_chouhan on 2007-01-08
ok solve my problem create my own conky script.

---

### Post by Waappu on 2007-01-08
Hi

If you just instal conky you need to create that file. Open text editor and copy e.g. all from [here]("http://koti.mbnet.fi/waappu/conky/conkyrc_ver3") to it and save it to your home foled at name .conkycr

---

### Post by johnnymac on 2007-01-08
It's not a folder...it's just a file - a hidden configuration file.  So just save whatever configuration you've created as:

/home/<your_user_name>/.conkyrc

---

### Post by lucky_chouhan on 2007-01-08
plz anyone give me simple and transparent conky script.

---

### Post by RichJacot on 2007-01-09
Maybe not as simple as you'd like, but here's mine.  You'll need to modify the disk usage lines and where it grabs the weather from(or just remove it).

```
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

#rj ${execi 12 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}

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
#rj default_color grey
default_color white

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
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${top_mem name 1} ${top_mem pid 1}   ${top_mem cpu 1}    ${top_mem mem 1}
${top_mem name 2} ${top_mem pid 2}   ${top_mem cpu 2}    ${top_mem mem 2}
${top_mem name 3} ${top_mem pid 3}   ${top_mem cpu 3}    ${top_mem mem 3}
${top_mem name 4} ${top_mem pid 4}   ${top_mem cpu 4}    ${top_mem mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
home:  ${fs_free_perc /spfs/home}%   ${fs_bar 6 /spfs/home}$color
 ftp:  ${fs_free_perc /spfs/ftp}%   ${fs_bar 6 /spfs/ftp}
logs:  ${fs_free_perc /spfs1/logs_repository}%   ${fs_bar 6 /spfs1/logs_repository}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

${execi 60 /usr/bin/pymetar KDFW}

```

---

### Post by lucky_chouhan on 2007-01-09
thank you very much i try and reply.

---

### Post by kerry_s on 2007-01-09
Here's my conkyrc. Just download it & rename it to .conkyrc then just put it in your home folder.

---

### Post by lucky_chouhan on 2007-01-09
sreenshot

---

### Post by Ben Sprinkle on 2007-01-09
Press  CTRL+H at your home folder to see hidden files, all hidden files begin with a .
Then you will be able to see your files.

---

### Post by kerry_s on 2007-01-09
> **lucky_chouhan said:**
> sreenshot

Sure thing->

---

