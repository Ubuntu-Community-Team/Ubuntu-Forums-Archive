---
title: "[SOLVED] conky wont go into background"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by clancymf on 2007-10-27
I have install conky and like it.  The only problem I have is that it is always in front (i.e it wont go into the background (see screenshot)

Any ideas.  Thanks for you help,
Regards,
Mick

---

### Post by n3tfury on 2007-10-27
post your .conkyrc file within the code brackets <code></code> so we can take a look

---

### Post by clancymf on 2007-10-27
<code># UBUNTU-CONKY
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

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
hda1:  ${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}$color
hdb3:  ${fs_free_perc /media/hdb3}%   ${fs_bar 6 /media/hdb3}

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
${execi 120 fortune -s | fold -w50}</code>

---

### Post by n3tfury on 2007-10-27
hm...

copy and paste this into the top of the conkyrc file

```
# set to yes if you want Conky to be forked in the background
background no
```

---

### Post by n3tfury on 2007-10-27
^^

---

### Post by clancymf on 2007-10-27
Seemed to do the trick.  

Thank you very much. 
:)

---

### Post by n3tfury on 2007-10-27
you're welcome.  can you please mark you thread as solved?  thanks man.

---

### Post by ozp on 2007-10-29
My conky starts up in preference > session as "conky"

it always starts in front of everything and somethimes with a bigger font (bigger size)

I have to kill the process and then start again with alt + F2 as "conky"

Then it goes ok


my config file called .conkyrc under my /home/myself

