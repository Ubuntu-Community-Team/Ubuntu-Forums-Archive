---
title: "config files"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by windows hater on 2008-03-25
 i want to try and get conky up and and running but one of the steps tells me to 

Make a configuration file in your home directory (Ex:-/home/ubuntuadmin)

vi /home/ubuntuadmin/.conkyrc

Paste the following code into the file and save / exit

is this talking about the source list if not can i have some help on how to get to this 

many thanks in advance

---

### Post by Oldsoldier2003 on 2008-03-25
screenshots and sample .conkyrc files can be seen [here]("http://ubuntuforums.org/showthread.php?t=281865")

---

### Post by windows hater on 2008-03-25
i just want to know how to get to this home directory where .conkyrc is

---

### Post by Oldsoldier2003 on 2008-03-25
> **windows hater said:**
> i just want to know how to get to this home directory where .conkyrc is

```
cd ~
```

or click home in the places menu

---

### Post by nedtoledo on 2008-03-25
please click on > Places > Home Folder

---

### Post by Oldsoldier2003 on 2008-03-25
> **nedtoledo said:**
> please click on > Places > Home Folder

Just a reminder, if you use the menu it will open your Home folder in nautilus, which does not show hidden files by default. Press ctrl+H to show the hidden files. ( filenames that start with a "." are hidden files)

---

### Post by windows hater on 2008-03-25
ok i did that and i enabled hidden files and i still cant see .conkyrc

---

### Post by markjensen on 2008-03-25
When you open a terminal and do a **ls al | grep conky** do you see the file?

Try doing **touch ~/.conkyrc** then re-run the above command.   Unless things are totally wacky, you should certainly see the (empty) file now!

---

### Post by nedtoledo on 2008-03-25
^ that means you need to create one
open up the terminal and type:
```
gedit .conkyrc
```

paste your conky config in there and save the file

then back on terminal just type 

```
conky
```

hope this helps

---

### Post by crane on 2008-03-25
> **windows hater said:**
> i want to try and get conky up and and running but one of the steps tells me to 

Make a configuration file in your home directory (Ex:-/home/ubuntuadmin)

vi /home/ubuntuadmin/.conkyrc

Paste the following code into the file and save / exit

is this talking about the source list if not can i have some help on how to get to this 

many thanks in advance

When you did the above steps. Did you by chance open vi with root privileges? If you did then it may have saved the file to root home directory.

---

### Post by Iowan on 2008-03-25
You can try **locate .conkyrc**.

---

### Post by windows hater on 2008-03-25
thnx for all your help but when i load conky its works great the only thing is its not intergrated to the desktop its open as a window and i saved it in sessions as well if thats any help

---

### Post by Lord Illidan on 2008-03-25
That might be a problem with your conkyrc.

Try this script :
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
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 200 5
maximum_size 200 5



# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
# Draw borders around graphs
draw_graph_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
#stippled_borders 8

# border margins
border_margin 4

# border width
border_width 2

# Default colors and also border colors, 90 == #e5e5e5
default_color white
#default_shade_color white
default_outline_color white

own_window_colour blue
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 20

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale yes
xftfont Candera:size=8
xftalpha 0.9

TEXT

${font :size=14}${color 00ffff}${alignc}${time %A, }${color 00ffff}${time %e %B %G}

${color 00ffff}${alignc}${time %H:%M:%S}
${font :size=8}${color }UpTime: ${color }$uptime
${color }Linux:  ${color }$kernel

${offset 30}${color }CPU 1   ${color }${cpu cpu1}%${offset 80}${color }CPU 2   ${color }${cpu cpu2}%
${color }${cpugraph cpu1 20,150 0000ff ff0000}${color }${cpugraph cpu2 20,150 0000ff ff0000}

${color }Processes: ${color }$processes       Running:   ${color }$running_processes

Top Processes${alignr}         ID       CPU         MEM
${color ffff00}${top name 2} ${alignr}${top pid 2}   ${top cpu 2}    ${top mem 2}
${color lightgrey}${top name 3} ${alignr}${top pid 3}   ${top cpu 3}    ${top mem 3}
${color lightgrey}${top name 4} ${alignr}${top pid 4}   ${top cpu 4}    ${top mem 4}


