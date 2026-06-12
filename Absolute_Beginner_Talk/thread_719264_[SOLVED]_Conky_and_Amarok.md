---
title: "[SOLVED] Conky and Amarok"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by hoges on 2008-03-09
I just installed conky, and am now trying to get it to play nice with amarok.

I got the script of the amarok page, saved it to ~/.conky/amarok, and then added the relevant bits into the conkyrc file. Amarok is configured for mysql.

Does anybody know why it won't display any info when amarok plays? It gets as far as showing the now playing title, but doesn't actually show any info.

The conkyrc file is listed below (amarok bit at the end).

Cheers
Hoges

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
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 1.0

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
default_color grey

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

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
${color #0077ff}Uptime:${color lightgrey} $uptime

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}VGA ${hr 2}$color
${color ffffff}GPU Temp:$alignr ${color white} +${exec nvidia-settings -q GPUCoreTemp | grep Attribute | cut -d ' ' -f 6 | cut -c 1-2}°C
${color ffffff}Video RAM:$alignr ${color white} ${exec nvidia-settings -q VideoRam | grep Attribute | cut -d ' ' -f 6 | cut -c 1-6}KiB
${color ffffff}NVidia Driver Version:$alignr ${color white} ${exec nvidia-settings -q NvidiaDriverVersion | grep Attribute | cut -d ' ' -f 6}
${color ffffff}Current GPU Clock:$alignr ${color white} ${exec nvidia-settings -q GPUPerfModes | grep perf=0 | cut -d ' ' -f 7 | cut -c 9-11}MHz
${color ffffff}Current Video RAM Clock:$alignr ${color white} ${exec nvidia-settings -q GPUPerfModes | grep perf=0 | cut -d ' ' -f 8 | cut -c 10-12}MHz

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
sda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
sdb3:  ${fs_free_perc /media/sdb3}%   ${fs_bar 6 /media/sdb3}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}"${execi 10 ~/.conky/amarok album}"
${alignc}${execi 10 ~/.conky/amarok year} - ${color white}${alignc}${execi 10 ~/.conky/amarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 10 ~/.conky/amarok totalArtists} $color${alignr}Compilations: ${color white}${execi 10 ~/.conky/amarok totalCompilations}$color
Albums:  ${color white}${execi 10 ~/.conky/amarok totalAlbums} $color${alignr}Genres: ${color white}${execi 10 ~/.conky/amarok totalGenres}$color
Tracks:  ${color white}${execi 10 ~/.conky/amarok totalTracks}
$color$stippled_hr
${alignc}Collection Statisctics
Most songs by ${color white}${execi 10 ~/.conky/amarok most_songs_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_by_artist_n}${color})
Most songs are ${color white}${execi 10 ~/.conky/amarok most_songs_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_are_genre_n}${color})
Most songs during ${color white}${execi 10 ~/.conky/amarok most_songs_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_during_year_n}${color})
Most albums by ${color white}${execi 10 ~/.conky/amarok most_albums_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_by_artist_n}${color})
Most albums are ${color white}${execi 10 ~/.conky/amarok most_albums_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_are_genre_n}${color})
Most albums during ${color white}${execi 10 ~/.conky/amarok most_albums_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_during_year_n}${color})$endif


```

---

### Post by p_quarles on 2008-03-09
Did you make the Amarok script executable? If not, you would do so by running the following:
```
chmod u+x .conky/amarok
```
Then, restart conky, and it should work.

---

### Post by hoges on 2008-03-09
Yes that did it. Thanks...

BUT
It only shows 1 1/2 line - cuts off the text. Anyway to fix this?

I'll try and get a screenshot...


Alright, I got the screenshot. Anybody have any idea what's causing this?

---

### Post by p_quarles on 2008-03-09
> **hoges said:**
> Yes that did it. Thanks...

BUT
It only shows 1 1/2 line - cuts off the text. Anyway to fix this?

I'll try and get a screenshot...


Alright, I got the screenshot. Anybody have any idea what's causing this?
Uncomment the "minimum_size" line. The value is in pixels, and can be used for fine-grain control over the size of the display. Having it commented makes the size whatever the default is, and this is probably simply too narrow to display all the text you want from the Amarok script.

---

### Post by hoges on 2008-03-09
You're a genius. Thanks!

---

