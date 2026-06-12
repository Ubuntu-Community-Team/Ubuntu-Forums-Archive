---
title: "[SOLVED] Help with .conkyrc"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by amazingtaters on 2007-08-14
So, I installed conky and I'm trying to figure out how to get it to look the way I want. So far what I know is that I need a .conkyrc file, and its gotta be in the home folder. I found one in an old thread here on the forums where a lot of people were posting the code, this is the one I want:

```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=10

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 160 5

# Maximum width
maximum_width 160

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

#  unused text
#  Current:${alignr}${execi 20 /home/tonyt/scripts/.conky_eth2} Mbits/sec
#  hda Temp:${alignr}${execi 1800 /home/tonyt/scripts/.hdtemp}

TEXT
$sysname $kernel
Uptime:$alignr$uptime
${time %A}$alignr${time %F}

Hostname:$alignr$nodename
ath0:$alignr${addr ath0}
Signal:$alignr${linkstatus  ath0}
Current:${alignr}${execi 20 /home/tonyt/scripts/.conky_ath0} Mbits/sec
eth2:$alignr${addr eth2}
Signal:$alignr${linkstatus  eth2}
eth0:$alignr${addr eth0}
 
RAM: $mem/$memmax ${color lightgray}$membar$color
CPU0 ${cpu cpu1}% ${color lightgray}${cpubar cpu1}$color
CPU1 ${cpu cpu2}% ${color lightgray}${cpubar cpu2}$color

hda3: ${fs_used_perc /}% ${color lightgray}${fs_bar /}$color
hda5: ${fs_used_perc /mnt/FILES}% ${color lightgray}${fs_bar /mnt/FILES/}$color
Swap: $swapperc% ${color lightgray}$swapbar$color

Processes: $processes ${alignr}Running: $running_processes
```

Now, how do I save this, aka what filetype and all that, and how do I get conky to load this and have this applied to it? Thanks in advance!

---

### Post by amazingtaters on 2007-08-14
Okay, never mind, conky is running. I will have to find out how to change text colour but I can do that on my own I believe.

---

### Post by skwishybug on 2007-08-14
Check out: [http://conky.sourceforge.net/](http://conky.sourceforge.net/)
 
There are screen shots of various conky scripts as well as a collection of variables and how to code them.
 
As for colour, if you want specific colours, use the Hex codes (minus the '#') or you can use some text colours as well (i.e. white, red).
 
I found a program that allows you to choose a colour and have its CYMK and Hex codes display, but cannot remember it right now and I'm at work.

---

### Post by amazingtaters on 2007-08-14
For anyone who can help, I've a new problem. I got the .conkyrc working, but it's flickering like crazy. Double buffer is on in the .conkyrc, but I think I need to put something into the xorg.conf? Where would that go?

---

### Post by skwishybug on 2007-08-14
In your xorg.conf  (/etc/X11/xorg.conf) you would need to add: Load "dbe" at the bottom of the Modules list.

---

### Post by amazingtaters on 2007-08-14
Well, it's still flickering, but it's not nearly as bad as it was. Thanks!

---

### Post by merlyn on 2007-08-14
Check [this]("http://ubuntuforums.org/showthread.php?t=281865&highlight=.conky.rc") thread out, it has heaps of .conky.rc examples and screenshots.

Cheers.

---

### Post by ayu on 2007-08-14
You can also try 'own_window_type override' instead of 'normal' to reduce flickering

---

### Post by merlyn on 2007-08-14
> **ayu said:**
> You can also try 'own_window_type override' instead of 'normal' to reduce flickering

I believe that your on the money with this one.

For amazingtaters, here is my simple .conky.rc, so that you can see where to place the "own window" line.

Towards the end you will notice some examples on setting font colour and size.

```
double_buffer yes
update_interval 1.0
background yes

own_window yes
own_window_transparent yes
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

use_xft yes
override_utf8_locale no
xftfont Bitstream Vera Sans:size=9
xftalpha 0.8
draw_shades no
draw_outline no
draw_borders no
uppercase no
use_spacer no

border_margin 9
border_width 0

default_color white
default_outline_color black

alignment bottom_left
gap_x 9
gap_y 6

TEXT
${font :size=18:bold}${color #b8bec1}${time %A %B %e} ${time %H:%M}${font}
${stippled_hr}
${font :size=9}CPU ${cpu}% ${acpitemp}C${offset 50}Ram ${memperc}% ${mem}/${memmax}${offset 20}Swap ${swapperc}% ${swap}/${swapmax}${offset 55}Down ${downspeed eth0}Kb/s${offset 111}Up ${upspeed eth0}Kb/s${font}
${cpugraph 16,120 5e646a b8bec1} ${membar 16,180} ${swapbar 16,180} ${downspeedgraph eth0 16,180 5e646a b8bec1} ${upspeedgraph eth0 16,180 5e646a b8bec1}
```Cheers.

---

### Post by amazingtaters on 2007-08-15
Thanks guys I've got it sorted out now. You've all been a big help. Dunno what I'd do without the forums.

---

### Post by merlyn on 2007-08-15
No worries,

glad to have contributed something, it's the kind of thing I love about the Linux community.

I'd encourage you to check out that conky thread I mentioned earlier. Some of the folks posting are doing some really groovy stuff.

I've just taken a squiz and one bloke, Herbster, has 7 different conky scripts running.

Cheers.

---