```

# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

#own_window no
#own_window_transparent no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Liberation Mono Italic:size=9

uppercase no

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 3

# Draw shades?
draw_shades yes

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

# Text alignment, other possible values are commented
#minimum_size 10 10
gap_x 13
gap_y 45
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

# Subtract file system buffers from used memory?
no_buffers yes

# ideas that I didn't want to lose
# ${time %a  %b  %d}${alignr -25}${time %k:%M}

TEXT
${alignc}${color #FFFFFF}$sysname kernel $kernel 
${alignc}${color #FFFFFF}${exec cat /etc/issue.net} on $machine host $nodename

${color #FFFFFF}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color #FFFF99} ${freq_dyn}Mhz
${color #FFFFFF}Current CPU usage & temp:${color #FFFF99}  ${cpu}%${color #FFFFFF}, ${color #FFFF99}${acpitemp}C ${color #FFFFFF}

${color #FFFFFF}Plug/battery status:${color #FFFF99}  $acpiacadapter, $battery

${color #FFFFFF}Load average:${color #FFFF99}   $loadavg

${color #FFFFFF}CPU usage         ${alignr}PID     CPU%   MEM%
${color #FFFF99} ${top name 1}${alignr}${top pid 1}   ${top cpu 1}   ${top mem 1}
${color #FFFF99} ${top name 2}${alignr}${top pid 2}   ${top cpu 2}   ${top mem 2}
${color #FFFF99} ${top name 3}${alignr}${top pid 3}   ${top cpu 3}   ${top mem 3}

${color #FFFFFF}Mem usage
${color #FFFF99} ${top_mem name 1}${alignr}${top_mem pid 1}   ${top_mem cpu 1}   ${top_mem mem 1}
${color #FFFF99} ${top_mem name 2}${alignr}${top_mem pid 2}   ${top_mem cpu 2}   ${top_mem mem 2}
${color #FFFF99} ${top_mem name 3}${alignr}${top_mem pid 3}   ${top_mem cpu 3}   ${top_mem mem 3}

${color #FFFFFF}RAM Usage:${color #FFFF99} $mem/$memmax - $memperc% $membar

${color #FFFFFF}Swap Usage:${color #FFFF99} $swap/$swapmax - $swapperc% ${swapbar}

${color #FFFFFF}Processes:${color #FFFF99} $processes  ${color #FFFFFF}Running:${color #FFFF99} $running_processes ${color #FFFFFF}

${color #FFFFFF}Hard disks:
  / ${color #FFFF99}${fs_used /}/${fs_size /} ${fs_bar /}
  ${color #FFFFFF}/home ${color #FFFF99}${fs_used /home}/${fs_size /home} ${fs_bar /home}
  ${color #FFFFFF}hdd temp: ${color #FFFF99}${execi 300 nc localhost 7634 | cut -c22-23 ;} C

${color #FFFFFF}Wireless Networking:
  ${color #FFFFFF}ESSID: ${color #FFFF99}${wireless_essid eth1}  ${color #FFFFFF}AP: ${color #FFFF99}${wireless_ap eth1}
  ${color #FFFFFF}${exec iwconfig eth1 | grep "Frequency" | cut -c 25-45}
  ${color #FFFFFF}Mode: ${color #FFFF99}${wireless_mode eth1}  ${color #FFFFFF}Bitrate: ${color #FFFF99}${wireless_bitrate eth1}
  ${color #FFFFFF}Local IP ${color #FFFF99}${addr eth1}  ${color #FFFFFF}Link Quality: ${color #FFFF99}${wireless_link_qual_perc eth1}
  ${color #FFFFFF}total download: ${color #FFFF99}${totaldown eth1}     
  ${color #FFFFFF}total upload: ${color #FFFF99}${totalup eth1}
  ${color #FFFFFF}download speed: ${color #FFFF99}${downspeed eth1} k/s${color #FFFF99} ${color #FFFFFF}   upload speed: ${color #FFFF99}${upspeed eth1} k/s
  ${color #FFFF99}${downspeedgraph eth1 15,150 ff0000 0000ff} $alignr${color #FFFF99}${upspeedgraph eth1 15,150 0000ff ff0000}

${color #FFFFFF}Wired Networking:
  ${color #FFFFFF}Local IP ${color #FFFF99}${addr eth0} ${color #FFFFFF}
  ${color #FFFFFF}total download: ${color #FFFF99}${totaldown eth0}     
  ${color #FFFFFF}total upload: ${color #FFFF99}${totalup eth0}
  ${color #FFFFFF}download speed: ${color #FFFF99}${downspeed eth0} k/s${color #FFFF99} ${color #FFFFFF}   upload speed: ${color #FFFF99}${upspeed eth0} k/s
  ${color #FFFF99}${downspeedgraph eth0 15,150 ff0000 0000ff} $alignr${color #FFFF99}${upspeedgraph eth0 15,150 0000ff ff0000}

${color #FFFFFF}Public IP ${color #FFFF99}${execi 3605 curl 'http://www.whatismyip.org'}

${color #FFFFFF}Port(s) / Connections:
${color #FFFFFF}Inbound: ${color #FFFF99}${tcp_portmon 1 32767 count}  ${color #FFFFFF}Outbound: ${color #FFFF99}${tcp_portmon 32768 61000 count}  ${color #FFFFFF}Total: ${color #FFFF99}${tcp_portmon 1 65535 count}
${color #FFFFFF}Outbound Connection ${alignr} Remote Service/Port${color #FFFF99}
 ${tcp_portmon 1 65535 rhost 0} ${alignr} ${tcp_portmon 1 65535 rservice 0}
 ${tcp_portmon 1 65535 rhost 1} ${alignr} ${tcp_portmon 1 65535 rservice 1}
 ${tcp_portmon 1 65535 rhost 2} ${alignr} ${tcp_portmon 1 65535 rservice 2}
 ${tcp_portmon 1 65535 rhost 3} ${alignr} ${tcp_portmon 1 65535 rservice 3}
 ${tcp_portmon 1 65535 rhost 4} ${alignr} ${tcp_portmon 1 65535 rservice 4}
 ${tcp_portmon 1 65535 rhost 5} ${alignr} ${tcp_portmon 1 65535 rservice 5}

```

---

