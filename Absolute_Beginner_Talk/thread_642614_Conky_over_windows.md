---
title: "Conky over windows"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by RobotAlligator on 2007-12-16
How can I make conky stop going on top of windows?  I'm running firefox right now and I can see conky on top of firefox.  I just want it to be as close to an attachment to my wallpaper as possible.  theres also a slight backround wall i can see going around it.  is there any way to remove that?

background no
use_xft yes
xftfont Bitstream Vera Sans Mono:size=10
xftalpha 0.8
update_interval 5.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_colour hotpink
own_window_hints undecorated,below,skip_taskbar,sticky,skip_pager
double_buffer yes
minimum_size 280 5
draw_shades yes
draw_outline no
draw_graph_borders yes
stippled_borders 8
border_margin 4
border_width 1
maximum_width 155
default_color darkgrey
default_shade_color black
default_outline_color black
alignment bottom_right
gap_x 4
gap_y 4
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer no

TEXT
${color #5b6dad}${alignc}${nodename} ${uptime_short}

${color #5b6dad}CPU: ${color grey}$cpu%
${color #5b6dad} ${cpugraph 16,140 000000 7f8ed3}
${color #5b6dad}RAM: $color$mem/$memmax
${color #5b6dad} ${membar 6,140}
${color #5b6dad}Swap:$color$swap/$swapmax
${color #5b6dad} ${swapbar 6,140}

${color #5b6dad}ETH0 Down: $color${downspeed eth0}${alignr} k/s 
${color #5b6dad} ${downspeedgraph eth0 16,140 000000 7f8ed3 150}
${color #5b6dad}ETH0 Up:   $color${upspeed eth0}${alignr} k/s 
${color #5b6dad} ${upspeedgraph eth0 16,140 000000 7f8ed3 18}

${color #5b6dad}File systems:
${color #5b6dad}/       $color${fs_free /}
${color #5b6dad} ${fs_bar 6,140 /}
${color #5b6dad}storage $color${fs_free /mnt/storage}
${color #5b6dad} ${fs_bar 6,140 /mnt/storage}

${color #5b6dad}Processes:$color $processes | $running_processes
${color} Cpu usage    CPU
${color #ddaa00} ${top name 1}${offset -50} ${top cpu 1}
${color #5b6dad} ${top name 2}${offset -50} ${top cpu 2}
${color #5b6dad} ${top name 3}${offset -50} ${top cpu 3}
${color #5b6dad} ${top name 4}${offset -50} ${top cpu 4}

${color} Mem usage    MEM
${color #ddaa00} ${top_mem name 1}${offset -50} ${top_mem mem 1}
${color #5b6dad} ${top_mem name 2}${offset -50} ${top_mem mem 2}
${color #5b6dad} ${top_mem name 3}${offset -50} ${top_mem mem 3}
${color #5b6dad} ${top_mem name 4}${offset -50} ${top_mem mem 4}

${color #5b6dad}# Connections   
$color In: ${tcp_portmon 1 32767 count}  Out: ${tcp_portmon 32768 61000 count}${alignr}


thats my file

---

### Post by spiderbatdad on 2007-12-16
[QUOTE=RobotAlligator;3964844]How can I make conky stop going on top of windows?  I'm running firefox right now and I can see conky on top of firefox.  I just want it to be as close to an attachment to my wallpaper as possible.  theres also a slight backround wall i can see going around it.  is there any way to remove that?

background no
use_xft yes
xftfont Bitstream Vera Sans Mono:size=10
xftalpha 0.8
update_interval 5.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_colour hotpink
own_window_hints undecorated,below,skip_taskbar,sticky,skip_pager
double_buffer yes


Add the line "on_bottom yes" just above where you have "own_window yes" NOTE: edited from original response.

---

### Post by gupta_sumesh63 on 2007-12-17
Hi,
Where can I find the config file for conky where I can make the changes.
I have the same problems.
Thnx.

---

### Post by spiderbatdad on 2007-12-17
usually conky doesn't come with one except as a sample. You have to create one in your home directory called .conkyrc. The dot means it is hidden, so open your home directory and choose the view tab, then select "show hidden files." You should se it if you have one. I was reading a little from the conky man, and I'm not sure what I suggested will solve the problem. For example the "sticky" option is to spread conky across all desktops. I would look for an option that says "on top." Anyway there is a great thread in these forums of example .conkyrc files. You can copy or use as a guide to build your own.[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)


ahh...i think i found it: add the line "on_bottom yes" (no quotes) just above where the original poster has "own_window yes."

---

