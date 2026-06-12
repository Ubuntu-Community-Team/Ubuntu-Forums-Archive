---
title: "Conky configuration for MacBook Pro 5.1"
date: 2009-05-28
forum: Apple Hardware Users
---

### Post by Aybara on 2009-05-28
I just installed Ubuntu on my MBP 5.1, and now I would like to use Conky. Anyone got a nice configuration file for this hardware?

---

### Post by Nikos.Alexandris on 2009-11-10
> **Aybara said:**
> I just installed Ubuntu on my MBP 5.1, and now I would like to use Conky. Anyone got a nice configuration file for this hardware?

Here is my **/etc/conky/conky.conf** (currently):
> alignment bottom_left
background yes
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont Droid Sans Mono:size=7.5
gap_x 5
gap_y 45
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
own_window_transparent yes
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${scroll 20 $nodename - $sysname $kernel on $machine | }
$hr
${color grey}Uptime:$color $uptime
#${color grey}Frequency (in MHz):$color $freq
#${color grey}Frequency (in GHz):$color $freq_g
${color grey}Frequency:$color $freq_g GHz
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}Temperatures:
${color grey} CPU:
${color grey} GPU:$color ${nvidia temp} Celsius degrees ${color grey}~$color ${nvidia gpufreq} MHz
${color grey}Fans:
${color grey} $color ${exec sensors | grep Left}
${color grey} $color ${exec sensors | grep Right}
$hr
${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
 Up:$color ${upspeed eth2} ${color grey} Down:$color ${downspeed eth0}
$hr
${color grey}Name              PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

I want to add more (1st and 2nd CPU, free disk space for all mounted partitions, etc.).

---

### Post by Nikos.Alexandris on 2009-11-10
Conly frequently disappears and it only takes to execute *conky* in the terminal to reappaer. But this is not a solution. Anybody knows how to have conky parmanently showing-up in the desktop?

---

### Post by Nikos.Alexandris on 2009-11-19
A bit of editing...

> **Nikos.Alexandris said:**
> I want to add ... 1st and 2nd CPU...

```
alignment bottom_left
background yes
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont Droid Sans Mono:size=7.5
gap_x 5
gap_y 45
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
own_window_transparent yes
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${scroll 20 $nodename - $sysname $kernel on $machine | } ${color grey}Uptime:$color $uptime
# ----------------------------------------------------------------------------
$hr

# CPUs
${color grey}Cores
#${color grey}Frequency (in MHz):$color $freq
 ${color grey}(1) ${color grey}Frequency:$color ${freq_g 1} GHz ${color grey}Usage:$color ${cpu cpu1}% ${cpubar 4}
 ${color grey}(2) ${color grey}Frequency:$color ${freq_g 2} GHz ${color grey}Usage:$color ${cpu cpu2}% ${cpubar 4}

# Temperatures
${color grey}Temperatures
${color grey} CPU:
${color grey} GPU:$color ${nvidia temp} Celsius degrees ${color grey}~$color ${nvidia gpufreq} MHz

# Fans
${color grey}Fans
${color grey} $color ${exec sensors | grep Left}
${color grey} $color ${exec sensors | grep Right}

# Usage
${color grey}Usage
 ${color grey}RAM $color $mem/$memmax - $memperc% ${membar 4}
 ${color grey}Swap $color $swap/$swapmax - $swapperc% ${swapbar 4}
 ${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes

  ${color grey}Name               PID   CPU%   MEM%
  ${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
  ${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
  ${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
  ${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

# ----------------------------------------------------------------------------
$hr

# File systems
${color grey}File systems
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}

${color grey}Networking
 Up:$color ${upspeed eth2} ${color grey} Down:$color ${downspeed eth2}
```

Anybody else with a simple and useful conky setup?

---

