---
title: "Problems with conky and desktop icons"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ahoman66 on 2007-06-24
I have a problem with conky and desktop icons. My icons disappear when conky starts and only appear when I move the mouse over them. Point me in the right direction and I will fix this. 

Thanks 
Allen

---

### Post by shearn89 on 2007-06-24
you could try checking your .conkyc file; make sure you have the following settings:

```

own_window yes
own_window_type utility
own_window_hints undecorated,below,skip_taskbar

```

Let me know if that helps.

---

### Post by ahoman66 on 2007-06-24
Thank you for the help but the problem continues.

Thanks 
Allen

---

### Post by Seisen on 2007-06-24
Post you conky config file

---

### Post by ahoman66 on 2007-06-25
Here it is...

```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
own_window_colour hotpink
own_window_type utility
own_window_hints undecorated,below,skip_taskbar

# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 280 5
#maximum_width 150

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 10

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color black
default_shade_color red
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 13
gap_y 13
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# boinc (seti) dir
# seti_dir /opt/seti


TEXT

${color lightgrey}System Info ${hr 2}
${color #000000}$nodename - $sysname $kernel on $machine
${color #000000}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #ff0000} ${cpu}% ${cpubar}
${color black}${cpugraph 000000 ff0000}
${color lightgrey}RAM Usage:${color #ff0000} $mem/$memmax - $memperc% $membar
${color lightgrey}Swap Usage:${color #ff0000} $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes

${color lightgrey}Networking Info ${hr 2}
${color lightgrey} Down:${color #000000} ${downspeed ath0} k/s${color lightgrey} ${offset 70}Up:${color #ff0000} ${upspeed ath0} k/s
${color black}${downspeedgraph ath0 32,150 000000 ff0000} $alignr${color black}${upspeedgraph ath0 32,150 000000 ff0000}
${color lightgrey}Wireless Networking:
${color lightgrey}ip address: ${color #000000}${addr ath0}
${color lightgrey}status: ${color #000000}${linkstatus ath0} % 
${color lightgrey}essid: $color${exec iwconfig ath0 | sed 's/  /\n/g' | grep ESSID | sed 's/ESSID:"//'| sed 's/"//'}

${color lightgrey}Processes ${hr 2}
${color}Name              PID     CPU%   MEM%
${color #ff0000} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}


${color lightgrey}Memory ${hr 2}
${color}Name              PID     CPU%   MEM%
${color #ff0000} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color lightgrey} ${top_mem name 4} ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}


${color lightgrey}Port Connections ${hr 2}
${color lightgrey}Port(s)${offset 48}Connections:
${color lightgrey} ALL: ${alignc}${tcp_portmon 1 65535 count}
${color lightgrey} mpd:${alignc}${tcp_portmon 6600 6600 count}
${color lightgrey} 1 - 1024:${alignc}${tcp_portmon 1 1024 count}
${color lightgrey} 1025 - 65535:${alignc}${tcp_portmon 1024 65535 count}
${color lightgrey}Remote Address:${alignr} Local Service/Port:
${color}${tcp_portmon 1 1024 rport 0} 
${color}${tcp_portmon 1 65535 rhost 0}${alignr}${tcp_portmon  1 65535 lservice 0}
${color}${tcp_portmon 1 65535 rhost 1}${alignr}${tcp_portmon  1 65535 lservice 1}
${color}${tcp_portmon 1 65535 rhost 2}${alignr}${tcp_portmon  1 65535 lservice 2}
${color}${tcp_portmon 1 65535 rhost 3}${alignr}${tcp_portmon  1 65535 lservice 3}
${color}${tcp_portmon 1 65535 rhost 4}${alignr}${tcp_portmon  1 65535 lservice 4}


```

Thanks
Allen

---

### Post by shearn89 on 2007-06-25
I don't think you need "on_bottom" if you've set "own_window_hints" to "below"
You also have "own_window yes", then "own_window no" - you need "yes" for it to work with nautilus -  I think this is the answer.

Try turning on "maxmimum_width", and set it to something like 300 (depending on how much you have to fit <->).

Post the results.

---

### Post by ahoman66 on 2007-06-25
After I posted the file I figured out the problem here is the fix. I did also find the errors you stated. Thank you very much shearn89. I also turned on width to 300.  Now I have another problem. The icon did not flicker but when I went to delete the icon conky went away also.

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type desktop

Thanks for all the help. I am off to work...

Thanks
Allen

---

### Post by ahoman66 on 2007-06-25
Sorry for the double post but fixed the problem. 

changed own_window_type desktop

to this own_window_type override

problem solved. Thanks again for the help.

Later
Allen

---

