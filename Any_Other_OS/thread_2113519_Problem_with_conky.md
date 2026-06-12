---
title: "Problem with conky"
date: 2013-02-07
forum: Any Other OS
---

### Post by Slimmons on 2013-02-07
Hi everybody.  As many have said, I absolutely love this thread.  Here's my .conkyrc file, but I also have a question.  I have tried several different things to get some form of weather on my conky.  I've added scripts and changed configurations and can't seem to get anything to work.  Can anybody give me any good ideas.  I'm using Linux Mint 14 on a Lenovo T410, and I Live in Huntsville Alabama.  Any help would be greatly appreciated.


background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.1
update_interval 2
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color cc0000
default_shade_color red
default_outline_color green
alignment top_right
gap_x 8
gap_y 8
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer no


#################################################################
TEXT
################SYSTEM################
${color 33bb33}System ${hr 2}
${color cc0000}Linux Mint 14 "Nadia" $alignr $machine
Intel CORE i5 $alignr${freq_g cpu0}Ghz
Temperature: $alignr${ibm_temps N = 0} C
Fan Speed: $alignr${ibm_fan} RPM
$alignc${color 33bb33}Processor${color cc0000}
${cpugraph cc0000 33bb33}
${color 33bb33}CPU:1 ${color cc0000}${cpu cpu1}% ${cpubar cpu1}
${color 33bb33}CPU:2 ${color cc0000}${cpu cpu2}% ${cpubar cpu2}
${color 33bb33}CPU:3 ${color cc0000}${cpu cpu3}% ${cpubar cpu3}
${color 33bb33}CPU:4 ${color cc0000}${cpu cpu4}% ${cpubar cpu4}

################HDD/MEM################
${color 33bb33}HDD/Memory${hr 2}
${color 33bb33}MEM ${color cc0000}$alignc $mem / $memmax $alignr $memperc%
$membar
#
${color 33bb33}/home ${color cc0000}$alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

Disk i/o 
${diskiograph cc0000 33bb33} 

###############PROCESSES################
${color 33bb33}Processes ${hr 2}
${color cc0000}$alignr $running_processes Running 
$alignr $processes Sleeping
#
${color 33bb33} $alignc Top Processes
#
${color 33bb33}CPU $alignr CPU% MEM%
${color cc0000}${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 2}${top mem 3}
#
${color 33bb33}MEM $alignr CPU% MEM%
${color cc0000}${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}
${execpi 1800 conkyForecast --refetch --hideunits --template=/media/5/Conky/templates/cF-2013.template}
############NETWORKING##############
${color 33bb33}Networking${hr 2}
${color cc0000}${if_existing /proc/net/route wlan0}
IP on wlan0 $alignr ${addr wlan0}
Down ${downspeed wlan0}kb/s    $alignr Up ${upspeed wlan0}kb/s
${upspeedgraph wlan0 25,100 cc0000 33bb33} ${downspeedgraph wlan0 25,100 cc0000 33bb33}
${else}
${if_existing /proc/net/route eth0}
IP on eth0 $alignr ${addr wlan0}
Down ${downspeed eth0}kb/s    $alignr Up ${upspeed eth0}kb/s
${upspeedgraph eth0 25,100 cc0000 33bb33} ${downspeedgraph eth0 25,100 cc0000 33bb33}
${endif}

---

### Post by Sector11 on 2013-02-07
> **Slimmons said:**
> Hi everybody.  As many have said, I absolutely love this thread.  Here's my .conkyrc file, but I also have a question.  I have tried several different things to get some form of weather on my conky.  I've added scripts and changed configurations and can't seem to get anything to work.  Can anybody give me any good ideas.  I'm using Linux Mint 14 on a Lenovo T410, and I Live in Huntsville Alabama.  Any help would be greatly appreciated.

OK, if I may suggest TeoBigusGeekus's weather scripts.  They come with working examples. and you can get weather from 4 different locations, and from *a nice light version* to the *if it's weather it in this script* version.

Check my signature for a link.  Pick one and try it.  I'll help you here or in Teo's thread on Crunchbang.

**IE:** for weather·com you would need:
```
http://www.weather.com/weather/tenday/Huntsville+AL+USAL0287:1:US
```

