---
title: "Conky Help"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Depressed Man on 2007-07-24
I'm using a config I found in the post your conky config with screenshot thread in the community cafe. But I want to make modifications to it. 

```
vforviktor@vendetta:~$ conky
Conky: statfs '/media/sda2': No such file or directory
Conky: forked to background, pid is 28063
vforviktor@vendetta:~$ 
Conky: statfs '/media/sda2': No such file or directory
Conky: desktop window (1200061) is subwindow of root window (4d)
Conky: window type - normal
Conky: drawing to created window (4200002)
Conky: drawing to double buffer
Conky: statfs '/media/sda2': No such file or directory
Conky: statfs '/media/sda2': No such file or directory

```

I don't have an sda2 drive, I do have hda drives though. How do I get the config to show those instead.  I also have a dual core CPU so how can I get the graph to show two charts? 

And lastly, how do I set the conky config to remember it's last position I placed it in? The default position it starts up in covers up my icons on the desktop.

```
background yes
use_xft yes
xftfont Trebuchet\ MS:size=8
xftalpha 0.1
update_interval 2.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color red
default_outline_color green
alignment bottom_left
gap_x 8
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
$alignc ${color #9fb6cd} $sysname $kernel $machine $color
Core: $alignr Opteron 165 ${freq_g} Ghz
Uptime: $alignr${uptime}
$alignc ${time %a, } ${time %e %B %G} | ${time %I:%M %P}
$alignc --------------------------
$alignc${cpugraph cpu0 16,50 ffffff ffffff}
CPU:  ${cpu cpu1}% ${cpubar cpu1}
${hr 1} $color
Cached Memory: $alignr $cached
RAM $alignc $mem / $memmax $alignr $memperc%
$membar
Filesystem $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}
${if_mounted /media/sda2} ${color #9fb6cd} $alignc Windows Partition Mounted
$alignc ${fs_used /media/sda2} / ${fs_size /media/sda2} $color $endif
${hr 1}
${execi 180 fortune -s | fold -w38}
${hr 1}
$alignc ${color #9fb6cd}Processes $color
$running_processes Running $alignr $processes Total

Top CPU Hogs: $alignr CPU% RAM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 2}${top mem 3}

Top RAM Hogs: $alignr CPU% RAM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}
${hr 1}
Network [eth1] $alignr (${addr eth1})
Sending: $alignr ${upspeedf eth1}kb/s
Receiving: $alignr ${downspeedf eth1}kb/s

Connections: ${tcp_portmon 32768 61000 count} ${alignr} Service/Port
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
```

Edit: And how do I set it so it's transparent (so it fits in with the desktop color)

---

### Post by raja on 2007-07-24
Instead of /media/sda2, insert the names of the directories that you want to monitor. It can be '/' for example.
I dont know if it is possible to get the parameters for both cpus - there is only one variable in conky, so I dont know how it works with a dual-core.
The placement is based on the alignment and the gap values. The current config tells that you want a x-gap of 8 and y-gap of 48 starting from bottom-left. The maximum width is 200 pixels from there. Change these as you want.
With the current config, conky should be transparent as far as I know.

---

### Post by Depressed Man on 2007-07-25
thanks for the help! I just realized it was transparent. It just looks odd when I zoom out in the cube with Compiz Fusion since it draws it's own transperancy over it.

---

