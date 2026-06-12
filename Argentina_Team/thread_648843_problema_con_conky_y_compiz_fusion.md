---
title: "problema con conky y compiz fusion"
date: 2007-12-24
forum: Argentina Team
---

### Post by Skavenger on 2007-12-24
como dice el titulo, tengo un problema con estas dos aplicaciones. en sessions agregue a conky para que inicie automaticamente, pero se ve que hay conflicto compiz fusion porque se me ve asi o.Ö

[[IMG]http://img227.imageshack.us/img227/6175/conkydelortoyk2.th.png[/IMG]](http://img227.imageshack.us/my.php?image=conkydelortoyk2.png)

si lo inicio desde la consola se ve sin bordes
[http://ubuntuforums.org/showpost.php?p=4006328&postcount=142](http://ubuntuforums.org/showpost.php?p=4006328&postcount=142)

revise la configuracion y aunque no entiendo mucho, no veo nada raro como para que se vean los bordes y eso, ademas de que no muestra el alto completo, lo corta =/ y ademas si pongo un archivo en ese lugar o una ventana como en la screenshot, el conky lo tapa y no puedo ver lo que hay abajo

por las dudas aca dejo mi .conkyrc

```
# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

#on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 300

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 70
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
#xmms_player bmp

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
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}

TEXT
${font bold:size=26}${color ffffff}${time %I:%M %p}$color$font
${font bold:size=8}${color ffffff}${time %A %B, %d %Y}$color$font

${voffset -2}${color DAA520}UBUNTU$color
${color DAA520}${voffset -6}$hr${color}
${font bold:size=15}${color ffffff} $nodename$color$font - $sysname $kernel on $machine$font

${voffset -2}${color DAA520}STATUS$color
${color DAA520}${voffset -6}$hr${color}
${color #CCCCCC} Uptime:${color lightgrey} $uptime ${color #CCCCCC} - Load:${color lightgrey} $loadavg
 Processes Running: $processes
 Active Processes: $running_processes
 Processes Detail:         PID    ${offset 4}  CPU       MEM
 ${color #B26B59}${offset 17}${top name 1}${alignr}${offset -1}${top pid 1}    ${top cpu 1}    ${top mem 1}$color
 ${offset 17}${top name 2}${alignr}${offset 6}${top pid 2}    ${top cpu 2}    ${top mem 2} 
 ${offset 17}${top name 3}${alignr}${top pid 3}    ${top cpu 3}    ${top mem 3}
 ${offset 17}${top name 4}${alignr}${top pid 4}    ${top cpu 4}    ${top mem 4}
 ${offset 17}${top name 5}${alignr}${top pid 5}    ${top cpu 5}    ${top mem 5}

${voffset -2}${color DAA520}${shadecolor 202020}PROCESSOR$color
${color DAA520}${voffset -6}$hr${color}
${color #CCCCCC} ${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
${color #CCCCCC} Usage:${color #CCCCCC} ${color lightgrey}${cpu}% ${color #CCCCCC}${cpubar}
${color #CCCCCC} ${cpugraph 000000 CCCCCC}

${voffset -2}${color DAA520}${shadecolor 202020}MEMORY$color
${color DAA520}${voffset -6}$hr${color}
${color #CCCCCC} RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #CCCCCC}${membar 5,110}
${color #CCCCCC} SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #CCCCCC}${swapbar 5,110}

${voffset -2}${color DAA520}${shadecolor 202020}STORAGE$color
${color DAA520}${voffset -6}$hr${color}
${color #CCCCCC} Root: ${color lightgrey}${fs_used /}/${fs_size /} ${alignr}${color #CCCCCC}${fs_bar 5,120 /}
${color #CCCCCC} Home: ${color lightgrey}${fs_used /home}/${fs_size /home} ${alignr}${color #CCCCCC}${fs_bar 5,120 /home}
${color #CCCCCC} Win XP: ${color lightgrey}${fs_used /media/sda1}/${fs_size /media/sda1} ${alignr}${color #CCCCCC}${fs_bar 5,120 /media/sda1}
${color #CCCCCC} Disk: ${color lightgrey}${fs_used /media/sda5}/${fs_size /media/sda5} ${alignr}${color #CCCCCC}${fs_bar 5,120 /media/sda5}

${voffset -2}${color DAA520}${shadecolor 202020}NETWORK$color
${color DAA520}${voffset -6}$hr$color
${color #CCCCCC} IP: ${color lightgrey}${addr eth0}
${color #CCCCCC} Down Speed:${color lightgrey} ${downspeed eth0} Kb/s $alignr${color #CCCCCC} Up Speed:${color lightgrey} ${upspeed eth0} Kb/s
${color #CCCCCC} ${downspeedgraph eth0 27,130 000000 CCCCCC 180} $alignr${color #CCCCCC}${upspeedgraph eth0 27,130 000000 CCCCCC 25}
${color lightgrey} Total Down: ${totaldown eth0}           $alignr${color lightgrey} Total Up: ${totalup eth0}

${color #CCCCCC} Port(s)${alignr} # Connections
${color #CCCCCC} Inbound: ${color lightgrey}${tcp_portmon 1 32767 count}  ${color #CCCCCC}Outbound: ${color lightgrey}${tcp_portmon 32768 61000 count}${alignr}${color #CCCCCC}Total: ${color lightgrey}${tcp_portmon 1 65535 count}

${voffset -2}${color DAA520}${shadecolor 202020}WEATHER$color
${color DAA520}${voffset -6}$hr$color
${color #CCCCCC}${execi 60 /usr/bin/pymetar SACO}$color
```

espero puedan ayudarme a solucionar esto

gracias!

---

### Post by matog on 2008-01-06
Tengo exactamente el mismo problema...
Acá va mi configuración de Conky (la saqué de un post del foro):
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
${color orange}SISTEMA ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NOMBRE           PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORIA / DISCOS ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}$color
hdb3:  ${fs_free_perc /media/hdb3}%   ${fs_bar 6 /media/hdb3}

${color orange}RED (${addr eth0}) ${hr 2}$color
Bajada: $color${downspeed eth0} k/s ${alignr}Subida: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}CITAS ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

---

