---
title: "Temperature monitoring"
date: 2011-06-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mr_mop on 2011-06-26
I have an Asus M4A78LT-M LE mobo.

I am using sensors and conky to display the hw temps on my desktop.

The problem I am having is, the devices I am using keep moving.

I have to edit the .conkyrc file each time I boot.

Does anyone have experience of sensors, conky and this mobo?

My .conkyrc file is:

```

background no
cpu_avg_samples 2
net_avg_samples 2
out_to_console no
use_xft yes
xftfont 8x13
xftalpha 0.8
#on_bottom deprecated.
#on_bottom yes
# Set conky on the bottom of all other applications
own_window_hints below
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
#border_margin 4
border_width 1
default_color white
default_shade_color grey
default_outline_color black
gap_x 3
gap_y 3
alignment top_left
use_spacer none
no_buffers yes
uppercase no

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

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer left
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
#font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
#border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
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
#${freq}MHz   Load: ${loadavg}   Temp: ${platform it87.656 temp 1}C   ${platform it87.656 fan 1}RPM
${freq}MHz   Load: ${loadavg}
${execi 2 cat /sys/class/hwmon/hwmon1/temp1_label}: ${execi 2 cat /sys/class/hwmon/hwmon1/temp1_input | cut -c1,2}C ${execi 2 cat /sys/class/hwmon/hwmon1/fan1_label}: ${execi 2 cat /sys/class/hwmon/hwmon1/fan1_input}RPM
${execi 2 cat /sys/class/hwmon/hwmon1/temp2_label}: ${execi 2 cat /sys/class/hwmon/hwmon1/temp2_input | cut -c1,2}C ${execi 2 cat /sys/class/hwmon/hwmon1/fan2_label}: ${execi 2 cat /sys/class/hwmon/hwmon1/fan2_input}RPM
$cpubar
PCI0: ${execi 2 cat /sys/bus/pci/drivers/k10temp/000*/temp1_input | cut -c1,2}C
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
Home:  ${fs_free_perc /home}%   ${fs_bar 6 /home}$color

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/syslog | fold -w50}

```

The parts giving me a problem are those using:
/sys/class/hwmon/hwmonX

Both /sys/class/hwmon/hwmon0 and /sys/class/hwmon/hwmon1 are present.
Sometime 0 is in use, sometimes 1 is in use.

Any ideas?

Thanks.

---