[LIST]
[*]go to Weather·com and put in your location,
[*]click on 10 days,
[*]copy the url into the ~/Conky_WeatherCom/**weath_com** file - you'll see the place at the top, and run the conky:
[/LIST]
```
conky -c ~/Conky_WeatherCom/.conkyrc_weather_com
```

**[COLOR="Blue"][SIZE="3"]Huntsville AL:[/SIZE][/COLOR]** · · · [[IMG]http://t.imgbox.com/adq61Eax.jpg[/IMG]](http://imgbox.com/adq61Eax) 

That's the example you can make it look anyway you want or add it to you conky.

**Also your image didn't take - a thousand lines of code in your post though.**

---

### Post by howefield on 2013-02-07
Thread moved to "*Other OS/Distro Talk*" and tagged as Mint.

---

### Post by Sector11 on 2013-02-07
For over 5 years the "Post your .conkyrc files w/ screenshots" has been the place to go for conky information regardless of which distro people use.

Has something changed in the Ubuntu Forums that this no longer is the case?

---

### Post by Slimmons on 2013-02-08
I know right?  Half of these .conkyrc posts aren't with ubuntu, but somehow mine manages to go somewhere else.....And yes, I would say this is probably the number one conky resource.  Just an opinion.

---

### Post by Slimmons on 2013-02-08
Thanks for all of the info.  I just started working on it, and I decided to use the 1d2 Accuweather.
I followed the instructions:

Downloaded 1d2Accuweather
Put the ConkyWeather.ttf file in my ~/.fonts folder, which I had to create
made the script inside executable
but then it says to run the command conky -c /path/.conkyrc_acc_int_cwfont
I'm not sure what to do there, because there is no .conkyrc_acc_int_cwfont, am I missing something?


I also tried the example you showed using weather.com and wasn't able to get that working either.  I get the error 
    rm: cannot remove '/home/myName/Conky_WeatherCom/10days/10days_OK': No such file or directory
 I know that's just saying that b/c the directory doesn't exist, but I didn't want to go making things that the script might want to use later.  
Thanks in advance.  Also, I'm not sure what to add inside my script, or do I have to make this command my new startup command for conky?

---

### Post by Sector11 on 2013-02-08
> **Slimmons said:**
> Thanks for all of the info.  I just started working on it, and I decided to use the 1d2 Accuweather.
I followed the instructions:

Downloaded 1d2Accuweather
Put the ConkyWeather.ttf file in my ~/.fonts folder, which I had to create
made the script inside executable
but then it says to run the command conky -c /path/.conkyrc_acc_int_cwfont
I'm not sure what to do there, because there is no .conkyrc_acc_int_cwfont, am I missing something?


I also tried the example you showed using weather.com and wasn't able to get that working either.  I get the error 
    rm: cannot remove '/home/myName/Conky_WeatherCom/10days/10days_OK': No such file or directory
 I know that's just saying that b/c the directory doesn't exist, but I didn't want to go making things that the script might want to use later.  
Thanks in advance.  Also, I'm not sure what to add inside my script, or do I have to make this command my new startup command for conky?

After putting the font in ~/.font did you run:
```
fc-cache -fv
```

I keep it as an alias in my bash file.
```
alias font='fc-cache -fv'
```

I haven't used that script, I'll test it today though.

=== to continue ===

Does the top of ~/Conky_WeatherCom/**weath_com** look like this:
```
#!/bin/bash

#put your 10 day weather.com address here
address10="http://www.weather.com/weather/tenday/Huntsville+AL+USAL0287:1:US"

addr_now=$(echo $address10|sed 's/tenday/right-now/')
addr_today=$(echo $address10|sed 's/tenday/today/')

kill -STOP $(pidof conky)
killall wget

wget --user-agent="Firefox" -O $HOME/Conky_WeatherCom/RightNow/raw_rn $addr_now
wget --user-agent="Firefox" -O $HOME/Conky_WeatherCom/Today/raw_td $addr_today
wget --user-agent="Firefox" -O $HOME/Conky_WeatherCom/10days/raw_10 $address10

rm $HOME/Conky_WeatherCom/10days/10days_OK

if [[ -s $HOME/Conky_WeatherCom/RightNow/raw_rn ]]; then
	#############
	# Right now #
	#############

```
That line for Huntsville, AL is what you need in there.

Try "executing" the bash script ~/Conky_WeatherCom/**weath_com** from your file manager for the first time.  You should see the images appear in the directory.  Then run the conky.

One other thing, what does $HOME in a terminal produce?  Does it display your /home directory?

```
 sector11 @ sector11
 08 Feb 13 | 08:27:24 ~
         $ $HOME
bash: /home/sector11: Is a directory
 sector11 @ sector11
 08 Feb 13 | 08:27:30 ~
         $ 
```

If not, you will need to search for $HOME/ in **weath_com** and replace it with a direct path: **/home/alain/**

---

### Post by Sector11 on 2013-02-08
> **Slimmons said:**
> I know right?  Half of these .conkyrc posts aren't with ubuntu, but somehow mine manages to go somewhere else.....And yes, I would say this is probably the number one conky resource.  Just an opinion.

Not only that, I don't use Ubuntu or Xubuntu anymore.  I used them both at one time and got my conky start here with them, now I just come to help people with conky.

If my last post doesn't help then I would suggest that you join the [CrunchBang forum]("http://crunchbang.org/forums/") and go directly to thwe source; [TeoBigusGeekus]("http://crunchbang.org/forums/viewtopic.php?id=19235").

BTW, I am also on the Mint forum in the [Conky Showoff Thread]("http://forums.linuxmint.com/viewtopic.php?f=212&t=30209&sid=62343279bf194a0fe603b2be85b6f0ee&start=280#p672734").  ):P <<-- green!

---

