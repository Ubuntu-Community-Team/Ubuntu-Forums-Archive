---
title: "CPU usage graph background"
date: 2008-05-25
forum: Art &amp; Design
---

### Post by James_the_dude on 2008-05-25
I was looking at my desktop today when had this amazing idea: what if I could have an animated graph of my cpu usage as my desktop background? It would look amazing. Now this has to be possible, the questions would be: is it feasible? Would it slow things down dramatically? I'm using ubuntu 8.04, has anybody ever heard of or seen this done before?

---

### Post by LeoSolaris on 2008-05-25
Look up conky. It's a program that is very lightweight and can be made to look like it is just sitting on your desktop without a window of it's own.

Here's a screenshot of mine, attached.  It is conceivable to make a graph of the CPU that fits across the screen. There is a nice thread that has screenshots and copies of the config file on the forum. I don't have time to hunt it at the moment, just search for conky.

Leo

---

### Post by Bubba64 on 2008-05-25
There are 2 types of ways to show usage in add to panel. Personally I use system monitor and change the background color on the processor window that can be put on any panel with a window for up to the millisecond information you can add little windows on 6 different areas of usage and change the millisecond amount showing size and background colors. If you click on the widows it will bring up the system info that top will give you from a terminal with the ability to kill a process and other access. Also if you put your cursor over the window it will tell you exactly the usage.

---

### Post by James_the_dude on 2008-05-25
Hmm, this "conky" looks like a potential solution to look into. If I actually get this thing working I'll post pretty screen-shots and instructions. Thanks

- J

---

### Post by James_the_dude on 2008-05-25
I have partial success.

here is a screenshot:

[[IMG]http://img186.imageshack.us/img186/6014/conkydccpuxm1.th.png[/IMG]](http://img186.imageshack.us/my.php?image=conkydccpuxm1.png)

Now I am struggling to understand the conky configuration syntax. Specifically I can't get alignment the way I'd like it. I'm trying to get what you see in the screenshot centered on my screen both horizontally and vertically. Here is my settings file:

```
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
own_window no
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 0.5

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color black
default_shade_color black
default_outline_color black

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

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

Core 1
${cpugraph cpu1 200,1200 000000 000000}
Core 2
${cpugraph cpu2 200,1200 000000 000000}
```

---

### Post by Abu_Dayya on 2008-05-26
> **LeoSolaris said:**
> Look up conky. It's a program that is very lightweight and can be made to look like it is just sitting on your desktop without a window of it's own.

Here's a screenshot of mine, attached.  It is conceivable to make a graph of the CPU that fits across the screen. There is a nice thread that has screenshots and copies of the config file on the forum. I don't have time to hunt it at the moment, just search for conky.

Leo

Your conky looks realy nice. Can you post your .conkyrc file?

---

### Post by LeoSolaris on 2008-05-28
My RC Is an edit of one found on the conky showing off thread. I tried to change the font, but it was being grouchy.

```

# do not fork to background
background no

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 10 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color 75B6D1
default_shade_color black
default_outline_color white

#own_window_colour no

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 30

# stuff after 'TEXT' will be formatted on screen


override_utf8_locale yes
xftfont sans:size=8
xftalpha 0.8
TEXT






${offset 0}${color #FFF500}${font sans:size=10}${exec whoami}@${exec hostname}$font
 ${offset 0}${color #ffffff}Date/Time ${stippled_hr }
 ${offset 0}${color #ffffff} ${time %a, }${color #ffffff}${time %e %B %G  }${color #ffffff} ${color #ffffff}${time %H:%M:%S}${time %Z}

${offset 0}${color #ffffff}System Info ${stippled_hr }

 ${offset 0}${color #ffffff} UpTime: ${color }${alignr}$uptime
 ${offset 0}${color #ffffff} Kern:${color }${alignr}$kernel
 ${offset 0}${color #ffffff} Battery: ${color }${alignr}${battery BAT0}

${offset 0}${color #ffffff}CPU INFO ${stippled_hr }

  ${offset 0}${color #ffffff} CPU Clock: ${color }${alignr}${freq_g}GHz
  ${offset 0}${color #ffffff} Load: ${color }${alignr}$cpu %
  ${offset 0}${color #ffffff} Load Avg: ${color }${alignr}$loadavg
  ${offset 0}${color #ffffff} Processes: ${color }${alignr}$processes
  ${offset 0}${color #ffffff} Running:   ${color }${alignr}$running_processes

${alignc}${color #ffffff}Highest CPU
${alignc}${color } ${top name 1}${top cpu 1}%
${alignc}${color } ${top name 2}${top cpu 2}%

${alignc}${color #ffffff}Highest MEM
${alignc}${color } ${top_mem name 1}${top_mem mem 1}%
${alignc}${color } ${top_mem name 2}${top_mem mem 2}%

${offset 0}${color #ffffff}Memory and Storage${stippled_hr }

${offset 0}${color #ffffff}MEM:
 ${offset 0}${color }$mem/$memmax${alignr}${membar 3,150} ${memperc}%

${offset 0}${color #ffffff}SWAP:
 ${offset 0}${color }$swap/$swapmax${alignr}${swapbar 3,150} ${swapperc}%

${offset 0}${color #ffffff}ROOT:
 ${offset 0}${color }${fs_used /}/${fs_size /}${alignr}${fs_bar 3,150 /} ${fs_used_perc /}%

${offset 0}${color #ffffff}HOME:
 ${offset 0}${color }${fs_used /home}/${fs_size /home}${alignr}${fs_bar 3,150 /home} ${fs_used_perc /home}%

${offset 0}${color #ffffff}Windows:
 ${offset 0}${color }${fs_used /media/Windows}/${fs_size /media/Windows}${alignr}${fs_bar 3,150 /media/Windows} ${fs_used_perc /media/Windows}%

${color #ffffff}NETWORK (${addr wlan0} ${wireless_essid wlan0})
 ${offset 0}${color #ffffff}Down: $color${downspeed wlan0} kb/s${alignr}${color #ffffff}UP: $color${upspeed wlan0} kb/s
 ${offset 0}${color #ffffff}Total Down: $color${totaldown wlan0}${alignr}${color #ffffff}Total Up: $color${totalup wlan0}

```Check out conky's website, they have help for programing it, syntax and all that good stuff. You can even get it to display weather readings, amount of mail in your email, and output from your music player. Mine just scratches the surface.

Leo

---

### Post by Abu_Dayya on 2008-05-29
thanks

---

