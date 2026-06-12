---
title: "Conky dissapears behind wallpaper after every boot"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by whee on 2007-01-09
I installed Conky on Edgy(Ubuntu + Gnome).
I have set the window type to override.
But every time i boot(not log off and on again but really reboot) then Conky is visible only as long the wallpaper hasn't loaded yet.(So when you see the wallpaperless brown background)
This seemed to happen on Dapper aswell as Edgy.
Does anyone know why this happens and/or how to fix this in an elegant way?

---

### Post by energiya on 2007-01-09
I had the same problem with some configs, but some would work... here is mine (taken from [here]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky"))
```

# conky configuration

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
#xftfont Terminus:size=8
xftfont Arial:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar,sticky
#own_window_hints undecorated,below,sticky
background yes
own_window_colour blue
own_window_transparent yes
#own_window_type desktop


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 50 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 2
gap_y 2

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes
#Note: doesn't work in conky 1.2 =(

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none


# Possible variables to be used:
#
#      Variable         Arguments                  Description                

# 	addr              (interface)   IP address for an interface
# 	acpiacadapter                   ACPI ac adapter state.                   
# 	acpifan                         ACPI fan state                           
# 	acpitemp                        ACPI temperature.                        
# 	adt746xcpu                      CPU temperature from therm_adt746x       
# 	adt746xfan                      Fan speed from therm_adt746x             
# 	alignr            (num)         Right-justify text, with space of N
# 	alignc                          Align text to centre
# 	battery           (num)         Remaining capasity in ACPI or APM        
# 					battery. ACPI battery number can be      
# 					given as argument (default is BAT0).     
# 	buffers                         Amount of memory buffered                
# 	cached                          Amount of memory cached                  
# 	color             (color)       Change drawing color to color            
# 	cpu                             CPU usage in percents                    
# 	cpubar            (height)      Bar that shows CPU usage, height is      
# 					bar's height in pixels                 
# 	cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
# 					CPU usage graph, with optional colours in hex,
# 					minus the #.
# 	downspeed         net           Download speed in kilobytes              
# 	downspeedf        net           Download speed in kilobytes with one     
# 					decimal                                  
# 	downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
# 					Download speed graph, colours defined in
# 					hex, minus the #.
# 	exec              shell command Executes a shell command and displays    
# 					the output in conky. warning: this      
# 					takes a lot more resources than other    
# 					variables. I'd recommend coding wanted   
# 					behaviour in C and posting a patch :-).  
# 	execbar           shell command Same as exec, except if the first value
# 					return is a value between 0-100, it
# 					will use that number for a bar.
# 					The size for the bar is currently fixed,
# 					but that may change in the future.
# 	execgraph         shell command Same as execbar, but graphs values
# 	execi             interval, shell command
#  					Same as exec but with specific interval. 
# 					Interval can't be less than              
# 					update_interval in configuration.        
#	font		  font		Specify a different font.  Only applies
#					to one line.
# 	fs_bar            (height), (fs)Bar that shows how much space is used on 
# 					a file system. height is the height in   
# 					pixels. fs is any file on that file      
# 					system.                                  
# 	fs_free           (fs)          Free space on a file system available    
# 					for users.                               
# 	fs_free_perc      (fs)          Free percentage of space on a file       
# 					system available for users.              
# 	fs_size           (fs)          File system size                         
# 	fs_used           (fs)          File system used space                   
# 	hr                (height)      Horizontal line, height is the height in 
# 					pixels                                   
# 	i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
# 					may be omitted if you have only one I2C  
# 					device. type is either in (or vol)       
# 					meaning voltage, fan meaning fan or
# 					temp/tempf (first in C, second in F)
# 					meaning temperature. n is number of the  
# 					sensor. See /sys/bus/i2c/devices/ on     
# 					your local computer.                     
# 	if_running        (process)     if PROCESS is running, display
# 					everything if_running and the matching $endif
# 	if_existing       (file)        if FILE exists, display everything between
# 					if_existing and the matching $endif
# 	if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
# 					if_mounted and the matching $endif
# 	else                            Text to show if any of the above are not true
# 	kernel                          Kernel version                          
# 	linkstatus        (interface)   Get the link status for wireless connections
# 	loadavg           (1), (2), (3) System load average, 1 is for past 1     
# 					minute, 2 for past 5 minutes and 3 for   
# 					past 15 minutes.                         
# 	machine                         Machine, i686 for example                
# 	mails                           Mail count in mail spool. You can use    
# 					program like fetchmail to get mails from 
# 					some server using your favourite         
# 					protocol. See also new_mails.            
# 	mem                             Amount of memory in use                  
# 	membar            (height)      Bar that shows amount of memory in use   
# 	memmax                          Total amount of memory                   
# 	memperc                         Percentage of memory in use
# 	
# 	metar_ob_time
# 	metar_temp
# 	metar_tempf                     Temp in F
# 	metar_windchill
# 	metar_dew_point                 There are a bunch of these
# 	metar_rh                        and they are self-explanatory
# 	metar_windspeed
# 	metar_winddir
# 	metar_swinddir
# 	metar_cloud
# 	metar_u2d_time
# 	
# 	ml_upload_counter               total session upload in mb
# 	ml_download_counter             total session download in mb
# 	ml_nshared_files                number of shared files
# 	ml_shared_counter               total session shared in mb, buggy
# 					in some mldonkey versions
# 	ml_tcp_upload_rate              tcp upload rate in kb/s
# 	ml_tcp_download_rate            tcp download rate in kb/s
# 	ml_udp_upload_rate              udp upload rate in kb/s
# 	ml_udp_download_rate            udp download rate in kb/s
# 	ml_ndownloaded_files            number of completed files
# 	ml_ndownloading_files           number of downloading files
# 	
# 	mpd_artist			Artist in current MPD song
# 					(must be enabled at compile)
# 	mpd_album			Album in current MPD song
# 	mpd_bar           (height)      Bar of mpd's progress
# 	mpd_bitrate                     Bitrate of current song
# 	mpd_status                      Playing, stopped, et cetera.
# 	mpd_title			Title of current MPD song
# 	mpd_vol				MPD's volume
# 	mpd_elapsed                     Song's elapsed time
# 	mpd_length                      Song's length
# 	mpd_percent                     Percent of song's progress
# 	new_mails                       Unread mail count in mail spool.         
# 	nodename                        Hostname                                 
# 	outlinecolor      (color)       Change outline color                     
# 	pre_exec          shell command Executes a shell command one time before 
# 					conky displays anything and puts output 
# 					as text.                                 
# 	processes                       Total processes (sleeping and running)   
# 	running_processes               Running processes (not sleeping),        
# 					requires Linux 2.6                       
# 	shadecolor        (color)       Change shading color                     
# 	stippled_hr       (space),      Stippled (dashed) horizontal line        
# 			(height)        
# 	swapbar           (height)      Bar that shows amount of swap in use     
# 	swap                            Amount of swap in use                    
# 	swapmax                         Total amount of swap                     
# 	swapperc                        Percentage of swap in use                
# 	sysname                         System name, Linux for example           
# 	offset            pixels        Move text over by N pixels
# 	tail              logfile, lines (interval)
# 					Displays last N lines of supplied text
# 					text file.  If interval is not supplied,
# 					Conky assumes 2x Conky's interval.
# 					Max of 30 lines.
# 					Max of 30 lines can be displayed.
# 	time              (format)      Local time, see man strftime to get more 
# 					information about format                 
# 	totaldown         net           Total download, overflows at 4 GB on     
# 					Linux with 32-bit arch and there doesn't 
# 					seem to be a way to know how many times  
# 					it has already done that before conky   
# 					has started.                            
# 	top               type, num     This takes arguments in the form:
# 					top <name> <number>
# 					Basically, processes are ranked from 
# 					highest to lowest in terms of cpu
# 					usage, which is what <num> represents.
# 					The types are: "name", "pid", "cpu", and
# 					"mem".
# 					There can be a max of 10 processes listed.
# 	top_mem           type, num     Same as top, except sorted by mem usage
# 					instead of cpu
# 	totalup           net           Total upload, this one too, may overflow 
# 	updates                         Number of updates (for debugging)        
# 	upspeed           net           Upload speed in kilobytes                
# 	upspeedf          net           Upload speed in kilobytes with one       
# 					decimal                                  
# 	upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
# 					Upload speed graph, colours defined in
# 					hex, minus the #.
# 	uptime                          Uptime                                   
# 	uptime_short                    Uptime in a shorter format               
# 	
# 	seti_prog                       Seti@home current progress
# 	seti_progbar      (height)      Seti@home current progress bar
# 	seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color }$nodename  ${hr}
${color #9fb6cd}${time %a: } $alignr${color }${time %e %B %G}
${color #9fb6cd}${time %Z:    }$alignr${color }${time %H:%M:%S}
${color #9fb6cd}UpTime: $alignr${color }$uptime
${color #9fb6cd}Kernel:$alignr${color }$kernel
${color #9fb6cd}CPU:${color } $alignr$cpu% ${i2c 9191-0290 temp 2} C 
${cpugraph 20,130 000000 ffffff}
${color #9fb6cd}Processes: $alignr${color }$processes
${color #9fb6cd}Running:   $alignr${color }$running_processes

${color #9fb6cd}Highest CPU:
${color #ddaa00} ${top name 1}$alignr${top_mem cpu 1}
${color lightgrey} ${top name 2}$alignr${top cpu 2}
${color lightgrey} ${top name 3}$alignr${top cpu 3}
${color lightgrey} ${top name 4}$alignr${top cpu 4}

${color #9fb6cd}Highest MEM:
${color #ddaa00} ${top_mem name 1}$alignr${top_mem mem 1}
${color lightgrey} ${top_mem name 2}$alignr${top_mem mem 2}
${color lightgrey} ${top_mem name 3}$alignr${top_mem mem 3}
${color lightgrey} ${top_mem name 4}$alignr${top_mem mem 4}

${color #9fb6cd}MEM:  $alignr${color } $memperc% $mem/$memmax
${membar 3,100}
${color #9fb6cd}SWAP: $alignr${color }$swapperc% $swap/$swapmax
${swapbar 3,100}
${color #9fb6cd}ROOT:    $alignr${color }${fs_free /}/${fs_size /}
${fs_bar 3,100 /}
${color #9fb6cd}HOME:  $alignr${color }${fs_free /home}/${fs_size /home}
${fs_bar 3,100 /home}

${color #9fb6cd}NET (${color}${addr eth0}${color #9fb6cd}): 
${color}Up: ${color }$alignr${upspeed eth0} kB/s
${upspeedgraph eth1 20,130 000000 ffffff}
${color}Total: $alignr${totalup eth0}
${color}Down: ${color }$alignr${downspeed eth0}kB/s${color}
${downspeedgraph eth0 20,130 000000 ffffff}
${color}Total: $alignr${totaldown eth0}

```
If that doesn't work, you should read [this page]("http://ubuntuforums.org/showthread.php?t=207792&highlight=conky").

---

### Post by whee on 2007-01-09
Do you happen to know which setting(s) it is in the config file that causes Conky to either stay visible or dissapear?

---

### Post by doobit on 2007-01-09
> **whee said:**
> Do you happen to know which setting(s) it is that causes Conky to either stay visible or dissapear?

I think it's the number of times Conky will update before quitting. Set to 0 to let it run forever.

---

### Post by truthfatal on 2007-01-09
[http://www.ubuntuforums.org/showpost.php?p=1987762&postcount=410](http://www.ubuntuforums.org/showpost.php?p=1987762&postcount=410)
[quote=oyvindaa]
It's not just a conky-related problem though, because this was happening when I was using adesklets as well.
[/quote]

I just installed conky and had the exact same problem.

instead of trying to autostart conky, I followed [raul_](http://www.ubuntuforums.org/member.php?u=79472)'s advice and made a script containing 
```

#!/bin/bash
sleep 20 && conky;

```
and add that to my autostart instead... I don't know if that's considered an "elegant" fix, but it's an invisible one if you make the script a .[dot]file.sh :)

---

