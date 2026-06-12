---
title: "conky sensors"
date: 2012-05-12
forum: Apple Hardware Users
---

### Post by cabal1209 on 2012-05-12
Im fairly new to this sorry if i leave out info in the beginning. I have a macbook pro 5,5 with Ubuntu 12.04, and i started playing around conky, and i wanted to add the cpu temps to it, did some searching around but i havent found anything that helps.

here is the output of sensors


applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   1998 RPM  (min = 2000 RPM)
TB0T:         +36.8°C  
TB1T:         +36.5°C  
TB2T:         +36.0°C  
TB3T:         +40.2°C  
TC0D:         +64.8°C  
TC0P:         +58.5°C  
TN0D:         +64.0°C  
TN0P:         +55.5°C  
TTF0:          +0.0°C  
Th0H:          +0.0°C  
Th1H:         +58.5°C  
ThFH:         +58.5°C  
Ts0P:         +36.0°C  
Ts0S:         +46.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +64.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +63.0°C  (high = +105.0°C, crit = +105.0°C)

jc42-i2c-0-18
Adapter: SMBus nForce2 adapter at 2140
temp1:        +58.8°C  (low  =  +0.0°C)                  ALARM (HIGH, CRIT)
                       (high =  +0.0°C, hyst =  +0.0°C)
                       (crit =  +0.0°C, hyst =  +0.0°C)

jc42-i2c-0-19
Adapter: SMBus nForce2 adapter at 2140
temp1:        +58.0°C  (low  =  +0.0°C)                  ALARM (HIGH, CRIT)
                       (high =  +0.0°C, hyst =  +0.0°C)
                       (crit =  +0.0°C, hyst =  +0.0°C)


how do i tell conky to get the cpu temp for the two core if possible if not just cpu as a whole. and if possible the fan as well but that is second to the cpu

if you need more info please let me know

---

### Post by wilee-nilee on 2012-05-12
If your help here is not quick enough, there are tons of scripts on line download some and give them a look, tweak away to your content. :)

There  is a conky thread on the forum that has pictures and their scripts posted as well.

---

### Post by Enigmapond on 2012-05-12
Yea the best way to learn conky is by doing. Get one you kinda like and fool with it. See how everything is set up and what makes it work. We could set here and tell you all day how but until you actually do it, it won't make too much sense.

---

### Post by cabal1209 on 2012-05-12
i did just that but i am stuck on getting the core temps to display everything else is fine

---

### Post by wilee-nilee on 2012-05-12
> **cabal1209 said:**
> i did just that but i am stuck on getting the core temps to display everything else is fine

Post the conky.

---

### Post by cabal1209 on 2012-05-12
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 2

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints below

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 8
maximum_width 500

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline yes # amplifies text if yes

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0


# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color white
#default_outline_color white
own_window_colour black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 5

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
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT



${alignr}${offset -109}
${font Arial Black:size=18}${time %H}${color}${font Dodger Condensed:size=18}${time :%M}${font}${alignr}${time %A %B %d %Y}

${voffset 2}${font OpenLogos:size=8}${font}   Kernel:  ${alignr}${kernel} ${machine}
${font StyleBats:size=8}${font}   
${color0}Cpu 1:${color grey60} ${cpu cpu1}%
${color grey60}${cpugraph cpu1 7,250 0b0d0d 0b0d0d} 
${color0}Cpu 2:${color grey60}  ${cpu cpu2}%
${color grey60}${cpugraph cpu2 7,250 303030 0b0d0d} 
${color0}Ram used:${color grey60} $memperc% $mem / $memmax ${membar 5,100}
${color0}Space:${color grey60} ${fs_free_perc /}% ${fs_used} / ${fs_size} ${alignr}${fs_bar 5,100}
${color0}Swap used:${color grey60} $swap / $swapmax ${alignr}${swapbar 5,100}
${color0}
${font StyleBats:size=8}${font}   Uptime: ${alignr}${uptime}

${if_existing /proc/net/route eth2}
WIRELESS ${hr 0.5}
${voffset 4}${font PizzaDude Bullets:size=8}${font}   Up: ${upspeed eth2}  ${alignr}${upspeedgraph eth2 15,150 303030 00ff00}
${voffset 4}${font PizzaDude Bullets:size=8}${font}   Down: ${downspeed eth2}  ${alignr}${downspeedgraph eth2 15,150 303030 ff0000}
${voffset 4}${font PizzaDude Bullets:size=8}${font}   Upload / Download: ${alignr}${totalup eth2} / ${alignr}${totaldown eth2}
${voffset 4}${font PizzaDude Bullets:size=8}${font}   Local Ip: ${alignr}${addr eth2}
External Ip ${execi 3600 curl http://riivo.eu/php/ip.php}
${endif}
${if_existing /proc/net/route eth0}
WIRED ${hr 2}
${voffset 4}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 10,175 0092FF 00A91D}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 10,175 0092FF 00A91D}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload / Download: ${alignr}${totalup eth0} / ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
External Ip ${execi 3600 curl http://riivo.eu/php/ip.php}
${endif}


it doesnt have my attempts at adding the core temps 1 one because it doesnt work 2 i have found more then one command and i dont want clutter
this is the latest command i tried  
${execi 8 sensors | grep -A 1 'coretemp-isa-0000 core 0' | cut -c13-16 | sed '/^$/d'}

---

### Post by Mopar1973Man on 2012-05-12
Like other have said it best ot dive in and play with it...

Here is the code I used to get my sensor displayed...

```
${voffset 5}${font StyleBats:size=9.9}${color2}${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}CPU Temperature${goto 95}${font DroidSans:size=8.3}${alignr}${exec sensors -f | grep 'CPU Temperature:' | cut -c21-23}°F / ${color #FCAF3E}203°F${font}
```

The **{exec sensors -f | grep 'CPU Temperature:' | cut -c21-23} **has to be tweaked to read the lines of sensors the** cut **command is the character to read on the display and the **'CPU Temp' **is the text to look for so cut can read the character position 21 to 23.

Hopefully that helps...

---

### Post by cabal1209 on 2012-05-12
thanks you but that still doesn't print anything out i even change that grep to just 'core 0:' and still nothing

---

### Post by Mopar1973Man on 2012-05-12
Hmmm... Did you change the value of cut? Your should be 9-10 if I counted it right.

---

### Post by cabal1209 on 2012-05-12
i tried that just now but im now getting
sh: 1: Syntax error: end of file unexpected

---

### Post by cabal1209 on 2012-05-12
my bad got it to work thanks guys

---

### Post by Mopar1973Man on 2012-05-12
Right on I'm glad you got it working... ;)

---

