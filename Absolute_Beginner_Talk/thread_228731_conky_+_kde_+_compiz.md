---
title: "conky + kde + compiz"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by joelones on 2006-08-03
hey guys,
just wondering if others are the same problem. 
loaded the 'dbe' extension and when conky start ups the icons on the desktop disappear, clicking the desktop makes them reappear until conky's next refresh cycle then they disappear againg. running kde 3.5.3, latest compiz from quinn's repo.

thanks

---

### Post by Adrian_b on 2006-08-03
Wtf, i just wanted to make this topic aswell :D
I have Gnome + Conky + Compiz with the .conkyrc from the 1.4.2 howto here.. ( [http://www.ubuntuforums.org/showthread.php?t=205865&highlight=conky](http://www.ubuntuforums.org/showthread.php?t=205865&highlight=conky) )

I found the solution:
```

own_window 1
own_window_type override
own_window_transparent 1

```

( [http://www.ubuntuforums.org/showpost.php?p=1246604&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1246604&postcount=6) found it )

---

### Post by joelones on 2006-08-12
see next post

---

### Post by joelones on 2006-08-12
thanks for the heads up, Adrian_b

the desktop icons don't disappear but i can not get transparency working for conky. the conky background is black. did you have this problem?

this is my conkyrc

```

# Create own window instead of using desktop (required in nautilus)
# own_window no
own_window 1
own_window_type override
own_window_transparent 1
# set to yes if you want Conky to be forked in the background
background yes

# Set conky on the bottom of all other applications
#on_bottom yes
#own_window_hints undecorated,below,skip_taskbar
#own_window_hints below

xftalpha 1
total_run_times 0
cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
# xftfont monospace-8
xftfont Constantia:size=8

#own_window_colour hotpink
#own_window_colour black

# Text alpha when using Xft
xftalpha 0.8

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 5 5
#maximum_width 150

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 10

# border width
border_width 2

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

gap_x 20
gap_y 20

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#      Variable         Arguments                  Description
#  acpiacadapter                     ACPI ac adapter state.
#  acpifan                           ACPI fan state
#  acpitemp                          ACPI temperature.
#  adt746xcpu                        CPU temperature from therm_adt746x
#  adt746xfan                        Fan speed from therm_adt746x
#  battery           (num)           Remaining capasity in ACPI or APM
#                                    battery. ACPI battery number can be
#                                    given as argument (default is BAT0).
#  buffers                           Amount of memory buffered
#  cached                            Amount of memory cached
#  color             (color)         Change drawing color to color
#  cpu                               CPU usage in percents
#  cpubar            (height)        Bar that shows CPU usage, height is
#                                    bar's height in pixels
#  downspeed         net             Download speed in kilobytes
#  downspeedf        net             Download speed in kilobytes with one
#                                    decimal
#  exec              shell command   Executes a shell command and displays
#                                    the output in torsmo. warning: this
#                                    takes a lot more resources than other
#                                    variables. I'd recommend coding wanted
#                                    behaviour in C and posting a patch :-).
#  execi             interval, shell Same as exec but with specific interval.
#                    command         Interval can't be less than
#                                    update_interval in configuration.
#  fs_bar            (height), (fs)  Bar that shows how much space is used on
#                                    a file system. height is the height in
#                                    pixels. fs is any file on that file
#                                    system.
#  fs_free           (fs)            Free space on a file system available
#                                    for users.
#  fs_free_perc      (fs)            Free percentage of space on a file
#                                    system available for users.
#  fs_size           (fs)            File system size
#  fs_used           (fs)            File system used space
#  hr                (height)        Horizontal line, height is the height in
#                                    pixels
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev
#                                    may be omitted if you have only one I2C
#                                    device. type is either in (or vol)
#                                    meaning voltage, fan meaning fan or temp
#                                    meaning temperature. n is number of the
#                                    sensor. See /sys/bus/i2c/devices/ on
#                                    your local computer.
#  kernel                            Kernel version
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1
#                                    minute, 2 for past 5 minutes and 3 for
#                                    past 15 minutes.
#  machine                           Machine, i686 for example
#  mails                             Mail count in mail spool. You can use
#                                    program like fetchmail to get mails from
#                                    some server using your favourite
#                                    protocol. See also new_mails.
#  mem                               Amount of memory in use
#  membar            (height)        Bar that shows amount of memory in use
#  memmax                            Total amount of memory
#  memperc                           Percentage of memory in use
#  new_mails                         Unread mail count in mail spool.
#  nodename                          Hostname
#  outlinecolor      (color)         Change outline color
#  pre_exec          shell command   Executes a shell command one time before
#                                    torsmo displays anything and puts output
#                                    as text.
#  processes                         Total processes (sleeping and running)
#  running_processes                 Running processes (not sleeping),
#                                    requires Linux 2.6
#  shadecolor        (color)         Change shading color
#  stippled_hr       (space),        Stippled (dashed) horizontal line
#                    (height)
#  swapbar           (height)        Bar that shows amount of swap in use
#  swap                              Amount of swap in use
#  swapmax                           Total amount of swap
#  swapperc                          Percentage of swap in use
#  sysname                           System name, Linux for example
#  time              (format)        Local time, see man strftime to get more
#                                    information about format
#  totaldown         net             Total download, overflows at 4 GB on
#                                    Linux with 32-bit arch and there doesn't
#                                    seem to be a way to know how many times
#                                    it has already done that before torsmo
#                                    has started.
#  totalup           net             Total upload, this one too, may overflow
#  updates                           Number of updates (for debugging)
#  upspeed           net             Upload speed in kilobytes
#  upspeedf          net             Upload speed in kilobytes with one
#                                    decimal
#  uptime                            Uptime
#  uptime_short                      Uptime in a shorter format
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
#${font Luxi Mono:size=10}justo como este texto que o google traduz fÃªz o portuguÃªs
# stuff after 'TEXT' will be formatted on screen
TEXT
${color white}[${color #00ff00}Server${color white}][${color red}$nodename${color white}]
${color #888888}$sysname $kernel ${color #888888}on ${color #888888}$machine
${color #888888}Uptime: $uptime
${color #888888}${time %b/%a/%d}                     ${color #00ff00}${time %k:%M:%S}
${color #888888}$stippled_hr
${color #ffccaa}Monitors-
${color #888888}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color #888888}${cpugraph cpu1 25 ff0000 ff00ff}
${color #888888}CPU2 Usage:${color} ${cpu cpu2}% ${cpubar cpu2}
${color #888888}${cpugraph cpu2 25 ff0000 ff00ff}
$stippled_hr
${color #888888}ram : ${color #888888}$mem${color #888888}/${color #888888}$memmax ${color #888888}- ${color #888888}$memperc%
${color #888888}swap: ${color #888888}$swap${color #888888}/${color #888888}$swapmax ${color #888888}   - ${color #888888}$swapperc%
${color #888888}load: ( ${color #888888}$loadavg ${color #888888})
${color #888888}processes: ${color #888888}$processes   ${color #888888}running: ${color #888888}$running_processes
$stippled_hr
${color #ffccaa}Network:${color #BBBBBB}eth1-
${color #888888}down: ${color #888888}${downspeed eth1} k/s         ${color #888888}up: ${color #888888}${upspeed eth1} k/s
${color #888888}${downspeedgraph eth1 25,100 ff0000 0000ff}       ${color #888888}${upspeedgraph eth1 25,100 0000ff ff0000}
${color #888888}total: ${color #888888}${totaldown eth1}                ${color #888888}TOTAL: ${color #888888}${totalup eth1}
$stippled_hr
$color Free Space-
${color #888888}root : ${color #888888}${fs_used /}${color #888888}/${color #888888}${fs_size /} ${color #888888}(${color #888888}${fs_free /} ${fs_free_perc /}% ${color #888888} free)
       ${fs_bar /}
${color #888888}boot : ${color #888888}${fs_used /boot}${color #888888}/${color #888888}${fs_size /boot} ${color #888888}(${color #888888}${fs_free /boot} ${fs_free_perc /boot}% ${color #888888} free)
       ${fs_bar /boot}
${color #888888}home : ${color #888888}${fs_used /home/rromeo}${color #888888}/${color #888888}${fs_size /home/rromeo} ${color #888888}(${color #888888}${fs_free /home/rromeo} ${fs_free_perc /home/rromeo}% ${color #888888} free)
       ${fs_bar /home/rromeo}
${color #888888}share: ${color #888888}${fs_used /share}${color #888888}/${color #888888}${fs_size /share} ${color #888888}(${color #888888}${fs_free /share} ${fs_free_perc /share}% ${color #888888} free)
       ${fs_bar /share}
$stippled_hr
$color $Processes-
${color #888888}Name            PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #888888} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #888888} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #888888} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color #888888} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}
$stippled_hr
$color Temperatures-
 M/B:$color ${i2c 9191-0290 temp 1} C$color CPU:$color ${i2c 9191-0290 temp 2} C

```

---

### Post by one_stinky_bum on 2006-09-16
I can change the transparency on mine with:
```
own_window_transparent yes
```
and I'm running compiz+aiglx on an i915, albeit on gnome.

I was wondering if one could compose the upload and download graphs, so that one is inverted and both graphs occupy the same space. I was able to do that with samurize (awesome Windoze app)... would be nice if conky could do so too.

---

### Post by hyperair on 2007-07-17
I have that with GKrellM to tell you the truth. =D

---

### Post by albertmatyi on 2007-09-27
Hey! I've figured out that in **gnome & nautilus** icon disappearance can be switched off by having the **own_window** setting set to** yes** in the .conkyrc configuration file. At least this solved my problem. 

Still i've got another issue. When i startup my computer conky will be on top until i restarted even though i've set in the .conkyrc to be below the other windows. 

Anybody met this problem?

___[conkyrc partial content]___

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

on_bottom yes
background yes

double_buffer yes

use_spacer yes
use_xft no

---

### Post by hyperair on 2007-09-27
Make sure Compiz Fusion or Beryl runs BEFORE conky runs.

---

### Post by ddnev45 on 2008-03-20
Thanks for the solutions!

I was having this problem using Gnome+conky (no compiz). Now the only issue is that I can't place an icon on top of the conky display. Since I usually don't keep icons on the desktop, this is only an problem with auto mounted devices and mounted NFS shares. I'll start searching the forum, but does anyone know how to configure Feisty 7.10 so that the auto mounted and nfs share icons appear on the right side of the screen?

---

### Post by zxscooby on 2008-03-20
in your conky.rc file set 
own_window 1
own_window_type override
own_window_transparent 1
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

then install the program feh
```
sudo apt-get install feh
```
and add this code to the end of the conky.rc file 
```
${exec feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`}
```

that will enable conky to be fully transparent in kde

---

### Post by saj0577 on 2008-03-24
> **zxscooby said:**
> in your conky.rc file set 
own_window 1
own_window_type override
own_window_transparent 1
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

then install the program feh
```
sudo apt-get install feh
```
and add this code to the end of the conky.rc file 
```
${exec feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`}
```

that will enable conky to be fully transparent in kde

What about doing the same in gnome? Just delete the "k" before each title?

Saj
Because its showing a background of my old desktop(when not runnnig compiz) not making it transparent.

---

### Post by theZoid on 2008-04-29
> **zxscooby said:**
> in your conky.rc file set 
own_window 1
own_window_type override
own_window_transparent 1
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

then install the program feh
```
sudo apt-get install feh
```
and add this code to the end of the conky.rc file 
```
${exec feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`}
```

that will enable conky to be fully transparent in kde

Here's my .conkyrc file, followed by what it looks like...how can I make it appear transparent with what I've got?  I've had it that way, but desktop icons disappear, thanks!

```
background 1
use_xft yes
xftfont Segoe UI:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window 1
own_window_type override
own_window_transparent 1
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 300 5
maximum_width 300
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$sysname $kernel on $machine

${time %A}$alignr${time %F}

Uptime $alignr $uptime

$nodename $sysname $kernel on $machine
CPU0: ${freq}MHz   $cpu%  $cpubar
CPU1: ${freq}MHz   $cpu%  $cpubar

RAM ($memmax):  $memperc%   ${membar 6}$color
Swap ($swapmax): $swapperc%   ${swapbar 6}$color

Hostname $alignr $nodename
wlan0 $alignr ${addr wlan0}

Download $alignr ${downspeed wlan0} kb/s
${downspeedgraph wlan0}
Upload   $alignr ${upspeed wlan0} kb/s
${upspeedgraph wlan0}

${exec feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`}
```

I figured it out...works, but uses mucho processor time.  Switched to SuperKaramba.

---

### Post by tasos on 2008-05-24
> **hyperair said:**
> Make sure Compiz Fusion or Beryl runs BEFORE conky runs.

How can I do that? Thanx

---

### Post by Crinos512 on 2008-05-29
WHen I run *feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`*

I recieve the following error:

object not accessible
feh: option `--bg-scale' requires an argument
feh - No loadable images specified.
Use feh --help for detailed usage information

--- Screen shots attached ---

[ATTACH]72111[/ATTACH]
[ATTACH]72110[/ATTACH]

--- .conkyrc ---
```

##	.conkyrc configuration
##Aligned position on screen, may be top_left, top_right, bottom_left, bottom_right, or none
alignment top_right

##Boolean value, if true, Conky will be forked to background when started
background yes

##Border margin in pixels
border_margin 5
##Border width in pixels
border_width 5

##Color variables for use inside TEXT segments
#color0
#color1
#color2
#color3
#color4
#color5
#color6
#color7
#color8
#color9

##The number of samples to average for CPU monitoring
cpu_avg_samples 2

##Default color and border color
default_color grey90
##Default outline color
default_outline_color 555555
##Default shading color and border's shading color
default_shade_color black

##Use the Xdbe extension? (eliminates flicker)
##It is highly recommended to use own window with this one so double buffer won't be so big.
double_buffer yes

##Draw borders around text?
draw_borders no
##Draw borders around graphs?
draw_graph_borders yes
##Draw outlines?
draw_outline no
##Draw shades?
draw_shades no

##Font name in X, xfontsel can be used to get a nice font
#font

##Gap, in pixels, between right or left border of screen, same as passing -x at command line, e.g. gap_x 10
gap_x 12
##Gap, in pixels, between top or bottom border of screen, same as passing -y at command line, e.g. gap_y 10.
gap_y 96

##Default global IMAP server. Arguments are: "host user pass [-i interval] [-f folder] [-p port] [-e command]".
##Default port is 143, default folder is 'INBOX', default interval is 5 minutes.
##If the password is supplied as '*', you will be prompted to enter the password when Conky starts.
#imap

##Mail spool for mail checking
#mail_spool $MAIL

##Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections

##Maximum number of special things, e.g. fonts, offsets, aligns, etc. (default is 512)
max_specials 512
##Maximum size of user text buffer, i.e. layout below TEXT line in config file (default is 16384 bytes)
max_user_text 20000
##Size of the standard text buffer (default is 1280 bytes).
text_buffer_size 2000

##Maximum width of window
maximum_width 400
##Minimum size of window
minimum_size 200

##Host of MPD server
#mpd_host
##Port of MPD server
#mpd_port
##MPD server password
#mpd_password
##Music player thread update interval (defaults to Conky's update interval)
#music_player_interval

##The number of samples to average for net data
net_avg_samples 2

##Substract (file system) buffers from used memory?
no_buffers yes

##Force UTF8? requires XFT
override_utf8_locale yes

##Boolean, create own window to draw?
own_window yes
##Manually set the WM_CLASS name. Defaults to "Conky". 	own_window_class
##If own_window_transparent no, set a specified background colour (defaults to black).
##Takes either a hex value (#ffffff) or a valid RGB name (see /usr/lib/X11/rgb.txt)
own_window_colour 000000
##If own_window is yes, you may use these window manager hints to affect the way Conky displays.
##Notes: Use own_window_type desktop as another way to implement many of these hints implicitly.
##If you use own_window_type override, window manager hints have no meaning and are ignored.
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
##Manually set the window name. Defaults to "<hostname> - conky".
#own_window_title
##Boolean, set pseudo-transparency?
own_window_transparent yes
##if own_window is yes, you may specify type normal, desktop or override (default: normal).
##Desktop windows are special windows that have no window decorations; are always visible on your desktop; do not appear in your pager or taskbar; and are sticky across all workspaces.
##Override windows are not under the control of the window manager. Hints are ignored. This type of window can be useful for certain situations.
own_window_type normal

##Print text to stdout.
#out_to_console
##Pad percentages to this many decimals (0 = no padding)
pad_percents 2
##Default global POP3 server. Arguments are: "host user pass [-i interval] [-p port] [-e command]".
##Default port is 110, default interval is 5 minutes. If the password is supplied as '*', you will be prompted to enter the password when Conky starts.
#pop3

##Border stippling (dashing) in pixels
stippled_borders 3

##Total number of times for Conky to update before quitting. Zero makes Conky run forever
total_run_times 0

##Update interval in seconds
update_interval 1.0

##Boolean value, if true, text is rendered in upper case
uppercase no

##Adds spaces after certain objects to stop them from moving other things around.
##Note that this only helps if you are using a mono font, such as Bitstream Vera Sans Mono.
use_spacer right
##Use Xft (anti-aliased font and stuff)
use_xft yes
##Alpha of Xft font. Must be a value at or between 1 and 0.
xftalpha 0.9
##Xft font to use.
xftfont Liberation Sans:size=12

#	*** RHYTHMBOX FORMAT SETTINGS ***

#	${rhythmbox-client --print-playing}
#              Print the title and artist of the playing song

#	${rhythmbox-client --print-playing-format}
#              Print formatted details of the song

#	*** PARAMETERS ***

#       %at    Album title
#       %aT    Album title in lowercase
#       %aa    Album artist
#       %aA    Album artist in lowercase
#       %ay    Release year of album
#       %an    Album disc number
#       %aN    Album disc number with leading zero
#       %ag    Album genre
#       %aG    Album genre in lowercase
#       %tt    Track title
#       %tT    Track title in lowercase
#       %ta    Track artist
#       %tA    Track artist in lowercase
#       %tn    Track number
#       %tN    Track number with leading zero
#       %td    Track duration
#       %te    Elapsed time of track

#       Variables can be combined using quotes. For example "%tn %aa %tt", will
#       print the track number followed by the artist  and  the  title  of  the
#       track.

#After this begins text to be formatted on screen
TEXT
${font Liberation Sans:size=12}${color white}${time %a}, ${time %e %B %G} ${alignr} ${time %H:%M:%S}$font
${color #9999FF}${hr 1}
${font Liberation Sans:size=8}${color white}${execi 60000 grep -m1 'model name' /proc/cpuinfo | sed -e 's/model name.*: //'}
    | ${color white}Core 0 @ ${acpitemp}C ${alignr} ..:: ${freq_dyn_g cpu1}Ghz ::..
    `- Usage: ${cpu cpu1}% ${color white}${cpubar cpu1}
    | ${color white}Core 1 @ ${acpitemp}C ${alignr} ..:: ${freq_dyn_g cpu2}Ghz ::..
    `- Usage: ${cpu cpu2}% ${color white}${cpubar cpu2}
  ${color #9999FF}RAM Usage: ${alignr}${color white} $mem/$memmax - $memperc%
  $membar
  ${color #9999FF}Processes Loaded:${color white} $processes${alignr} ${color #9999FF}Running:${color white} $running_processes
  ${cpugraph 333333 ffffff}

${color #9999FF}File Systems: ${hr 1}
  ${color white}/ ${alignr} ${fs_free /} (${fs_free_perc /}%) free of ${fs_size /}
  ${fs_bar /}
  ${color white}/home ${alignr} ${fs_free /home} (${fs_free_perc /home}%) free of ${fs_size /home}
  ${fs_bar /home}${if_mounted /media/PTAH}
  ${color white}/media/PTAH ${alignr} ${fs_free /media/PTAH} (${fs_free_perc /media/PTAH}%) free of ${fs_size /media/PTAH}
  ${fs_bar /media/PTAH}${endif}

${color #9999FF}Network: ${hr 1}
  ${color #9999FF}Wired ( ${color #ff9900}${addr eth0}${color #9999FF} )
    ${color white}| down ${color #ff9900}${downspeedf eth0} ${color white}k/s ${alignr}${color white}up ${color #0099ff}${upspeedf eth0} ${color white}k/s
    `- ${color white}total down: ${totaldown eth0} ${alignr} total up: ${totalup eth0}
  ${color #9999FF}Modem ( ${color #ff9900}${addr ppp0}${color #9999FF} )
    ${color white}| down ${color #ff9900}${downspeedf ppp0} ${color white}k/s ${alignr}${color white}up ${color #0099ff}${upspeedf ppp0} ${color white}k/s
    `- ${color white}total down: ${totaldown ppp0} ${alignr} total up: ${totalup ppp0} $color$stippled_hr${if_running amarok}


${color #9999FF}Music: ${hr 1}
${color}${alignc}Now Playing${color white}
${alignc}${execi 100 ~/.conky/amarok.sh artist}
${alignc}${execi 100 ~/.conky/amarok.sh title}
${execibar 1 ~/.conky/amarok.sh progress}
${alignc}"${execi 100 ~/.conky/amarok.sh album}"
${alignc}${execi 100 ~/.conky/amarok.sh year} - ${color white}${alignc}${execi 100 ~/.conky/amarok.sh genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 100 ~/.conky/amarok.sh totalArtists} $color${alignr}Compilations: ${color white}${execi 100 ~/.conky/amarok.sh totalCompilations}$color
Albums:  ${color white}${execi 100 ~/.conky/amarok.sh totalAlbums} $color${alignr}Genres: ${color white}${execi 100 ~/.conky/amarok.sh totalGenres}$color
Tracks:  ${color white}${execi 100 ~/.conky/amarok.sh totalTracks}
$color$stippled_hr
${alignc}Collection Statisctics
Most songs by ${color white}${execi 100 ~/.conky/amarok.sh most_songs_by_artist} $alignr${color}(${color white}${execi 100 ~/.conky/amarok.sh most_songs_by_artist_n}${color})
Most songs are ${color white}${execi 100 ~/.conky/amarok.sh most_songs_are_genre} $alignr${color}(${color white}${execi 100 ~/.conky/amarok.sh most_songs_are_genre_n}${color})
Most songs during ${color white}${execi 100 ~/.conky/amarok.sh most_songs_during_year} $alignr${color}(${color white}${execi 100 ~/.conky/amarok.sh most_songs_during_year_n}${color})
Most albums by ${color white}${execi 100 ~/.conky/amarok.sh most_albums_by_artist} $alignr${color}(${color white}${execi 100 ~/.conky/amarok.sh most_albums_by_artist_n}${color})
Most albums are ${color white}${execi 100 ~/.conky/amarok.sh most_albums_are_genre} $alignr${color}(${color white}${execi 100 ~/.conky/amarok.sh most_albums_are_genre_n}${color})
Most albums during ${color white}${execi 100 ~/.conky/amarok.sh most_albums_during_year} $alignr${color}(${color white}${execi 100 ~/.conky/amarok.sh most_albums_during_year_n}${color})$endif

${exec feh --bg-scale 'dcop kdesktop KBackgroundIface currentWallpaper 1'}

```

---

### Post by Crinos512 on 2008-05-31
entering [COLOR="#0000ff"]${exec feh --bg-scale '/path/to/my/wallpaper'}[/COLOR] into conky works!

typing [COLOR="#0000ff"]grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11[/COLOR] gets my wallpaper and path from the plasma config file. 

entering [COLOR="#0000ff"]${exec feh --bg-scale 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'}[/COLOR] does not work :(

what am I doing wrong? :confused:

---

### Post by chepioq on 2008-07-08
@Crinos512
Hello
I have the same problem and I saw your tread 
Firs tank for your help...
And I see what your are doing wrong...The syntaxe is not:
```
${exec feh --bg-scale 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'}
```
but:
```
${exec feh -u --bg-scale 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'}
```

It's work for me
==EDIT==

I re-start my laptop and now that don't work :confused:

---

### Post by Crinos512 on 2008-07-08
RE: [COLOR="Blue"]feh -u --bg-scale 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'[/COLOR]

the -u according to [COLOR="#0000ff"]feh --help[/COLOR] does the following:
> "Don't display images. Just print out their name if imlib2 can NOT successfully load them."

I DO want the image displayed. :(

---

### Post by Crinos512 on 2008-07-08
Intresting read that help....
> "Feh stores the commandline necessary to restore the background you chose in ~/.fehbg. So to have feh-set backgrounds restored when you restart X, add the line [COLOR="Blue"]eval `cat $HOME/.fehbg`[/COLOR] to your X startup script (e.g. ~/.xsession). Note that you only need to do this for non E window managers."

So in theory if you 
[LIST]
[*]add the line [COLOR="Blue"]eval `cat $HOME/.fehbg`[/COLOR] to your X startup script
[*]edit the ~/.fehbg file to add [COLOR="Blue"]'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'[/COLOR] as the wallpaper to be used
[/LIST]
then the X Background should match the plasma background on every boot... Theory is good, right?

Not on -buntu ATM... will fight with this some tonight after work.

---

### Post by chepioq on 2008-07-08
:( That's don't work...When I do ```
eval `cat $HOME/.fehbg`
```
in console I have:
```
[dominique@localhost ~]$ eval `cat $HOME/.fehbg`
bash: grep wallpaper= ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11: Aucun fichier ou dossier de ce type

```

---

### Post by Crinos512 on 2008-07-08
well shoot....

was there anything in ~/.fehbg before you edited it?

---

### Post by chepioq on 2008-07-08
no there is nothing in ~/.fehbg

---

### Post by Crinos512 on 2008-07-08
What if you set the contents of ~/.fehbg to
> [COLOR="Blue"]feh --bg-scale 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'[/COLOR]

then what happens when you [COLOR="Blue"]eval `cat $HOME/.fehbg`[/COLOR]

---

### Post by chepioq on 2008-07-09
If I set :
feh --bg-scale 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'
in ~/.fehbg
and I do:eval `cat $HOME/.fehbg`
I have:
```
[dominique@localhost ~]$ eval `cat $HOME/.fehbg`
feh WARNING: grep wallpaper= ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11 - File does not exist
feh ERROR: Couldn't load image in order to set bg

```
But if I set /path/of/my/wallpaper that work...
I think feh don't like command lines...:)

---

### Post by Crinos512 on 2008-07-09
well... If I use [COLOR="#0000ff"]grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11[/COLOR] in a konsole, it returns > [COLOR="Purple"]/home/crinos/Pictures/Void_by_Angel_Valis.jpg[/COLOR]

If I use [COLOR="Blue"]feh --bg-scale /home/crinos/Pictures/Void_by_Angel_Valis.jpg[/COLOR]in a konsole, it works perfectly making the backgrounds match nicely.

but it's like feh does not like using piped commands.

I have tried 
[LIST]
[*][COLOR="#0000ff"]feh --bg-scale  'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'[/COLOR]
[*][COLOR="#0000ff"]grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11 | feh --bg-scale[/COLOR]
[/LIST]
... neither one works. :(

---

### Post by chepioq on 2008-07-09
:confused:
I think that make a bash-script solve problem...
But i don't know how make it...

---

### Post by chepioq on 2008-07-09
Hello Crinos512...
This command:
```
grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11 > ~/.fehbg
```
over-write the .fehbg file, but when I do eval `cat $HOME/.fehbg` I have this error:
```
[dominique@localhost ~]$ eval `cat $HOME/.fehbg`
bash: /home/dominique/Images/gecko3.jpg: Permission non accordée
```
as in user or root...
And I don't see why...
With this method .fehbg are wrong permission?
But when I look for permission .fehbg have this for my user...
(for resolve delete ~/.fehbg and re-run "feh --bg-scale '/home/dominique/Images/gecko3.jpg'" and after eval `cat $HOME/.fehbg`)

---

### Post by chepioq on 2008-07-09
The #26 post is bad and I am stupid...
I am tired and my brain is out...
Don't try this...

---

### Post by Crinos512 on 2008-07-09
> **chepioq said:**
> Hello Crinos512...
This command:
```
grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11 > ~/.fehbg
```
over-write the .fehbg file, but when I do eval `cat $HOME/.fehbg` I have this error:
```
[dominique@localhost ~]$ eval `cat $HOME/.fehbg`
bash: /home/dominique/Images/gecko3.jpg: Permission non accordée
```
as in user or root...
And I don't see why...
With this method .fehbg are wrong permission?
But when I look for permission .fehbg have this for my user...
(for resolve delete ~/.fehbg and re-run "feh --bg-scale '/home/dominique/Images/gecko3.jpg'" and after eval `cat $HOME/.fehbg`)

OK, the problem here is that $HOME/.fehbg contains the path and filename to the picture, but not the [COLOR="Blue"]feh[/COLOR] command, so that when you try to [COLOR="#0000ff"]eval[/COLOR]uate the contents of the file there is'nt a command to actually run.

if you set the contents of ~/.fehbg to 
> [COLOR="Purple"]feh --bg-scale '/home/dominique/Images/gecko3.jpg'[/COLOR] and then [COLOR="Blue"]eval `cat $HOME/.fehbg'[/COLOR] should work.... the problem is when you change your background in KDE it won't change in the feh command.

---

### Post by Crinos512 on 2008-07-09
Hmmm..,

try this:
[COLOR="Blue"]grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11 > ~/.fehbg && feh --bg-scale 'cat ~/.fehbg'[/COLOR]

if that works then try this as the 1st line of yer .conkyrc

[COLOR="Blue"]${execi 10000 grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11 > ~/.fehbg && feh --bg-scale 'cat ~/.fehbg'} [/COLOR]

---

### Post by Crinos512 on 2008-07-09
OK, Disregard all of that.... :D


[LIST=1]
[*]Create a script [COLOR="Purple"]~/set_wallpaper[/COLOR] as follows: 
> #!/bin/bash
feh --bg-scale $1
[*]Make ~/set_wallpaper executable.
[*]try [COLOR="Blue"]~/set_wallpaper 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'[/COLOR] in a konsole.
[*]If that works put the following in your .conkyrc
> [COLOR="#0000ff"]${execi 10000 ~/set_wallpaper 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'}[/COLOR]
[*]If that works ... be happy!
[/LIST]

Oh, and you will be able to delete the [COLOR="Purple"]~/.fehbg[/COLOR] file.

---

### Post by chepioq on 2008-07-09
:confused::confused::confused:
that's don't work
```
[dominique@localhost ~]$ ~/set_wallpaper 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11' 
feh: unrecognized option '--bytes=+11'
feh WARNING: wallpaper= does not exist - skipping
feh WARNING: ~/.kde/share/config/plasma-appletsrc does not exist - skipping
feh WARNING: | does not exist - skipping
feh WARNING: tail does not exist - skipping
feh WARNING: grep - File does not exist
feh ERROR: Couldn't load image in order to set bg
[dominique@localhost ~]$ 
```

---

### Post by Crinos512 on 2008-07-09
try this:
[COLOR="Blue"]grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11 | ~/set_wallpaper[/COLOR]

---

### Post by chepioq on 2008-07-09
:(:(:(
grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11 | ~/set_wallpaper return:
```
[dominique@localhost ~]$ grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11 | ~/set_wallpaper
feh: option '--bg-scale' requires an argument
feh - No loadable images specified.
Use feh --help for detailed usage information

```
](*,)](*,)](*,)
I am tired after a long day of work.
Wait and see tomorrow...
Good night
chepioq

---

### Post by chepioq on 2008-07-10
Hello Crinos512
With help of Pikachu_2014 and Fox Delta from fedora-fr.org, I made this script:
```
#!/bin/bash
fond=`grep 'wallpaper=' ~/.kde/share/config/plasma-appletsrc | tail --bytes=+11`
echo $fond
feh --bg-scale $fond
```
Name this script with how you want ( I name his "Fond_d'ecran") and give it executable
And that work!!!
But I don't know how to integrate it in my conkyrc...

---

### Post by chepioq on 2008-07-10
And there are a little problem.
When I change my wallpaper there is one minute between I change wallpaper and this inscription in /home/dominique/.kde4/share/config/plasma-appletsrc also my script work after one minute...
:-k:-k:-k

---

### Post by Crinos512 on 2008-07-10
to embed the script into Conky place the following under [COLOR="DarkOrange"]TEXT[/COLOR] in your .conkyrc

[COLOR="Blue"]${execi 10000 script}[/COLOR]    (where [COLOR="Blue"]script[/COLOR] is the path and name of the script)

mine is [COLOR="#0000ff"]${execi 10000 ~/.conky/wallpaper.sh}[/COLOR]

...looks like you should remove the echo line out of the script though as it will cause conky to display the value of $fond.

---

### Post by Crinos512 on 2008-07-10
it's kinda odd that there would be a delay in updating that file....

---

### Post by chepioq on 2008-07-11
kde4.08 is a beta and I think it is a bug...
when there are kde4.1 at the end of July maybe that is solve...

---

### Post by chepioq on 2008-07-11
I place:
```
${execi 100 /home/dominique/.conkyrc/Fond}
```
under TEXT in my conkyrc and that work...
When I change wallpaper, after 2 minutes the new wallpaper appear under conky...:guitar::KS:guitar:
Thank for your help Crinos512
You do a very good job...
P.S.
Script also work when I remove "echo $fond" in text...

---

### Post by Crinos512 on 2008-07-11
oddly mine does not work ... :(

---

### Post by chepioq on 2008-07-11
Aie,Aie,Aie...(french expression)
I tell you what I do:
-1) install feh

-2) create a script in /home/~/.kde/Autostart with:
```
#!/bin/bash
eval `cat $HOME/.fehbg`
conky -c .conkyrc/.conkyrc1 &
```
adapt path of your conkyrc (mine is conkyrc1 because I have a conkyrc for gnome) and give it executable
 
-3)create a script in /home/~/.conkyrc (name "Fond"in my case):
```
#!/bin/bash
fond=`grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11`
feh --bg-scale $fond
```
and give it executable

-4)add in your .conkyrc file just under "TEXT":
```
${execi 100 /home/dominique/.conkyrc/Fond}
```

and that's all... that work for me (I re-test twice since I read your post).

Have you an error message?

---

### Post by chepioq on 2008-07-11
I forget:
When I change wallpaper the new wallpaper appear under conky after approximately 2 minutes...

---

### Post by chepioq on 2008-07-14
I see they are problems with name of wallpaper:
for exemple if my wallpaper name is: Qs XScape 1280.jpg , that don't work, but if it is: Qs_XScape_1280.jpg it's good...
If that help you...

---

### Post by Crinos512 on 2008-07-14
Woot!

Long distance 'thank you's

it works like a champ :D

---

### Post by chepioq on 2008-07-14
Thank for your thank...
Now I make a little tuto for my distrib... Fedora F9 [http://forums.fedora-fr.org/viewtopic.php?id=33821]("http://forums.fedora-fr.org/viewtopic.php?id=33821") post #8
And I cite you for your help...
Ubuntu and Fedora are same family (Linux) and I think it's a good thing that we help together (excuse my bad English).
I also think that you made a tuto for Ubuntu...

---

### Post by chepioq on 2008-07-18
Hello Crinos...
I have solution for wallpaper with blank space in their name.
In script Fond I replace ```
feh --bg-scale $fond
``` by ```
feh --bg-scale "$fond"
```
My new script are:
```
#!/bin/bash
fond=`grep 'wallpaper=' ~/.kde/share/config/plasma-appletsrc | tail --bytes=+11`
feh --bg-scale "$fond"
```
And that work...
Please try this and say me if that work for you...

---

### Post by Crinos512 on 2008-07-18
Doh, I shoulda thought of that...

Great work!

---

### Post by chepioq on 2008-07-18
thank for thank :)
Now I want solve this:
feh --bg-scale 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11' who return:

```
[dominique@localhost ~]$  feh --bg-scale 'grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11'
feh WARNING: grep wallpaper= ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11 - File does not exist
feh ERROR: Couldn't load image in order to set bg

```

I search...](*,)](*,)](*,)

---

### Post by m_duck on 2008-07-18
I'm not sure why this works as I have only dabbled in using KDE, but when I did, the solution I found was (I cannot remember where I found it):

Install feh
```
sudo apt-get install feh
```Add this line to the bottom of your .conkyrc file
```
${exec feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`}
```I think this should do it. Although if you change your wallpaper while conky is running, you may have to kill and restart it. I suppose alternatively you could change the "exec" part to "execi #" where # is a number in seconds for how often it should check for a new wallpaper.

Then again I could be talking out the wrong end......

---

### Post by chepioq on 2008-07-18
@m_duck 
${exec feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`}
That work for kde 3 but not for kde 4...
In kde4 dcop is remplaced by dbus...

---

### Post by Crinos512 on 2008-07-18
And to make things worse, the "Wallpaper" that you define in KDE4 Destop Settings is actually just setting the background for another layer called *plasma* which covers the X screen... not the X screen itself. In my case the X screen remaind this retina searin shade of blue.

[COLOR="#0000ff"]feh --bg-scale[/COLOR] changes the X screen Wallpaper, and we are trying to have the feh command automatically match the plasma settings (which can be found in the file "~/.kde4/share/config/plasma-appletsrc") and yes, in concert with {execi } make Conky handle refreshing any changes made to the wallpaper.

---

### Post by chepioq on 2008-07-20
Hello Crinos...
I am stupide because solution is on the post...
You know that:
```
feh --bg-scale `grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11`
```
don't work...
But...
```
feh --bg-scale "`grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11`"
```
WORK!!!!!!!!!
Also we don't need fond-script...
Now the new tuto is
1)Install feh

2)Create a script in /home/~/.kde4/Autostart with:
```
#!/bin/bash
eval `cat $HOME/.fehbg`
conky -c .conkyrc/.conkyrc1 &
```
adapt path of your conkyrc (mine is conkyrc1 because I have a conkyrc for gnome) and give it executable
3)add in your .conkyrc file just under "TEXT":
```
${execi 100 feh --bg-scale "`grep 'wallpaper=' ~/.kde4/share/config/plasma-appletsrc | tail --bytes=+11`"}
```
And that's work for me...
Please try this and say me if it's work for you

---

### Post by Crinos512 on 2008-07-20
OH. MY. GHOD....

It works! <happy dance>

I cannot thank you enough, chepioq.

---

### Post by chepioq on 2008-07-20
Thank for you...
If I don't see this thread on google, I make nothing...
Now I chearch how replace dcop by dbus in:
feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`
But my knowledge is very bad...
There is tuto on kde site [http://techbase.kde.org/Development/Tutorials#D-Bus]("http://techbase.kde.org/Development/Tutorials#D-Bus") and for me that is very difficult...:lolflag:

---

### Post by chepioq on 2008-07-21
Hello Crinos..
Last change:
For testing I remove the "eval `cat $HOME/.fehbg`" line in the "/home/~/.kde4/Autostart" script.
And that also work...

---

