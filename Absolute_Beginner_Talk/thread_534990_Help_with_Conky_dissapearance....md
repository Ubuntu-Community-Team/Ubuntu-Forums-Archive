---
title: "Help with Conky dissapearance..."
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by madu on 2007-08-25
Hello guys...

I'm using 7.04 and has the problem of conky disappearing every time I click on the dekstop. I have put conky in sessions to begin at startup and it does start when I log into Ubuntu and works fine.. but if I click the desktop it just disappears... even if  I start it again same situation.. disappears when clicked the desktop... any suggestions are greatly welcome.. my conky config file is given below:

> background yes
font 7x13
use_xft yes
xftfont Monospace:size=9
on_top yes

update_interval 1.0

total_run_times 0

own_window yes
own_window_type desktop 
 

own_window_transparent yes

double_buffer yes

minimum_size 280 5

draw_shades no
draw_outline no
draw_borders no
stippled_borders 8
border_margin 4
border_width 1

default_color white
default_shade_color black
default_outline_color black

alignment top_right 

maximum_width 308

gap_x 15
gap_y 25

no_buffers yes

uppercase no

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale no

use_spacer no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color black}$nodename   linux-$kernel${alignr}${time %T}
${color black}System:
${color black}Cpu usage: ${color blue}${cpu 0}%
${color #5b6dad}Uptime:${color #7f8ed3} $uptime ${color #5b6dad}- Load:${color #7f8ed3} $loadavg
${freq_dyn}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 1 000000 ffffff}
${color black} RAM Usage:${color #7f8ed3} $mem/$memmax - $memperc% ${membar}
${color black} Swap Usage:${color #7f8ed3} $swap/$swapmax - $swapperc% ${swapbar}
${color black} Processes:${color #7f8ed3} $processes  ${color black}Running:${color #7f8ed3} $running_processes

${color black}Networking (ETHERNET):
 ${color black}Down:${color #7f8ed3} ${downspeed eth0} k/s${color black}${offset 80}Up:${color #7f8ed3} ${upspeed eth0} k/s
 ${color #000000}${upspeedgraph eth0 32,150 000000 7f8ed3} ${color #000000}${downspeedgraph eth0 32,150 000000 7f8ed3}
 ${color black}Address: ${color #7f8ed3}${addr eth0}${alignr}${color black}TCP Connections: ${color #7f8ed3}${tcp_portmon 1 65535 count}

${color black}Networking (WIRELESS):
 ${color black}Down:${color #7f8ed3} ${downspeed eth1} k/s${color black}${offset 80}Up:${color #7f8ed3} ${upspeed eth1} k/s
 ${color #000000}${upspeedgraph eth1 32,150 000000 7f8ed3} ${color #000000}${downspeedgraph eth1 32,150 000000 7f8ed3}
 ${color black}Address: ${color #7f8ed3}${addr eth1}${alignr}${color black}TCP Connections: ${color #7f8ed3}${tcp_portmon 1 65535 count}

${color black}Name              PID     CPU%   MEM%
${color blue} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #7f8ed3} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #7f8ed3} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}

${color black}File Systems:
 ${color black} ${color #7f8ed3}${fs_used /}/${fs_size /} ${color #7f8ed3}${fs_bar /}

${color black}Battery status: $battery



Best regards,
 Madu.

---

### Post by felicity on 2007-08-25
Try using other own_window_type variations:
# try override, or normal
own_window_type desktop  <-------
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky

---

### Post by madu on 2007-08-25
> **felicity said:**
> Try using other own_window_type variations:
# try override, or normal
own_window_type desktop  <-------
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky

Thanks a lot man.. OVERRIDE did the trick.. awesome...  thanks again bro...

Best regards,
 Madu.

---

### Post by psyopper on 2007-08-26
You might be careful about using override - it may cause other strange issues, especially when using alternate/additional window managers (like Beryl or Compiz).

I might suggest the following instead:
```

own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

```

I have the feeling it was the **background yes** with **own_window_type desktop** that was causing your issue.

---

