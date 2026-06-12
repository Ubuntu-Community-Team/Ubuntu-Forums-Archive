---
title: "2 Minor Conky Issues"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Aysah on 2008-04-05
I installed conky and now im starting to try to customize it based on a couple configs i found oinline.  so far everything is going well but i have two questions.

[LIST=1]
[*]How do i make conky stay on top of everything like my normal panel does? (i have it setup as a horizontal bar at the bottom of my screen)
[*]Why is my conky have extra black space beneath the text?  I want it only as thick as the text and can't figure out where those settings are.
[/LIST]

Here is a copy of my config:
# mod by uel

#avoid flicker
double_buffer yes
no_buffers yes

#own window to run simultanious 2 or more conkys
own_window yes
own_window_transparent no
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager

#borders
#draw_borders no
border_margin 1

#shades
draw_shades no

#draw_graph_borders yes

#draw_borders yes

#position
gap_x 1
gap_y 1
alignment bottom_left

#Update interval in seconds
update_interval 1

#colour
#default_color 000000
default_color D6D6D6
#default_color bfbfbf
#default_shade_color 000000
own_window_colour 000000
#draw_borders_colour 000000
#draw_graph_borders_colour 000000
#484432 95956B

#font
use_xft yes
xftfont HandelGotD:pixelsize=10

#to prevent window from moving
use_spacer no
minimum_size 1440 5

# ${offset -22}
TEXT
${voffset -1} Cpu: ${color E8BCA7}${font}${cpu}% ${color 292929}<${color} P: ${color BB4E3F}${font}${processes}${color} R: ${color 7FBB3F}${font}${running_processes}${color 292929} |${color} Mem: ${color E8BCA7}${font}${mem}${color} Swap: ${color E8BCA7}${font} ${swap} ${color 292929} | ${color} Uptime: ${color 8D41CC}${font}${uptime_short}${color 292929} | ${color E8BCA7}${font}${downspeed eth0} Kb/s ${color} ${totaldown eth0} down${color 292929}  | ${color} ${color E8BCA7}${upspeed eth0} Kb/s ${color} ${totalup eth0} up${color 292929}  |  ${color}Main: ${color E8BCA7}${font}${fs_free /} ${color} Home: ${color E8BCA7}${font}${fs_free /home} ${color 292929}|  ${color}Temperature: ${color D3BE4C}${font}${acpitemp}${color}C ${color 292929}

---

### Post by SOULRiDER on 2008-04-05
> **Aysah said:**
> I installed conky and now im starting to try to customize it based on a couple configs i found oinline.  so far everything is going well but i have two questions.

[LIST=1]
[*]How do i make conky stay on top of everything like my normal panel does? (i have it setup as a horizontal bar at the bottom of my screen)
[/LIST]


I dont think you want that, conky isnt really transparent, it just has a background like your desktop so it feels transparent.

MY suggestion is: Look for examples of conky scripts that you like and try changing your settings to reflect their settings. Also, try removing the 
> no_buffers yes line, and change the > own_window_transparent no
own_window_type normal lines to tes and desktop.

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

