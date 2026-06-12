---
title: "upgrade newbie help"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Nessa on 2008-01-27
How do I upgrade using the cd?

---

### Post by eolson on 2008-01-27
Hmmmmmmm.   Exacatly what do you mean?

---

### Post by seventhc on 2008-01-27
What version are you using now?
the upgrade can only be done from one version below. You could do that like you do an update, if the upgrade is available then the option will be presented to you in the upper right corner. So you wouldn't even need the CD. Maybe I am misunderstanding what you are asking, but you weren't very specific.

---

### Post by Nessa on 2008-01-27
I have Feisty. From what I understand, using the update manager, it take a long time to download everything. Is that right? I do have the Gutsy CD. My i-net connection isn't that fast even though it's broadband.

---

### Post by emarkd on 2008-01-27
I don't think you can update from the normal CD.  You'd need the alternate installation CD to do that.  Upgrading through the update manager would probably be faster that downloading a new CD image from Ubuntu.

---

### Post by seventhc on 2008-01-27
well it is the correct version for an upgrade then, Ive never done it using the cd though. the only thing I can think of is if you disable all of your repos and leave only your cd available. But still wait for someone else to give you more advice on this as I have never done it that way myself. The upgrade online doesn't take that long really. If it's slow, just start it before you go to sleep. ;)

---

### Post by Nessa on 2008-01-27
Ok. Will do that then. Thanks. (",)

---

### Post by Nessa on 2008-01-28
It's giving me errors. Some of the files can't be found.

---

### Post by cubeist on 2008-01-28
Try a different server if you are getting errors...

---

### Post by Nessa on 2008-01-28
```
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 302 Found
```

I get this on several servers... Help please...

---

### Post by cubeist on 2008-01-28
Try a different server.  Go to system/admin/software source and where it says "Download From:" Just choose a different server... try the main serve, it usually works well.

---

### Post by Nessa on 2008-01-28
I commented the 3rd party sources and got through the upgrade. I have gutsy now. :) I can't open my CCSM or run Conky. No error messages. They just don't come up. Any ideas?

---

### Post by seventhc on 2008-01-29
If you check in 'sessions' is conky in your start up?
'System>Preferences>Sessions'
To make sure you still have conky installed, open a terminal and put
```
conky
```I'm not familiar with ccsm so I can't help much on that.

---

### Post by Nessa on 2008-01-29
```
Conky: can't open '/sys/bus/i2c/devices/9191-0290/temp1_input': No such file or directory
please check your device or remove this var from Conky
```

That's what I get from the terminal...

---

### Post by seventhc on 2008-01-29
hmmm...what about this
```
gedit ~/.conkyrc
```

---

### Post by Nessa on 2008-01-29
```
background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
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

Uptime $alignr $uptime
Load $alignr $loadavg
Temp $alignr ${i2c 9191-0290 temp 1}C ${i2c 9191-0290 temp 2}C

Hostname $alignr $nodename
eth0 $alignr ${addr eth0}

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/root $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}

/disk $alignc ${fs_used /media/disk} / ${fs_size /media/disk} $alignr ${fs_free_perc /media/disk}%
${fs_bar /media/disk}

swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}

$processes processes ($running_processes running)

${color white}Highest CPU:
${color de0b0b}${top name 1}${top_mem cpu 1}
${color white}${top name 2}${top cpu 2}
${top name 3}${top cpu 3}
${top name 4}${top cpu 4}
${top name 5}${top cpu 5}

${color white}Highest MEM:
${color de0b0b}${top_mem name 1}${top_mem mem 1}
${color white}${top_mem name 2}${top_mem mem 2}
${top_mem name 3}${top_mem mem 3}
${top_mem name 4}${top_mem mem 4}
${top_mem name 5}${top_mem mem 5}

${color}Networking:
Down:${color} $alignr ${downspeed eth0} k/s${color} ${offset 80}
$alignc ${downspeedgraph eth0 32,150 de0b0b de0b0b}
Up:${color} $alignr ${upspeed eth0} k/s ${offset 80}
$alignc ${upspeedgraph eth0 32,150 de0b0b de0b0b}
```

:(

---

### Post by seventhc on 2008-01-29
ok, thats good, you still have your settings for conky :)
I would just reinstall conky
open terminal
```
 sudo apt-get install conky
```Did you check to see if you still have conky in your start up programs as posted above?

I email my conkyrc to myself so I always have a back up, I suggest this to you :D
To much work goes into getting a good conkyrc to lose it.
I know you didn't lose it, but if it's online in your email you can always retrieve it if something bad happens. ;)

---

### Post by Nessa on 2008-01-29
Yeah, it is. How do I uninstall it?

---

### Post by seventhc on 2008-01-29
oh wait, I think that error you got is from trying to read your temperature. you still have conky
if you open your conkyrc and comment out this line
Temp $alignr ${i2c 9191-0290 temp 1}C ${i2c 9191-0290 temp 2}C

then your conky will probably start...just for now comment it out

#Temp $alignr ${i2c 9191-0290 temp 1}C ${i2c 9191-0290 temp 2}C
then run conky again after you save the change.

---

### Post by Nessa on 2008-01-29
I have it again thanks! Are there any changes on how the temp is read on feisty and gutsy? I kinda need that temp gauge.

---

### Post by seventhc on 2008-01-29
I'm really not to sure what the changes would have been, and I don't have my conky set up for temp. My comp doesn't support it.:( I wish it did, but I tried everything possible, it just won't work on some computers. :(
So I'm not even sure what you will need to do to get it back, but I am sure someone here will be able to get it going for you. :)

---

### Post by Paqman on 2008-01-29
It's always a good idea to disable any extra repos before trying an upgrade.

Btw, if you've got the CD for the next version it's always an option to do a reinstall instead of an upgrade. This is where having /home on a separate partition comes into its own. When you reinstall only format the / partition, then make sure you set the users up the same as before. You can even [reinstall all your applications automatically](http://ubuntuforums.org/showthread.php?t=261366). Reinstalls with Linux can be really quick and painless compared to other OSes.

---

### Post by Nessa on 2008-01-29
Thanks. The upgrade went fine. Looks like I have to spend more time to smooth out compatibility hiccups.

---