${color }MEM: ${font :size=8}$alignr${color }$memperc% $mem/$memmax
${color lightgrey}${membar 5,300}
${font :size=8}${color }SWAP: ${font :size=8}$alignr${color }$swapperc% $swap/$swapmax
${color lightgrey}${swapbar 5,300}
${font :size=8}${color }LINUX: ${font :size=8}$alignr${color }${fs_free_perc /}%  ${fs_free /}/${fs_size /}
${color lightgrey}${fs_bar 5,300 /}


${font :size=8}${color }NET: IP ${color }${alignc}${addr wlan0}${color }

${offset 30}${color}Up:  ${color }${upspeed wlan0}k/s${offset 80}${color}Down:  ${color }${downspeed wlan0}k/s${color}
${color }${upspeedgraph wlan0 20,150 0000ff ff0000}${color }${downspeedgraph wlan0 20,150 0000ff ff0000}


${if_running amarokapp}
$alignc${font :size=8}${color darkgoldenrod}Amarok:

${voffset -3}${color darkgoldenrod}Artist:$alignc${if_empty execi 10 dcop amarok player artist}$alignc${color wheat1}Music Stopped $else${color wheat1}${execi 10 dcop amarok player artist}$endif

${voffset -3}${color darkgoldenrod}Title:$alignc${color wheat1}${execi 10 dcop amarok player title}

${voffset -3}${color darkgoldenrod}Time:$alignc${color wheat1}${execi 1 dcop amarok player currentTime} / ${execi 10 dcop amarok player totalTime} 
 
${voffset -3}${color darkgoldenrod}Album:$alignc${color wheat1}${execi 10 dcop amarok player album}$endif${font }



```

Some things will not work on your setup, but at least you should see if it integrates into the desktop.

---

### Post by windows hater on 2008-03-25
thnx but when i tryed that nothing showed up and when i type Conky in terminal i get this

Conky: /home/guitar/.conkyrc: 31: no such configuration: 'maximum_size'
Conky: desktop window (c000b0) is subwindow of root window (4d)
Conky: window type - override
Conky: drawing to created window (3000001)
Conky: drawing to double buffer
Conky: attempting to use more CPUs then you have!

---

### Post by Lord Illidan on 2008-03-25
> **windows hater said:**
> thnx but when i tryed that nothing showed up and when i type Conky in terminal i get this

Conky: /home/guitar/.conkyrc: 31: no such configuration: 'maximum_size'
Conky: desktop window (c000b0) is subwindow of root window (4d)
Conky: window type - override
Conky: drawing to created window (3000001)
Conky: drawing to double buffer
Conky: attempting to use more CPUs then you have!

Ah yes. It is supposed to show the graph of a dual core CPU.

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
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 200 5



# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
# Draw borders around graphs
draw_graph_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
#stippled_borders 8

# border margins
border_margin 4

# border width
border_width 2

# Default colors and also border colors, 90 == #e5e5e5
default_color white
#default_shade_color white
default_outline_color white

own_window_colour blue
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 20

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale yes
xftfont Candera:size=8
xftalpha 0.9

TEXT

${font :size=14}${color 00ffff}${alignc}${time %A, }${color 00ffff}${time %e %B %G}

${color 00ffff}${alignc}${time %H:%M:%S}
${font :size=8}${color }UpTime: ${color }$uptime
${color }Linux:  ${color }$kernel



```

Try this instead.

---

### Post by markjensen on 2008-03-25
GO back to your file, the one that you said appeared in a window, instead of on the desktop.

Then edit your .conkyrc program with your most favorite of text editors, and look for the line that says **own_window yes** and change it to **own_window no**, then it won't make a separate pesky window for conky.

---

### Post by windows hater on 2008-03-25
im sry im asking alot about this its seems its like one step forward and two steps back

 ok i add conky to my sessions and i log out and log back in its not there but when i go through terminal and type conky it shows up but every time it refreshes my icons on my desktop disapear

---

