---
title: "[SOLVED] Python with Conky Question"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by RottenBananas on 2008-02-03
Alright...been messing alot with conky...and its amazing. I made my own conkyrc and while learning the commands i saw the exec command. After searching and learning some more I saw tons of scripts people wrote for weather and rss feeds etc.

So i had an idea to write my own script. It would fetch the scores from the last flyers hockey game (love the flyers) and display them in conky. 

At the moment im teaching myself python so thats what i used to accomplish this. 

Now the problem is with conky. If I run my script in console by doing:
```

python conky.py
```

the output will be what i want. No errors or anything. So the script works. but when i call it in conky by doing:
```

${execi 1800 /home/myusername/conky.py}
```

i get the following errors:
/home/myusername/conky.py: 1: import: not found
/home/myusername/conky.py: 3: Syntax error: "(" unexpected

heres my python script...im a linux and python noob so pardon the coding
```

import urllib2
res = urllib2.urlopen("http://flyers.nhl.com")
page = res.read()
first = page.find('page" title="')
last = page.rfind('Recap')
print page[first+13:last-2]
```

is there something i need to do for conky to import the urllib2 from python?

If someone could test the script and see if it works (it works on my end) and try it in conky and tell me what the problem is thatd be great.

Thanks for the help
-Bananas

---

### Post by Faud on 2008-02-03
There is a forum here on Ubuntu titled "How to get a beautiful conky" I would try asking there cause those guys do this like 24-7

---

### Post by RottenBananas on 2008-02-05
someone in that other thread figured out what the problem was

instead of this:
${execi 1800 /home/myusername/conky.py}

you need to put this:
${execi 1800 python /home/myusername/conky.py}

god i love these forums

---

### Post by emarkd on 2008-02-05
Didn't see this the first time, but if you run across this again, remember that python is like bash or any other scripting languages.  If you make

```
#!/usr/bin/env python
```

the first line of the script and then do a chmod +x to make it executable, you can just run it like any other program and you don't have to invoke python directly.

---

### Post by cdtech on 2008-02-06
> **Faud said:**
> There is a forum here on Ubuntu titled "How to get a beautiful conky" I would try asking there cause those guys do this like 24-7

**Hey Faud**, here's the information:
This is my original .conkyrc script.  You'll have to change a few things to show your own personal information.  Just play around with it, you'll get the hang of it.
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
font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8
# xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 3.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

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

