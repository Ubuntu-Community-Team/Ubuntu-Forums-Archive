---
title: "Conky quits when terminal closes"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by flintflake on 2007-05-07
I have conky installed and seems to work great but whenever i close the terminal window, it stops conky.   Also, i see it when I initially log in but when my wallpaper shows up, it disappears.

Any ideas?

---

### Post by meborc on 2007-05-07
if you run conky from terminal, then it closes when the terminal is closed... you need to run it with alt+f2...

---

### Post by tkjacobsen on 2007-05-07
You probably want conky to run at startup. Add it in system->preferences->session -> something (I'm not currently running Gnome, so I don't remember)

If you would like to keep a program running after closing the terminal from which the program  is started you can use nohup. 

```
nohup conky
```

It is short for nohangup and if you run programs like that the terminal will not send a "terminal closed" signal if the terminal is closed.

---

### Post by Seisen on 2007-05-07
You need to change the colors in the .conkyrc file I had the same problem.

---

### Post by flintflake on 2007-05-07
> **Seisen said:**
> You need to change the colors in the .conkyrc file I had the same problem.

Can you add your .conkyrc file so i can see what colors you used?

---

### Post by Seisen on 2007-05-07
```
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
default_color black

own_window_colour white
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
${color red}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color red}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color red}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color


${color red}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color red}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color red}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

and I attached a screenshot of my desktop so you can see what it looks like so you can figure out which colors you need.

---

### Post by Green_Star on 2007-05-19
I tried with "conky &" and "nohup conky" in my startup list, but still when ever i login, conky loading showing up for 1-2 seconds, then it is disappearing. my system monitor showing that conky is still running. but i am not able to see anything on my screen. it is working fine if i start from terminal. 

Any clue?

---

### Post by nukecoder on 2007-05-23
> **Green_Star said:**
> I tried with "conky &" and "nohup conky" in my startup list, but still when ever i login, conky loading showing up for 1-2 seconds, then it is disappearing. my system monitor showing that conky is still running. but i am not able to see anything on my screen. it is working fine if i start from terminal. 

Any clue?

I had the exact same problem.
This thread has a fix that worked great: 
[http://ubuntuforums.org/showthread.php?t=437583&highlight=conky+on+startup](http://ubuntuforums.org/showthread.php?t=437583&highlight=conky+on+startup)

Hope that helps :)

---

### Post by jordanmthomas on 2007-05-23
To OP:  or, you could just run it with the option to run as a daemon:
```
conky -d
```
Or, put this in your .conkyrc
```
# directly fork into background after start            
background yes  
```
and voila, it'll still be around after your terminal goes away.

To Green_Star:  don't use conky &  :  try conky -d or the aforementioned line in your .conkyrc and then just run it as conky.  I'm not sure, but I think conky needs to run **after** nautilus or it will be drawn over by nautilus.

---

### Post by lazyart on 2007-05-23
[hijack]what app bar is that on the bottom?[/hijack]

---

### Post by IainT on 2007-05-23
lazyart - The screenshot looks like fluxbox to me. Conky agrees.

Some nice touches in that conky.rc, might have to borrow them.

---

### Post by RedSquirrel on 2007-05-24
> **lazyart said:**
> [hijack]what app bar is that on the bottom?[/hijack]

That's the standard Fluxbox toolbar. It can be customized (content and transparency level).

---

### Post by SumyTheSlayer on 2008-06-16
> **lazyart said:**
> what app bar is that on the bottom?

he is using fluxbox as a WM

---

