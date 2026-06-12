---
title: "Conky want show"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-09-24
Hi when i get this when i try to run conky:
```

czepluch@ubuntu:~$ conky
Conky: /home/czepluch/.conkyrc: 50: no such configuration: 'colour'
Conky: /home/czepluch/.conkyrc: 115: no such configuration: 'certain'
Conky: unknown variable czepluch
Conky: forked to background, pid is 4587

```

Here is my conky: 
```

# conky config
# edited by notwen @ efnet

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

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background
colour here
#own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 130 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 5

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color green
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 18
gap_y 48

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

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects
certain objects.
use_spacer yes
#Note: doesn't work in conky 1.2 =(

TEXT
$Czepluch
$sysname $kernel
${time %A %B %e, %G}
${time %I:%M:%S}${time %p}

CPU:
temp: ${acpitemp}C
cpu1: ${cpu cpu1}% ${cpubar cpu1}
top usage:
${top name 1}$alignr${top cpu 1}%
${top name 2}$alignr${top cpu 2}%
${top name 3}$alignr${top cpu 3}%

MEMORY:
ram: $memperc% $membar
swap: $swapperc% $swapbar
top usage:
${top_mem name 1}$alignr${top_mem mem 1}%
${top_mem name 2}$alignr${top_mem mem 2}%
${top_mem name 3}$alignr${top_mem mem 3}%

PARTITIONS:
/ ${fs_used_perc /}% ${fs_bar /}
/home ${fs_used_perc /home}% ${fs_bar /home}
/media/sda2 ${fs_used_perc /media/sda2}% ${fs_bar /media/sda2}

NETWORK (${addr eth0}):
downloads:$alignr ${downspeed eth0}kb/s
uploads:$alignr     ${upspeed eth0} kb/s

WEATHER:
${execi 150 /home/czepluch/.local/weather.sh 4281}

MUSIC:
${execi 1 ~/.local/amarok.sh artist}
${execi 1 ~/.local/amarok.sh title}
${execibar 1 ~/.local/amarok.sh progress}
"${execi 1 ~/.local/amarok.sh album}"
${execi 1 ~/.local/amarok.sh year} - ${execi 1 ~/.local/amarok.sh genre}

FORTUNE:
${execi 120 fortune -s | fold -w120}

```

---

### Post by raul_ on 2007-09-24
Go to line 50 and 115 and add a # in the beggining of the line

---