# Minimum size of text area
minimum_size 5 5
maximum_width 680

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 3
gap_y 100

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
# Use yes here to get the proper degree symbol
override_utf8_locale yes


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
${color #00ff00}bobkat${color #888888}@${color red}$nodename:
${color #888888}$sysname $kernel ${color #CCCCCC}on ${color #888888}$machine bit
${color #888888}Uptime: $uptime
${color #888888}${time %a,}${time %e %B %G}                     ${color #00ff00}${time %H:%M:%S}
${color cyan}${hr 1}$color

${color #ffccaa}System:
${color #888888}cpu0: ${color #CCCCCC}${freq cpu0} MHz  ${color #888888}cup1: ${color #CCCCCC}${freq cpu1} MHz
${color #888888}load: ${color #CCCCCC}${cpu cpu0}%  ${color #888888}   load: ${color #CCCCCC}${cpu cpu1}%

${color #888888}Last Backup: ${color #CCCCCC}${execi 3600 cat /media/Storage/Linux-Backup/current/lastfullbackupdate}
${color #888888}${cpugraph 25 ff0000 ff00ff}
${color #ffccaa}Temperatures:
${color #888888}Core1 Temp: ${color #CCCCCC}${execi 5 ~/Scripts/temp1conv} °f  ${color #888888}/ ${color #CCCCCC}${execi 5 ~/Scripts/temp2conv} °f 
${color #888888}Core2 Temp: ${color #CCCCCC}${execi 5 ~/Scripts/temp3conv} °f  ${color #888888}/ ${color #CCCCCC}${execi 5 ~/Scripts/temp4conv} °f 
${color cyan}${hr 1}$color

${color #ffccaa}Memory:
${color #888888}ram: ${color #CCCCCC}$mem${color #888888}/${color #CCCCCC}$memmax ${color #888888}, ${color #CCCCCC}$memperc%
${color #888888}swap: ${color #CCCCCC}$swap${color #888888}/${color #CCCCCC}$swapmax ${color #888888}, ${color #CCCCCC}$swapperc%
${color #888888}avg load: (${color #CCCCCC}$loadavg${color #888888})
${color #888888}processes: ${color #CCCCCC}$processes	${color #888888}running: ${color #CCCCCC}$running_processes
${color #ffccaa}Power:
${color #888888}Battery: $color${battery}
${color cyan}${hr 1}$color

${color #ffccaa}Wireless Network:
${color #888888}ip address: ${color #CCCCCC}${addr wlan0}
${color #888888}essid: $color${execi 5 iwconfig wlan0 | sed 's/  /\n/g' | grep ESSID | sed 's/ESSID:"//'| sed 's/"//'}
${color #888888}link status: $color${execi 5 iwconfig wlan0 | sed 's/  /\n/g' | grep Quality | sed 's/Link Quality://' | sed 's/Link Quality=//' | sed 's/ //g' } ${color #888888}signal: $color${execi 5 iwconfig wlan0 | sed 's/  /\n/g' | grep Signal | sed 's/Signal level=//' | sed 's/Signal level://' }

${color #888888}total download: ${color #CCCCCC}${totaldown wlan0}         ${color #888888}total upload: ${color #CCCCCC}${totalup wlan0}	 
${color #888888}download speed: ${color #CCCCCC}${downspeed wlan0} k/s	      ${color #888888}upload speed: ${color #CCCCCC}${upspeed wlan0} k/s
${color #888888}${downspeedgraph wlan0 25,100 ff0000 0000ff}                    ${color #888888}${upspeedgraph wlan0 25,100 0000ff ff0000}
${color cyan}${hr 1}$color

${color #ffccaa}File Systems:
${color #888888}root: ${color #CCCCCC}${fs_used /}${color #888888}/${color #CCCCCC}${fs_size /} ${color #888888}(${color #CCCCCC}${fs_free /}, ${fs_free_perc /}% ${color #888888}free)
       ${fs_bar /}
${color #888888}home: ${color #CCCCCC}${fs_used /home}${color #888888}/${color #CCCCCC}${fs_size /home} ${color #888888}(${color #CCCCCC}${fs_free /home}, ${fs_free_perc /home}% ${color #888888}free)
       ${fs_bar /home}
${color #888888}storage: ${color #CCCCCC}${fs_used /media/Storage}${color #888888}/${color #CCCCCC}${fs_size /media/Storage} ${color #888888}(${color #CCCCCC}${fs_free /media/Storage}, ${fs_free_perc /media/Storage}% ${color #888888}free)
       ${fs_bar /media/Storage}
${color #888888}vista: ${color #CCCCCC}${fs_used /media/sda1}${color #888888}/${color #CCCCCC}${fs_size /media/sda1} ${color #888888}(${color #CCCCCC}${fs_free /media/sda1}, ${fs_free_perc /media/sda1}% ${color #888888}free)
       ${fs_bar /media/sda1}
${color yellow}Logging ${hr 2}$color
${color white}${execi 20 tail -n2 /var/log/messages | fold -w50}
${color yellow}Security ${hr 2}$color
${color white}${execi 20 tail -n2 /var/log/auth.log | fold -w50}
```
[B]And this is my weather script:
Just change the zip code for your area.[/B]
```
background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

#use_xft yes
#xftfont HandelGotD:size=8
#xftalpha 0.5

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
#alignment top_right
#alignment bottom_left
alignment bottom_right
gap_x 600
gap_y 650
# Subtract file system buffers from used memory?
no_buffers yes

# Force UTF8? note that UTF8 support required XFT
# This should be set to yes to get the proper degree symbol
override_utf8_locale yes

#  FOR MY INFO
# last month
# ${font DejaVu Sans Mono :size=8}${execi 60 cal -3 | cut -c00-22}
# this month
# ${execi 60 cal}
# next month
# ${execi 60 cal -3 | cut -c45-64}$font
# this month and next month
# ${font DejaVu Sans Mono :size=8}${execi 60 cal -3 | cut -c23-64}$font

# For international dates & times ${tztime} see: /usr/share/zoneinfo
# Leave 2 blank lines below TEXT to clear panel
# add this line below TEXT to test things, remove when finished.

#${color cyan}Fix me: CPU Temp: ${color white}${acpitemp}C $color
#${color red}Test Cmds Above ${hr 3} $color


TEXT
${alignc}${offset -15}${color orange}${font Sans Mono:size=10}Your City 5 Day Forecast$font$color

${voffset -5}${font weather:size=30}${alignc}${offset -45}${execi 1800 perl ~/.scripts/conky-scripts/weather.pl 15065 f 1p}${offset 25}${color orange}${execi 1800 perl ~/.scripts/conky-scripts/weather.pl 15065 f 2p}${offset 25}${color cyan}${execi 1800 perl ~/.scripts/conky-scripts/weather.pl 15065 f 3p}${offset 24}${color green}${execi 1800 perl ~/.scripts/conky-scripts/weather.pl 15065 f 4p}${offset 23}${color red}${execi 1800 perl ~/.scripts/conky-scripts/weather.pl 15065 f 5p}${font}$color
${alignc}${offset -15}${execi 1800 perl ~/.scripts/conky-scripts/weather.pl 15065 f 1}${offset 10}${execi 1800 perl ~/.scripts/conky-scripts/weather.pl 15065 f 2}${offset 10}${execi 1800 ~/.scripts/conky-scripts/weather.pl 15065 f 3}${offset 10}${execi 1800 ~/.scripts/conky-scripts/weather.pl 15065 f 4}${offset 10}${execi 1800 perl ~/.scripts/conky-scripts/weather.pl 15065 f 5}

${alignc}${color cyan}${offset -10}Current Condition:$color ${voffset -5}${font weather:size=30}${execi 1800 perl ~/.scripts/conky-scripts/weather.pl 15065 f cp}${font}${voffset -18} - ${execi 1800 perl ~/.scripts/conky-scripts/weather.pl 15065 f c}

```

**And I use this script to get both of them to start together:**
```
#!/bin/bash
sleep 25 &&
conky -c ~/Documents/.conkyrc;
sleep 1 &&
conky -c ~/.scripts/weather-call;
```

Hope this helps...
Have fun.....

---

### Post by RottenBananas on 2008-02-06
Hey guys,
So I think i got the basics of python down and finished up my flyers script. I thought I should post it up for any hockey fans. After a quick glance through how the nhl team sites are set up they look like theyre all in a similar format.

So the code will def work for the flyers (unless they change their website format) and might work for any other team...you just have to change the url accordingly. i have tested it for the rangers and it works. 

Keep in mind i know python for a total of two days. My code is probably terrible and theres probably a million more efficient ways to get the same results but this is what worked for me through lots of trial and error :)

Enjoy!

```

#written by Bananas
#change 'http://flyers.nhl.com to http://yourteamsname.nhl.com
#please post if you have any programming suggestions!
#i dont know python and really would like to learn so your tips are appreciated!

import urllib2
temp = urllib2.urlopen('http://flyers.nhl.com')
myFile = temp.read()

first = myFile.find('<div class="gameScoreboard">')
last = myFile.rfind("Recap")
section = myFile[first:last]

date = section.find("datetime alert")
if date == -1:
	date = section.find("datetime")

dateEnd = section.find("</div>")
if dateEnd == -1:
	dateEnd = section.find("&")
inProgress = 0
#game hasnt begun yet
nextGame = section[date+33:dateEnd-13]
if date == 77 and dateEnd == 138:
	nextGame = section[date+33:dateEnd-13]
	inProgress = 0

#game is in progress
#if date == 74 and dateEnd == 120 or date == 74 and dateEnd == 122 or date #== 74 and dateEnd == 121:
if date == 74 and dateEnd < 137:
	nextGame = section[date+21:dateEnd-4] + ' Period'
	inProgress = 1

if inProgress == 0:
	time = section.find('time',dateEnd)
	timeEnd = section.find('</div>',time)
	theTime = section[time+6:timeEnd]

if inProgress == 1:
	theTime = ''

team1 = section.find('teamName">')
team1end = section.find('</div>',team1)
awayTeam = section[team1+10:team1end]

team2 = section.rfind('teamName">')
team2end = section.find('</div>',team2)
homeTeam = section[team2+10:team2end]

awayScore = section.find('total">',team1)
awayScoreEnd = section.find('</div>',team1end+1)
totalAwayScore = section[awayScore+7:awayScoreEnd]

homeScore = section.find('total">',team2)
homeScoreEnd = section.find('</div>',team2end+1)
totalHomeScore = section[homeScore+7:homeScoreEnd]

channel = myFile.find('TV:&nbsp;')
channelEnd = myFile.find(',',channel)
theChannel = myFile[channel+9:channelEnd]

lastGame = section.find('page" title="')
if lastGame == -1:
	lastGame = section.find('<div class="teamName right">')
lastGameEnd = myFile.rfind('>Recap</a>')
if lastGameEnd == -1:
	lastGameEnd = section.find('<div class="teamName left">')

previous = section[lastGame+13:lastGameEnd]

if lastGame == 1722 and lastGameEnd == 1820 or lastGame == 1711 and lastGameEnd == 1809:
	tempholder = section.find('</div>',lastGame)
	firstTeam = section[lastGame+28:tempholder]
	tempholder2 = section.find('</div>',lastGameEnd)
	secondTeam = section[lastGameEnd+27:tempholder2+2] 
	previous = firstTeam + ' @ ' + secondTeam


print 'Last Game:',previous[:-2]
print 'Next Game:',nextGame, theTime, theChannel
print ''
print 'Away Team:',awayTeam, totalAwayScore
print 'Home Team:',homeTeam, totalHomeScore

```

and execute it in conky by doing:
```

${execi 1800 python /home/wherever you put the file}

```
please please please post any suggestions you may have

...i was gonna upload a screen...but the screenshots 4 kbs too big lol o well

Thanks alot guys!

-Bananas

---

### Post by RottenBananas on 2008-02-06
I got a screen compressed, here it is

---

### Post by cdtech on 2008-02-07
Awesome, great work for such a short time.

I want one now for my team....

Thanks

---

### Post by RottenBananas on 2008-02-07
Scratch the script up top...it doesnt work right. Since the layout changes when someone scores it messes up. Flyers played last night so i was messing with it during the game and i think i fixed it.

heres the fixed script

```

#written by Bananas
#change 'http://flyers.nhl.com to http://yourteamsname.nhl.com
#please post if you have any programming suggestions!
#i dont know python and really would like to learn so your tips are appreciated!

import urllib2
temp = urllib2.urlopen('http://flyers.nhl.com')
myFile = temp.read()

first = myFile.find('<div class="gameScoreboard">')
last = myFile.rfind("Recap")
section = myFile[first:last]

date = section.find("datetime alert")
if date == -1:
	date = section.find("datetime")

dateEnd = section.find("</div>")
if dateEnd == -1:
	dateEnd = section.find("&")
inProgress = 0
#game hasnt begun yet
nextGame = section[date+33:dateEnd-13]
if date == 77 and dateEnd == 138:
	nextGame = section[date+33:dateEnd-13]
	inProgress = 0

#game is in progress
#if date == 74 and dateEnd == 120 or date == 74 and dateEnd == 122 or date #== 74 and dateEnd == 121:
if date == 74 and dateEnd < 137:
	nextGame = section[date+21:dateEnd-4] + ' Period'
	inProgress = 1

if inProgress == 0:
	time = section.find('time',dateEnd)
	timeEnd = section.find('</div>',time)
	theTime = section[time+6:timeEnd]

if inProgress == 1:
	theTime = ''

team1 = section.find('teamName">')
team1end = section.find('</div>',team1)
awayTeam = section[team1+10:team1end]

team2 = section.rfind('teamName">')
team2end = section.find('</div>',team2)
homeTeam = section[team2+10:team2end]

awayScore = section.find('total">',team1)
awayScoreEnd = section.find('</div>',team1end+1)
totalAwayScore = section[awayScore+7:awayScoreEnd]

homeScore = section.find('total">',team2)
homeScoreEnd = section.find('</div>',team2end+1)
totalHomeScore = section[homeScore+7:homeScoreEnd]

channel = myFile.find('TV:&nbsp;')
channelEnd = myFile.find(',',channel)
theChannel = myFile[channel+9:channelEnd]

lastGame = section.find('page" title="')
if lastGame == -1:
	lastGame = section.find('<div class="teamName right">')
lastGameEnd = myFile.rfind('>Recap</a>')
if lastGameEnd == -1:
	lastGameEnd = section.find('<div class="teamName left">')

previous = section[lastGame+13:lastGameEnd]

if lastGame == 1722 and lastGameEnd == 1820 or lastGame == 1711 and lastGameEnd == 1809:
	tempholder = section.find('</div>',lastGame)
	firstTeam = section[lastGame+28:tempholder]
	tempholder2 = section.find('</div>',lastGameEnd)
	secondTeam = section[lastGameEnd+27:tempholder2+2] 
	previous = firstTeam + ' @ ' + secondTeam


print 'Last Game:',previous[:-2]
print 'Next Game:',nextGame, theTime, theChannel
print ''
print 'Away Team:',awayTeam, totalAwayScore
print 'Home Team:',homeTeam, totalHomeScore
```

cdtech whos ur favorite team? just switch [http://flyers.nhl.com](http://flyers.nhl.com) to ur teams url ([http://yourteam.nhl.com](http://yourteam.nhl.com)) and ur good to go!

Lemme know if it messes up again, Hope the NHL never changes their site layout..lol

-Bananas

---

### Post by cdtech on 2008-02-09
errr... uhhh....Penguins.  I'll give it a shot, looks good.

Thanks

---

### Post by RottenBananas on 2008-02-10
another problem...it changed again...so i fixed it again...but i think im gonna give up if they change it again lol

heres the fixed script


```
#written by Bananas
#change 'http://flyers.nhl.com/index.html to http://yourteamsname.nhl.com/index.html
#please post if you have any programming suggestions!
#i dont know python and really would like to learn so your tips are appreciated!

import urllib2
temp = urllib2.urlopen('http://flyers.nhl.com/index.html')
myFile = temp.read()

first = myFile.find('<div class="gameScoreboard">')
last = myFile.rfind("Recap")
section = myFile[first:last]

date = section.find("datetime alert")
if date == -1:
	date = section.find("datetime")

dateEnd = section.find("</div>")
if dateEnd == -1:
	dateEnd = section.find("&")
inProgress = 0
#game hasnt begun yet
nextGame = section[date+33:dateEnd-13]
if date == 77 and dateEnd == 138:
	nextGame = section[date+33:dateEnd-13]
	inProgress = 0

#game is in progress
#if date == 74 and dateEnd == 120 or date == 74 and dateEnd == 122 or date #== 74 and dateEnd == 121:
if date == 74 and dateEnd < 137:
	nextGame = section[date+21:dateEnd-4] + ' Period'
	inProgress = 1

if inProgress == 0:
	time = section.find('time',dateEnd)
	timeEnd = section.find('</div>',time)
	theTime = section[time+6:timeEnd]

if inProgress == 1:
	theTime = ''

team1 = section.find('teamName">')
team1end = section.find('</div>',team1)
awayTeam = section[team1+10:team1end]

team2 = section.rfind('teamName">')
team2end = section.find('</div>',team2)
homeTeam = section[team2+10:team2end]

awayScore = section.find('total">',team1)
awayScoreEnd = section.find('</div>',team1end+1)
totalAwayScore = section[awayScore+7:awayScoreEnd]

homeScore = section.find('total">',team2)
homeScoreEnd = section.find('</div>',team2end+1)
totalHomeScore = section[homeScore+7:homeScoreEnd]

channel = myFile.find('TV:&nbsp;')
channelEnd = myFile.find(',',channel)
theChannel = myFile[channel+9:channelEnd]

lastGame = section.find('page" title="')
if lastGame == -1:
	lastGame = section.find('<div class="teamName right">')
lastGameEnd = myFile.rfind('>Recap</a>')
if lastGameEnd == -1:
	lastGameEnd = section.find('<div class="teamName left">')

previous = section[lastGame+13:lastGameEnd]

if lastGame == 1722 and lastGameEnd == 1820 or lastGame == 1711 and lastGameEnd == 1809 or lastGame == 1709 and lastGameEnd == 1807:
	tempholder = section.find('</div>',lastGame)
	firstTeam = section[lastGame+28:tempholder]
	tempholder2 = section.find('</div>',lastGameEnd)
	secondTeam = section[lastGameEnd+27:tempholder2+2] 
	previous = firstTeam + ' @ ' + secondTeam

print 'Last Game:',previous[:-2]
print 'Next Game:',nextGame, theTime, theChannel
print ''
print 'Away Team:',awayTeam, totalAwayScore
print 'Home Team:',homeTeam, totalHomeScore
```

hope thats the final version...lemme know if theres anymore fixes needed

---

