---
title: "[SOLVED] setting default colors in conky"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by JPotter on 2008-02-02
I tried to switch over to the intelligent method of assigning colors in conky today. That is, using color0 - color9. I switched all of the code over (old version is safe), but it won't recognize any of the color settings.

Here is a copy of my .conkyrc, any suggestions will be appreciated.

```
post_21_kernel yes

background yes

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes

double_buffer yes

# Minimum size of text area
minimum_size 150 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around graphs
draw_graph_borders yes

# border margins
border_margin 0

# border width
border_width 0

# Default colors and also border colors
default_color white
color0 #ddaa00
color1 lightgrey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 30

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename - $sysname $kernel on $machine
$time
$stippled_hr
${color1}Uptime:${color} $uptime ${color1}- Load:${color} $loadavg
${color1} CPU0: ${color0}${freq_g 1}GHz  ${color1}${cpu cpu1}%${cpubar cpu1}
${color1}${cpugraph 0000ff 00ff00}
${color1}Processes:${color} $processes ${alignr} ${color grey}Active:${color} $running_processes
${color}$stippled_hr
${color1}RAM${color0}  $memperc% ${color1}${membar}
${color1}Swap${color0}  $swapperc% ${color1}${swapbar}
${color1}/  ${color0}  ${fs_used_perc /}% ${color1}${fs_bar /}
${color1}hdc3 ${color0}${fs_used_perc /media/hdc3}% ${color1}${fs_bar /media/hdc3}
${color1}hdd1 ${color0}${fs_used_perc /media/hdd1}% ${color1}${fs_bar /media/hdd1}
${color}$stippled_hr
${color1}Processor Usage      PID    CPU%   MEM%
${color0} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color1}Memory Usage
${color0} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color} ${top_mem name 4} ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}
$stippled_hr
${color1}Networking: (${color0}${addr eth0}${color1})
 Down:${color0} ${downspeed eth1} k/s${color1} ${offset 50}Up:${color0} ${upspeed eth1} k/s
${color1}${downspeedgraph eth1 32,115 ff0000 0000ff} ${color1}${upspeedgraph eth1 32,115 0000ff ff0000}
${color1}Connections${alignr}Ports
${color1} Outbound: ${color0}${tcp_portmon 32768 61000 count} ${color1}Inbound: ${color0}${tcp_portmon 1 32767 count} ${alignr}${color1} ALL: ${color0}${tcp_portmon 1 65535 count}
${color1}Outbound Connection ${alignr} Remote Service/Port
 ${color0}${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}${color}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
 ${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
 ${tcp_portmon 32768 61000 rhost 6} ${alignr} ${tcp_portmon 32768 61000 rservice 6}
 ${tcp_portmon 32768 61000 rhost 7} ${alignr} ${tcp_portmon 32768 61000 rservice 7}
 ${tcp_portmon 32768 61000 rhost 8} ${alignr} ${tcp_portmon 32768 61000 rservice 8}
 ${tcp_portmon 32768 61000 rhost 9} ${alignr} ${tcp_portmon 32768 61000 rservice 9}
 ${tcp_portmon 32768 61000 rhost 10} ${alignr} ${tcp_portmon 32768 61000 rservice 10}
${color1}Inbound Connection ${alignr} Local Service/Port
 ${color0}${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}${color}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
 ${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}
 ${tcp_portmon 1 32767 rhost 7} ${alignr} ${tcp_portmon 1 32767 lservice 7}
 ${tcp_portmon 1 32767 rhost 8} ${alignr} ${tcp_portmon 1 32767 lservice 8}
 ${tcp_portmon 1 32767 rhost 9} ${alignr} ${tcp_portmon 1 32767 lservice 9}
 ${tcp_portmon 1 32767 rhost 10} ${alignr} ${tcp_portmon 1 32767 lservice 10}
```

---

### Post by spiderbatdad on 2008-02-03
try removing the hash sign. so, color0 ddaa00. Otherwise looks like it should work.

---

