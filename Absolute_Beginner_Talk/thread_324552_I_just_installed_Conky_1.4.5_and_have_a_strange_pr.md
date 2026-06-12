---
title: "I just installed Conky 1.4.5 and have a strange problem..."
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-12-23
Hello, I was able to compile/install the 1.4.5 version of Conky to my xubuntu edgy that uses Beryl AiGLX on an Intel 910gml.

Now, when I'm running my computer and have a few windows open like Firefox, mousepad, and my /home/folder, I have a strange problem with apps not staying minimized or behind whatever window I have open and am working on. 

Basically if I have a few different apps running on my task bar, they will pop up when I haven't clicked them, and they just keep popping up.

It's really annoying when trying to type in terminal or in mousepad, or when scrolling through my files, and especially when reading a page on Firefox and then having my mousepad keep popping up in front of Firefox.

Can I fix this in my .conkyrc ??

It also will spin my cube back to the popped up window if I'm working on a different workspace.

---

### Post by crimesaucer on 2006-12-24
Bump... I haven't read about this in any forum so far.

Basically the window behind the current open window, is opening on it's own, over and over again.

---

### Post by crimesaucer on 2006-12-24
Ok...I think I fixed it myself.

But to help anyone with Beryl installed, that might run into the same problem that I was having with Conky doing the things I described above, I'm going to write how I solved my problem.

First off, the installation guide I followed was from the first link below, but the second link I'm going to post is probably better, and after toying around with the .conkyrc a bit, the second link seems to be a much better .conkyrc. Here are the links below so you can compare.

[http://doc.gwos.org/index.php/Conky_1.4.2](http://doc.gwos.org/index.php/Conky_1.4.2)

this was the one I had used for my .conkyrc since I had found it first. This one is the one that had a line of code on it that was not compatible with the Beryl Window Manager. (it's at the very bottom, below the line of code for those corny fortunes, also deleted now.)

the line of code was this "${execi 60 wmctrl -a conky}" you can look up wmctrl on google and read why it doesn't work. The command execi is described on the manual pages of Conky Variables as an "exercise" command like exec, but it works in intervals. (probably why it kept repeating the annoying actions.)

This is the second link, it seems much better.

[http://www.ubuntuforums.org/showthread.php?t=205865](http://www.ubuntuforums.org/showthread.php?t=205865)

good luck for anyone else trying this package.

*****New Edit*****

After messing around with the .conkyrc and a few pages about settings and variables, I finally learned it and rewrote the .conkyrc to fit my desktop perfectly. Here is a screenshot and the .conkyrc for anyone interested.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-15-1.png[/IMG]

[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-13-1.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-13-1.png)

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - battery stats, cached memory, uptime, date/time, file system stats
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
#own_window_type normal
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
# I think the "use spacer" option only works with mono fonts.
use_spacer yes
use_xft yes

# Xft font when Xft is enabled
xftfont Judas:size=9

# Update interval in seconds
update_interval 3.0

# Minimum size of text area

minimum_size 666 10

maximum_width 249


# Draw shades? was no
#draw_shades yes

# Text stuff
# amplifies text if yes was no
draw_outline yes 
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase


# border margins
#border_margin 0

# border width
#border_width 0

# Default colors and also border colors
#default_shade_color a7d9a3
default_outline_color 2c2c2c
default_color fffcf7 



# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 23
gap_y 66
	

# Text alpha when using Xft
xftalpha 1


# drawn 1 pixel border around graphs
draw_graph_borders no

# stuff after 'TEXT' will be formatted on screen


TEXT
xubuntu 6.10/Beryl AiGLX
blah@${nodename}
${kernel} on ${machine} 
IP eth0:    ${addr eth0}
wifi eth1:  ${linkstatus eth1}
${time} 
*  Uptime:  ${uptime}
*  Battery: ${battery}
*  B. time: ${battery_time}
Thunar File System:${alignr 24}${fs_size}
${alignr 24}used = ${fs_used}
${alignr 24}free = ${fs_free} 
Root File:${alignr 24}${fs_free_perc /}% used  
Win Xp:${alignr 24}${fs_free_perc /media/hda1}% used
Swap File:${alignr 24}${swapperc}% of ${swapmax}
RAM:${alignr 24}${memperc}% of ${memmax}
Cache Mem:${alignr 24}${cached}
  
  1.)  ${top_mem name 1}
mem %${offset 18}${top_mem mem 1}${offset 31}${alignc}cpu %${alignr 24}${top_mem cpu 1}

  2.)  ${top_mem name 2}
mem %${offset 18}${top_mem mem 2}${offset 31}${alignc}cpu %${alignr 24}${top_mem cpu 2}

  3.)  ${top_mem name 3}
mem %${offset 18}${top_mem mem 3}${offset 31}${alignc}cpu %${alignr 24}${top_mem cpu 3}

Up: ${upspeedf eth0}k/s${alignr 24}Down: ${downspeedf eth0}k/s
Up: ${totalup eth0}${alignr 24}Down: ${totaldown eth0}
${upspeedgraph eth0 34,100 6f706b 2b2c27}${offset 28}${downspeedgraph eth0 34,100 2b2c27 6f706b}

*  Temp:    ${acpitemp}.c
*  Load:    ${loadavg}
*  CPU:     ${freq}MHz
*  Clocked: ${freq_dyn}MHz
${cpugraph 34,228 6f706b 2b2c27}  
  1.)  ${top name 1}
cpu %${offset 18}${top cpu 1}${offset 31}${alignc}mem %${alignr 24}${top mem 1}
  
  2.)  ${top name 2}
cpu %${offset 18}${top cpu 2}${offset 31}${alignc}mem %${alignr 24}${top mem 2}

  3.)  ${top name 3}
cpu %${offset 18}${top cpu 3}${offset 31}${alignc}mem %${alignr 24}${top mem 3}

. . . . . crimesaucer--->


```

---

### Post by edmondt on 2007-02-04
Thanks for the .conkyrc file, it made it so much easier for me :)

---

