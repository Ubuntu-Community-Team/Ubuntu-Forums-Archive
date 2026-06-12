---
title: "[SOLVED] system monitering"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2008-01-18
Hi I'm trying to find an app that in my top menu bar will show my system stats I only want how much memory I am using how filled my hardrive is and how much of my cpu I'm using prefrebly 2 graphs one for each core.

---

### Post by eolson on 2008-01-18
system > administration > system monitor

---

### Post by Nem1976 on 2008-01-18
I know this doesn't work on your Menu bar but have you checked out Conky?

Here is a screenshot of what my conky looks like.

---

### Post by chris200x9 on 2008-01-18
conky looks perfect thanx! :)

---

### Post by Nem1976 on 2008-01-18
Welcome.

Here is a great thread regarding conky.  I have spent so much time reading and looking at other users configs.  

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

---

### Post by andy gee on 2008-01-19
Yup, Conky is great, but don't forget about good old gkrellm! 

It's been around for a good while, pretty well bug free, has lots and lots of skins. It's really easy to configure (compared to conky, anyway) and works well with Gnome, fluxbox and Xfce (and probably others, but those are the ones i've tried myself).

It's v easy to install from the Ubuntu repos. Give it a try! Check out how it looks in Fluxbuntu in the attached screenshot. It's the blue section on the right side of the screen. there's also a close up of it there.

The Screenshot is actually taken by one of the gkrellm addons - look at the bottom box, it allows you to "Lock" ie lock the desktop or "Shoot" ie screenshot. Cool, eh?

Any questions?

---

### Post by andy gee on 2008-01-19
BTW Nem1976, could you  *please* post your .conkyrc? Its one of the nicer Conky's I've seen, wouldn't mind having it myself!

---

### Post by Nem1976 on 2008-01-19
> **andy gee said:**
> BTW Nem1976, could you  *please* post your .conkyrc? Its one of the nicer Conky's I've seen, wouldn't mind having it myself!

Yep here you go.  Enjoy.

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
# xftalpha 0.8
xftalpha 100

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
gap_x 45
gap_y 75
alignment bottom_right
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
${color #ffa200}$nodename :${color #0077ff}$sysname $kernel $machine  
${color #0077ff}Uptime:${color lightgrey} $uptime ${color #0077ff} Load:${color lightgrey} $loadavg

${color #0077ff}Usage:${color #0077ff} ${color lightgrey}${cpu}% ${color #0077ff}${cpubar}
${color #0077ff}${cpugraph 0077ff 00ff00}
${color #0077ff}Proces:${color lightgrey} $processes  ${color #0077ff}Run:${color lightgrey} $running_processes ${color #0077ff}CPU:${color lightgrey} ${acpitemp}C${color lightgrey} ${color #0077ff}MB:${color lightgrey} ${i2c temp 1}C

${color #0077ff}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #0077ff}${membar 5,110}
${color #0077ff}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #0077ff}${swapbar 5,110}

${color #0077ff}Hard Disks:
${color #0077ff} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color green}${fs_bar 5,100 /home}
${color #0077ff} Backup ${color lightgrey}${fs_used /media/backup}/${fs_size /media/backup}${alignr}${color yellow}${fs_bar 5,100 /media/backup}
${color #0077ff} 2nd Part ${color lightgrey}${fs_used /media/sda3}/${fs_size /media/sda3}${alignr}${color yellow}${fs_bar 5,100 /media/sda3}
${color #0077ff} Firefly ${color lightgrey}${fs_used /media/FIREFLY}/${fs_size /media/FIREFLY}${alignr}${color red}${fs_bar 5,100 /media/FIREFLY}

${color #0077ff}Network: ${color lightgrey}${addr eth0} ${color #0077ff}Network: ${color lightgrey}${addr eth1}

${color #0077ff}Down:${color lightgrey} ${downspeed eth0} k/s ${color lightgrey}${totaldown eth0} $alignr${color #0077ff} Up:${color lightgrey} ${upspeed eth0} k/s $alignr${color lightgrey}${totalup eth0}
${color #0077ff}${downspeedgraph eth0 27,120 000000 00ff00 180} $alignr${color #0077ff}${upspeedgraph eth0 27,120 000000 ff0000 180}
${color #0077ff}Port(s)${alignr}#Connections
${color #0077ff}Inbound: ${color lightgrey}${tcp_portmon 1 32767 count}  ${color #0077ff}Outbound: ${color lightgrey}${tcp_portmon 32768 61000 count}${alignr}${color #0077ff}Total: ${color lightgrey}${tcp_portmon 1 65535 count}

```

---

### Post by mcduck on 2008-01-19
Hardware Monitor applet does exactly what you want, and it runs in the panel. Just install the "hardware-monitor"-package from repositories and add it to your panel (you can actually add as many as you like).

---

### Post by chris200x9 on 2008-01-19
I installed hardware manager but can't find it anywhere on my computer

---

### Post by mister_pink on 2008-01-19
Right click the panel, then add to panel. Under System and hardware is the hardware sensors monitor.

Edit: that made no sense!

---

