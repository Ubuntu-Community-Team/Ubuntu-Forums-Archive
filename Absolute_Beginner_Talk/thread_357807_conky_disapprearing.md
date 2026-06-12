---
title: "conky disapprearing"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by eilu on 2007-02-10
weird problem with conky- it loads on startup but "disappears" when my wallaper loads over the default maroon one; it's still running though, I can see it on the system monitor (i.e., it looks like the wallpaper is drawn OVER conky)

I set conky to run on startup by adding conky -d to preferences>sessions>startup programs, and here's my conkyrc file:
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
maximum_width 265

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
gap_x 55
gap_y 55
#alignment top_right
alignment bottom_left
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
${color #C9C9C9}$sysname $kernel $machine - $nodename 

${color #C9C9C9}Uptime:${color lightgrey} $uptime ${color #C9C9C9} Load:${color lightgrey} $loadavg

${color #C9C9C9}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
${color #C9C9C9}Usage:${color #C9C9C9} ${color lightgrey}${cpu}% ${color #C9C9C9}${cpubar}
${color #C9C9C9}${cpugraph ffffff 666699}
${color #C9C9C9}Proces:${color lightgrey} $processes  ${color #C9C9C9}Run:${color lightgrey} $running_processes ${color #C9C9C9}CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} ${color #C9C9C9}MB:${color lightgrey} ${i2c temp 1}C

${color #C9C9C9}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #C9C9C9}${membar 5,110}
${color #C9C9C9}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #C9C9C9}${swapbar 5,110}

${color #C9C9C9}HD IO: ${color lightgrey}${diskio} ${alignr}${color #C9C9C9}Temperature: ${color lightgrey}${hddtemp}C
${color #C9C9C9}${diskiograph ffffff 666699}

```

any ideas? :confused: seems very weird!

---

### Post by Atreus12 on 2007-02-10
I had the same problem. I didn't really solve the problem, but I did find a solution.

Go to your home folder, and create a new document. Call it something like '.conky_start.sh' It should contain the following
> 
#!/bin/bash
sleep 6 && conky;


The # after 'sleep' tells the computer how long to wait until starting conky. This way you can wait until after the desktop is drawn, and then put conky on top of it

Then do a chmod on it and add execute privledges
> 
sudo chmod +x .conky_start.sh
 

Finally, go to system -> prefeneces -> sessions
pick the 'statup' tab
remove the conky entry
click add
browse for your '.conky_startup.sh' file

and you should be good to go.

---

### Post by eilu on 2007-02-11
thanks a lot! it worked perfectly! (although I had to tweak the number of cycles- 6 was too much)

---

