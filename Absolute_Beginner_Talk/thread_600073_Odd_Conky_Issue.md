---
title: "Odd Conky Issue"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2007-11-01
Conky is set to begin on startup for me but I am having some odd issue and I cannot figure out what is doing it.  Whenever I drag a program over conky, whatever covered it is missing from the display for a moment.  Here's a screenshot so you know what I am talking about.

Before:
[http://s24.photobucket.com/albums/c45/sigplace/?action=view&current=Before.png](http://s24.photobucket.com/albums/c45/sigplace/?action=view&current=Before.png)

After Minimizing:
[http://s24.photobucket.com/albums/c45/sigplace/?action=view&current=after.png](http://s24.photobucket.com/albums/c45/sigplace/?action=view&current=after.png)

And of course, my .conkyrc

```

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,sticky
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.8
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
own_window_colour brown
own_window_transparent yes
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25

TEXT
${color white}${color black}[${color white}$nodename${color black}]:
${color white}$sysname $kernel Uptime: $uptime
${color red}CPU ${hr 1}$color
${color black}Load: ${color white}${loadavg}   ${color black}Temp: ${color white}${acpitempf}F ${color black}(Fan: ${color white}${acpifan}${color black})
${color black}Processes: ${color white}$processes	${color black}Running: ${color white}$running_processes
${color black}CPU Load: ${color white}${cpu}%
${cpugraph 00ff00 ffffff}
${color black}NAME             $alignr PID       CPU%      MEM%${color white}
${color #ffff00}${top name 1} $alignr ${top pid 1}   ${top cpu 1}    ${top mem 1}${color white}
${top name 2} $alignr ${top pid 2} ${top cpu 2}    ${top mem 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}    ${top mem 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}    ${top mem 4}
${color red}MEMORY / DISK ${hr 1}$color
${color black}RAM :  ${color white}$memperc% ${color black}(${color white}${mem} / ${memmax}${color black})
${color black}Swap:  ${color white}$swapperc% ${color black}(${color white}${swap} / ${swapmax}${color black})

${color black}DiskIO:${color white}${diskio} 
${diskiograph 00ff00 ffffff}
${color black}Root:  ${color white}${fs_free_perc /}% ${color black}(${color white}${fs_used /} / ${fs_size /}${color black})
${color black}ISO :  ${color white}${fs_free_perc /media/hda1}% ${color black}(${color white}${fs_used /media/hda1} / ${fs_size /media/hda1}${color black})
${color black}APPS:  ${color white}${fs_free_perc /media/hdb1}% ${color black}(${color white}${fs_used /media/hdb1} / ${fs_size /media/hdb1}${color black})
${color red}NETWORK (${addr eth0}) ${hr 1}$color
${color black}Down: ${color white}${downspeed eth1}k/s ${alignr}${color black}Up: ${color white}${upspeed eth1}k/s
${downspeedgraph eth1 25,140 ff0000 00ff00} ${alignr}${upspeedgraph eth1 
25,140 00ff00 ff0000}
${color black}Total: ${color white}${totaldown eth1} ${alignr}${color black}Total: ${color white}${totalup eth1}
${color black}Inbound: ${color white}${tcp_portmon 1 32767 count} ${color black}Outbound: ${color white}${tcp_portmon 32768 
61000 count}${alignr}${color black}Total: ${color white}${tcp_portmon 1 65535 count}
${color black}Connections ${color white}${tcp_portmon 32768 61000 count} ${alignr} ${color black}Service/Port${color white}
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
${color red}LOGGING ${hr 1}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

```

---

### Post by Crafty Kisses on 2007-11-01
I've had the same issue, it's if you move a window over Conky it dissapears, it's really weird. :(

---

### Post by ajmorris on 2007-12-27
It is the config file :)
This configuration for your conky yields no lag, try this: This has no lag, just fiddle with it to suit your needs ```
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

on_bottom yes

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
maximum_width 260

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
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 70
alignment top_right
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
xmms_player bmp

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
${color #0077ff}$sysname $kernel $machine - $nodename 

${color #0077ff}Uptime:${color lightgrey} $uptime ${color #0077ff} Load:${color lightgrey} $loadavg

${color #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
${color #0077ff}Usage:${color #0077ff} ${color lightgrey}${cpu}% ${color #0077ff}${cpubar}
${color #0077ff}${cpugraph 000000 0077ff}
${color #0077ff}Proces:${color lightgrey} $processes  ${color #0077ff}Run:${color lightgrey} $running_processes ${color #0077ff}CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} ${color #0077ff}MB:${color lightgrey} ${i2c temp 1}C

${color #0077ff}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #0077ff}${membar 5,110}
${color #0077ff}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #0077ff}${swapbar 5,110}

${color #0077ff}HD IO: ${color lightgrey}${diskio} ${alignr}${color #0077ff}Temperature: ${color lightgrey}${execi 10 /home/admin/.bin/hddconky}C
${color #0077ff}${diskiograph 000000 0077ff}

${color #0077ff}Hard Disks:
${color #0077ff} Root ${color lightgrey}${fs_used /}/${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}
${color #0077ff} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}
${color #0077ff} Data ${color lightgrey}${fs_used /media/data}/${fs_size /media/data}${alignr}${color #0077ff}${fs_bar 5,120 /media/data}

${color #0077ff}CPU Usage         PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0077ff} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0077ff} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #0077ff}Mem Usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0077ff} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0077ff} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #0077ff}Network: ${color lightgrey}${addr eth0}

${color #0077ff}Down:${color lightgrey} ${downspeed eth0} k/s $alignr${color #0077ff} Up:${color lightgrey} ${upspeed eth0} k/s
${color #0077ff}${downspeedgraph eth0 27,120 000000 0077ff 180} $alignr${color #0077ff}${upspeedgraph eth0 27,120 000000 0077ff 25}
${color lightgrey}${totaldown eth0}           $alignr${color lightgrey}${totalup eth0}

${color #0077ff}Port(s)${alignr}#Connections
${color #0077ff}Inbound: ${color lightgrey}${tcp_portmon 1 32767 count}  ${color #0077ff}Outbound: ${color lightgrey}${tcp_portmon 32768 61000 count}${alignr}${color #0077ff}Total: ${color lightgrey}${tcp_portmon 1 65535 count}

${color #0077ff}Inbound Connection ${alignr} Local Service/Port${color lightgrey}
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
 ${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}
```

---

### Post by ajmorris on 2007-12-27
it also appears as if the long lines for your headings does some sort of lag, as removing those is reducing lag time... at least for me anyway...
I mean the lines like this: ```
${color #00ced1}NETWORK (${addr eth0}) ${hr 1}$color
```

---

### Post by adam.tropics on 2007-12-27
I get that if Compiz is disabled. When Compiz is running, it's all fine.

---

### Post by ajmorris on 2007-12-28
unfortunately adam, not all of us use compiz, i myself use the ever great WM, OpenBox, so do not and can not use compiz.
But, after removing the lines for headers, i only get lag occasionally, but when i remove the multi-coloured graphs, i get no lag at all.

---

### Post by ajmorris on 2007-12-29
I apologise adam, although compiz can not be run on OB, a composite manager is the way to go, to all those running flux, or openbox or other WMs that cannot use compiz, if you wish to eliminate all the lag, (without removing some of the better eye-candy options in conky) install xcompmgr (sudo apt-get install xcompmgr), start it by xcompmgr and add it to boot.

---

### Post by adam.tropics on 2007-12-29
lol. There is a God!!

---

### Post by urukrama on 2007-12-29
Xcompmgr interferes with conky in the same way you describe Compiz does. I haven't found a solution for this (yet). Alternatively, you can use [gkrellm]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html"). Its defaults don't look very good, but if you use the 'invisible' skin it is quite all right. Gkrellm doesn't interfere with xcompmgr (or vice versa)

If you want to use xcompmgr, [this]("http://ubuntuforums.org/showthread.php?t=75527") thread will be useful.

---

### Post by ajmorris on 2008-01-02
> **urukrama said:**
> Xcompmgr interferes with conky in the same way you describe Compiz does. I haven't found a solution for this (yet). Alternatively, you can use [gkrellm]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html"). Its defaults don't look very good, but if you use the 'invisible' skin it is quite all right. Gkrellm doesn't interfere with xcompmgr (or vice versa)

If you want to use xcompmgr, [this]("http://ubuntuforums.org/showthread.php?t=75527") thread will be useful.

what interference are you referring to with xcompmgr?
And, grellm, isnt as good as conky IMO, conky is way more slick

---

