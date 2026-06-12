---
title: "SummerRebirth &amp; GrayRevenge [Official Thread]"
date: 2011-01-27
forum: Art &amp; Design
---

### Post by alecive on 2011-01-27
Hi!

This is the official thread talking about my two last themes, i.e. [SummerRebirth]("http://alecive.deviantart.com/art/SummerRebirth-Oct-2010-1-3-183624661") and [GrayRevenge]("http://alecive.deviantart.com/art/GrayRevenge-Jan-2011-1-0-194633730") . They're quite similar in the structure, so the installation guide could be the same. Within this evening, I'll translate my guide from italian to english, and I'll post it here.

For now, I wanted just to open the thread, and get users the possibility to ask questions related to my themes here!

---

### Post by madnorthnorthwest on 2011-01-27
So, after having edited the bottom file and the notify files to adjust the conkys which were offset,  the offset returns once I relaunch the conkys. Also, I noticed today that after restarting the computer, two of the three launchers are gone. You can see what it looks like in the attached picture.

Actually, I think my problems are quite similar to those discussed by Michael Scogfield on here: [http://forum.ubuntu-it.org/index.php?PHPSESSID=n2np4mp2k3fbcgp31ff64h5iq2&topic=428999.0](http://forum.ubuntu-it.org/index.php?PHPSESSID=n2np4mp2k3fbcgp31ff64h5iq2&topic=428999.0)

However, I'm not sure I understand everything correctly, using Google translate.

---

### Post by alecive on 2011-01-27
Where you located the "Conky" folder? I need the absolute path, so I can send you the proper commands to do to let me understand better!

---

### Post by madnorthnorthwest on 2011-01-27
> **alecive said:**
> Where you located the "Conky" folder? I need the absolute path, so I can send you the proper commands to do to let me understand better!

In my home folder. Home/isi/Conky

---

### Post by alecive on 2011-01-28
Ok, so post the result of these commands:

```
cat /home/isi/Conky/Notify/notifywet
``````
cat /home/isi/Conky/Notify/notifymem
``````
cat /home/isi/Conky/Notify/notifycal
``````
cd /home/isi/Conky/Notify/
./checkwet
``````
cd /home/isi/Conky/Notify/
./checkcal
``````
cd /home/isi/Conky/Notify/
./checkmem
```So I can know exactly what runs and what is wrong (and maybe why)!

PS: one thing I can suggest now: the conky that displays calendar needs a file called "Note.txt" and located wherever you want.. To get a template of it, just go there -> [http://alecive.deviantart.com/art/Conky-Calendar-Python-Script-157844577](http://alecive.deviantart.com/art/Conky-Calendar-Python-Script-157844577)
Download the pack, extract it wherever you want, and copy the file called "Note.txt" in your preferred directory (I choosed my "Documents" folder). Then, open the file named "note.py" (in the Conky/Notify folder) and in the line #27 (i.e. this -> *inp = open('/home/alecive/Documenti/Note.txt','r') *) modify the path with the correct path to your "Note.txt" file!

---

### Post by madnorthnorthwest on 2011-01-28
ok, here we go.

**notifywet**
```
use_xft yes
xftfont Eurostile:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager

minimum_size 250 300
maximum_width 200

default_color 1a1a1a
draw_shades no

color0 bfbfbf
color1 97bebd
color2 919FB8

alignment br
gap_x 90
gap_y -82

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes
imlib_cache_size 0
short_units yes


TEXT
${image ~/Conky/Notify/notifywet.png -s 214x185 -p -1,5}
${voffset 4}${goto 70}FORECASTS:
${execpi 1 conkyForecast --location=GMXX1870 -w --template=~/Conky/Notify/notifywet.template}

```**notifymem**
```
use_xft yes
xftfont Eurostile:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager

minimum_size 250 600
maximum_width 200

default_color 1a1a1a
draw_shades no

color0 bfbfbf
color1 97bebd
color2 919FB8

alignment lr
gap_x 400
gap_y -170

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes
imlib_cache_size 0
short_units yes

TEXT
${image ~//Conky/Notify/notifymem.png -p -1,5}
${voffset 10}${alignc}${color0}CPU: ${cpu cpu0}%${color}
${voffset 5}${goto 9}${cpugraph cpu0 17,187}${offset -187}${color0}${cpugraph cpu5 17,187}${color}
${voffset 5}${goto 9}CPU1${color0}${goto 77}${cpu cpu1}%${color}
${voffset 32}${goto 85}${color0}Top CPU${color}
${voffset 5}${goto 9}${top name 1}  ${color0}${alignr 8}${top cpu 1}${color}
${voffset 3}${goto 9}${top name 2}  ${color0}${alignr 8}${top cpu 2}${color}
${voffset 3}${goto 9}${top name 3}  ${color0}${alignr 8}${top cpu 3}${color}
${voffset 3}${goto 9}${top name 4}  ${color0}${alignr 8}${top cpu 4}${color}
${voffset 3}${goto 9}${top name 5}  ${color0}${alignr 8}${top cpu 5}${color}
${voffset 32}${goto 85}${color0}Top RAM${color}
${voffset 5}${goto 9}${top_mem name 1}  ${color0}${alignr 8}${top_mem mem 1}${color}
${voffset 3}${goto 9}${top_mem name 2}  ${color0}${alignr 8}${top_mem mem 2}${color}
${voffset 3}${goto 9}${top_mem name 3}  ${color0}${alignr 8}${top_mem mem 3}${color}
${voffset 3}${goto 9}${top_mem name 4}  ${color0}${alignr 8}${top_mem mem 4}${color}
${voffset 3}${goto 9}${top_mem name 5}  ${color0}${alignr 8}${top_mem mem 5}${color}

```**notifycal**
```
use_xft yes
xftfont Eurostile:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager

minimum_size 250 600
maximum_width 200

default_color 1a1a1a
draw_shades no

color0 bfbfbf
color1 97bebd
color2 919FB8

alignment br
gap_x 400
gap_y -87

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes
imlib_cache_size 0
short_units yes

TEXT

${voffset 3}${goto 101}NOTES:${color}${voffset -3}

${execpi 1 $HOME/Conky/Notify/conkycal.sh -l it -v|sed 's/^/\${goto 10}/'}${color0}
${voffset -403}${font Segoe UI:style=Italic:size=8}${execpi 1 python ~/Conky/Notify/note.py}${font}${voffset -300}

```**./checkwet**
```
Conky: desktop window (22000a6) is subwindow of root window (ac)
Conky: window type - override
Conky: drawing to created window (0x5000001)
Conky: drawing to double buffer
```**./checkcal**
```

Conky: desktop window (22000a6) is subwindow of root window (ac)
Conky: window type - override
Conky: drawing to created window (0x5200001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/isi/Conky/Notify/note.py", line 24, in <module>
    inp = open('/home/isi/Conky/Notify/Note.txt','r')
IOError: [Errno 2] No such file or directory: '/home/isi/Conky/Notify/Note.txt'
Traceback (most recent call last):

```**./checkmem**
```
Conky: /home/isi/Conky/Notify/notifymem: 24: config file error
Conky: desktop window (22000a6) is subwindow of root window (ac)
Conky: window type - override
Conky: drawing to created window (0x5400001)
Conky: drawing to double buffer

```resulting in what you can see in the attached picture.

I had downloaded th note.txt but didn't really understand what to do with it. I'll work on that.

---

### Post by alecive on 2011-01-28
Ok.

As you can see (if you can't see I tell you now [but if you went so far with customizing the theme it means that you're very good with computer, so I don't know if you need this!!]), the first and third conkys work quite fine, but the middle has one problem, specifically this:
```
Traceback (most recent call last):
  File "/home/isi/Conky/Notify/note.py", line 24, in <module>
    inp = open('/home/isi/Conky/Notify/Note.txt','r')
IOError: [Errno 2] No such file or directory: '/home/isi/Conky/Notify/Note.txt'
```

This means that the script called "note.py" doesn't find the file Note.txt, because it's not in the correct location. To get the middle conky running, just move that file to the Conky/Notify/ folder, and it will work! When it works, I can explain you in details what is its purpose.. ;)

Another thing you have to do, is move the lower part of the images related to clickable conkys to match the upper. To do this, you have to edit the "bottom" file. At line #38 there is something like this:
```
${image ~/Artwork/GrayRevenge/Conky/Notify/notifywet2.png -p 1062,-173}${image ~/Artwork/GrayRevenge/Conky/Notify/notifymem2.png -p 390,-379}${image ~/Artwork/GrayRevenge/Conky/Notify/notifycal2.png -p 751,-470}
```
In this part, the bottom file calls the ${image} tag to draw an image on the desktop, specifying its position with the "-p" parameter. And those three images are exactly the bottom part of the images related to clickable conkys! To move them, you have only to modify the numbers that came after the "-p" parameter. In your case, surely you have to move the image related to the weather to the left.. so just try to decrease the 1062 number in the first ${image} tag.

---

### Post by madnorthnorthwest on 2011-01-28
yup, I got the "Note.txt" and changed the path in the "note.py". That error is gone. And I edited the "bottom" file already. 1062 is already the original number decreased. Here's what that part from the "bottom" file looks like when all the conkys show up correctly:

```
TEXT
${image ~/Conky/Notify/notifywet2.png -p 1062,-162}${image ~/Conky/Notify/notifymem2.png -p 394,-374}${image ~/Conky/Notify/notifycal2.png -p 660,-457}${voffset -8}${alignc 42}${font Eurostile:size=28}${color}${time %H}:${time %M}${color}
```and here's a screenshot:

[IMG]http://img96.imageshack.us/img96/5564/bildschirmfoto1l.png

Note that the clock in the middle is somehow concealed by something. 
And unfortunately, if I close the conkys and relaunch them (using the launchers) the changes are gone and it looks like this again:

[IMG]http://img696.imageshack.us/img696/299/bildschirmfoto2zc.png

The weird thing is, the "bottom" file still looks the same and if I open it and just press "save" the offset is gone again and everything looks fine. So why won'tthe computer remember the changes made to the "bottom" file when I relaunch the conkys?
A second problem is that two of the three launchers I created (namely the checkcal and the checkwet ones) vanish if I reboot my computer. Only the checkmem launcher stays is the panel.
And a third problem is that the little bar in the upper right corner (is it a battery conky?) always stays in the foeground, see screenshot:

[IMG]http://img832.imageshack.us/img832/4333/bildschirmfoto3l.png

---

### Post by alecive on 2011-01-28
for the top conky (yes it's the battery, but we have to fix it for your case I think), just open the conkystart.sh file with gedit and increase the first sleep (for example to 20, it depends on how much time your computer needs on startup).

The bad effect with bottom conky is due to the fact that if one conky is open, the next conky that you will open will go below the first (if they use the same part of the screen). In my plans, this might not happen, cause those three clickable conkys might be usually closed, and you may open them only when you need them! But, as far as my english understanding let me know, I understood that you want that those three conkys were always open right?

For the second problem, could you please explain me in a detailed way how you created the launchers?

---

### Post by madnorthnorthwest on 2011-01-28
first of all, thanks so much fo your patience. :o) I appreciate that

The battery is now in the background, it worked. thanks.

No, I also just want to open a conky if I need it. For some reason all launchers appeared in the panel when I started the pc this time. I can close and open mem and cal now and the changes to the botom and notify files work. Only the weather conky doesn't. It's bottom keeps mving to the right if I close and reopen that conky.

I created the launchers by right clicking on the desktop and choosing "create launcher", the way it was described in your README. I then moved them to the panel, though the ones on the desktop remained. So I deleted them from the desktop but kept them in the panel.

---

### Post by alecive on 2011-01-29
Mmmm.. it's probably a gnome-panel problem (not strictly related to the launcher itself). Try to right click on the launcher (and also other launchers) and select "Block on the panel" (or something similar, I don't know exactly because I have an italian version).

Talking about other things, you solved all problems? Can you please take a screenshot?

---

### Post by madnorthnorthwest on 2011-01-30
so. The sticking the launchers to the panel thing didn't work. But I found out that if I don't delete the launchers on the desktop, the ones in the panel will stay. However, I don't want them on the desktop and the mem launcher stays even though its launcher on the desktop is long gone. How did you move your launchers from the desktop to the panel?

As for the conkys, the mem and cal conkys look fine. Their positions are correct and they stay there even when I relaunch them. Only the weather conky's bottom keeps getting out of place and shows up too far to the right whenever I relaunch that conky.

---

### Post by alecive on 2011-01-30
I don't remember exactly what I did, but in my opinion I did the same I wrote in the tutorial! However, have you tried by right-clicking on the panel and selecting "Add a launcher to panel" (or something similar) directly?


For weather popup: tray to increase the value related to "x_gap" (or something similar) in notifywet file.. ;)

---

### Post by madnorthnorthwest on 2011-01-31
not working. Tells me I have no permissions to launch the process if I add the launchers to the panel directly.

The notifywet is modified. The problem remains.

I guess I'll just give up on the conkys

---

### Post by alecive on 2011-01-31
Could you post a screenshot of the window that appears that says that you have no permission? 

And another in wich I can see the problem with notifywet?

---

### Post by madnorthnorthwest on 2011-01-31
well, I had deleted the launchers and just created new ones and now the situation is different once again. Seems more likely to be resolved though :-)

So, I added launchers to the panel directly. Clicking the checkmem launcher opens the conky but also a  terminal window with the following error message

```

Conky: /home/isi/Conky/Notify/notifymem: 24: config file error
Conky: desktop window (22000a6) is subwindow of root window (ac)
Conky: window type - override
Conky: drawing to created window (0x4a00001)
Conky: drawing to double buffer

```sounds like there's something wrong with my notifymem now.

Calendar conky launches just fine. 
Weather conky launches with the screwed up position. I'll attach a screenshot.

---

### Post by alecive on 2011-02-01
Ok. So let me to give a look to these files. Post the result of:

```
cat /home/isi/Conky/Notify/notifymem
```

```
cat /home/isi/Conky/bottom
```

In bottom file, have you modified this line: "${image ~/home/isi/Conky/Notify/notifywet2.png -p 1062,-173}" (decreasing the 1062)?

Now another problem is related to the fact that the launcher automatically open a new terminal window. But in my opinion (unfortunately I can't check directly until this evening) if you right-click on the launcher, and select "Properties", there might be a checkbox to deselect that tells you something like "Run in a terminal". I'm right?

---

### Post by madnorthnorthwest on 2011-02-01
**notifymem**

```
use_xft yes
xftfont Eurostile:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager

minimum_size 250 600
maximum_width 200

default_color 1a1a1a
draw_shades no

color0 bfbfbf
color1 97bebd
color2 919FB8

alignment lr
gap_x 400
gap_y -170

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes
imlib_cache_size 0
short_units yes

TEXT
${image ~//Conky/Notify/notifymem.png -p -1,5}
${voffset 10}${alignc}${color0}CPU: ${cpu cpu0}%${color}
${voffset 5}${goto 9}${cpugraph cpu0 17,187}${offset -187}${color0}${cpugraph cpu5 17,187}${color}
${voffset 5}${goto 9}CPU1${color0}${goto 77}${cpu cpu1}%${color}
${voffset 32}${goto 85}${color0}Top CPU${color}
${voffset 5}${goto 9}${top name 1}  ${color0}${alignr 8}${top cpu 1}${color}
${voffset 3}${goto 9}${top name 2}  ${color0}${alignr 8}${top cpu 2}${color}
${voffset 3}${goto 9}${top name 3}  ${color0}${alignr 8}${top cpu 3}${color}
${voffset 3}${goto 9}${top name 4}  ${color0}${alignr 8}${top cpu 4}${color}
${voffset 3}${goto 9}${top name 5}  ${color0}${alignr 8}${top cpu 5}${color}
${voffset 32}${goto 85}${color0}Top RAM${color}
${voffset 5}${goto 9}${top_mem name 1}  ${color0}${alignr 8}${top_mem mem 1}${color}
${voffset 3}${goto 9}${top_mem name 2}  ${color0}${alignr 8}${top_mem mem 2}${color}
${voffset 3}${goto 9}${top_mem name 3}  ${color0}${alignr 8}${top_mem mem 3}${color}
${voffset 3}${goto 9}${top_mem name 4}  ${color0}${alignr 8}${top_mem mem 4}${color}
${voffset 3}${goto 9}${top_mem name 5}  ${color0}${alignr 8}${top_mem mem 5}${color}

```

**bottom**
```
use_xft yes
xftfont Eurostile:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 1024

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 1280 0
maximum_width 1280

default_color 1a1a1a
draw_shades no

color0 bfbfbf
color1 97bebd
color2 919FB8

alignment bl
gap_x 0
gap_y -12

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes
imlib_cache_size 0
short_units yes

TEXT
${image ~/Conky/Notify/notifywet2.png -p 1070,-162}${image ~/Conky/Notify/notifymem2.png -p 394,-374}${image ~/Conky/Notify/notifycal2.png -p 670,-457}${voffset -8}${alignc 42}${font Eurostile:size=28}${color}${time %H}:${time %M}${color}
${alignc -80}${voffset -29}${font Segoe UI:size=10}${time %d %B %y}
${voffset -42} T-Online: ${color}${execi 1000 conkyEmail --servertype=IMAP --servername=secureimap.t-online.de --username=***@t-online.de --password=*** --ssl}${color} GMX:  ${color}${execi 1000 conkyEmail --servertype=POP --servername=pop.gmx.net --username=***@gmx.de --password=*** --ssl}${color} ${alignr 5}${execpi 1000 conkyForecast --location=GMXX1870 --template=~/Conky/Notify/bottom.template}${voffset 6} Cpu: ${color}${cpu cpu0} %${color} ${goto 100}RAM: ${color}${memperc} %${color} ${alignr 100}Down: ${color}${if_up wlan0}${downspeed wlan0}${else}${downspeed eth0}${endif}${color}
${voffset -18}${alignr 5} Up: ${color}${if_up wlan0}${upspeed wlan0}${else}${upspeed eth0}${endif}${color}

```

Yes, I modified that line in the bottom file several times. And it does change the conky's position. But after relaunching the conky, the changes are gone EVEN THOUGH that line in the bottom file stays modified. Should I record a video for you?

As for the launcher, you're right. The "run in terminal" option is selected. If I select the other option it's working. 

So I think all problems except for the weather conky offset are now solved.

---

### Post by alecive on 2011-02-06
Hi, sorry for the late reply but I was very very busy in this meanwhile.

What do you mean exactly with: "But after relaunching the conky".

I explain better: what do you mean with relaunching the conky? How do you relaunch it?

Another problem I can see is the top-right bar. It should manage the battery charge. Does it this or we need to fix it?

---

### Post by madnorthnorthwest on 2011-02-06
with relaunching the conky I mean that if I click the launcher in the panel, the weather conky opens and it's offset. So I go and edit the bottom file until the conky's position is correct. That's this line

```
${image ~/Conky/Notify/notifywet2.png -p 1070,-162}
```

I save the bottom file, click the launcher in the panel again, the conky closes. I then click the launcher again to open it and it's offset again. I go look at the bottom file and nothing has changed, it's still

```
${image ~/Conky/Notify/notifywet2.png -p 1070,-162}
```

I can then just click "save" without having to edit the bottom file (since the values are already correct) and the weather conky moves to the correct position. But it happens again once I close the conky and reopen it.

As for the battery bar, it's always blank, that is it always says the battery is empty.

---

### Post by Action_Radar on 2011-02-06
hi! 

i'm the guy who talked to you about the 1920x1200 background in the deviantarts comments. ;)

maybe you can help me with the repositioning of the conkys. in my screenshot you can see that the text in the bottom conky is way off the desired position. how could i change this?

---

### Post by alecive on 2011-02-07
@madnorthnorthwest: it's really really strange and I can't find the reason.. I have a question: when you shutoff the computer and re-start it, the value inside that ${image} command remains the value that you set up before, or returns the old value?


@action_radar: take a look to the posts inside this thread, they will be really helpful because also madnorthnorthwest had your problems! When you finish, send me a screenshot, so we can finish fixing remaining issues! ;)

---

### Post by militarist on 2011-02-07
hey [alecive]("http://newyork.ubuntuforums.org/member.php?u=997679") 
i read all the posts but my problem is diffrent from [madnorthnorthwest]("http://newyork.ubuntuforums.org/member.php?u=1232400")'s problem,
he can use the launchers but i see an error message when i click on them, so here is my problem:
i can configure all of the applications, but i have problem with conky,
as you see in attached picture, ram and cpu indicators are not in their right place and clock is abit lower than its place.
and the other problem is about those checkcal, chackmem and checkwet launchers, the error is visible in screenshot.
my resolution is 1366*768, and i placed conky in /home/till/Conky

also i looked inside checkcal script and i find something like:
"/home/alecive/Artwork/GrayRevenge/Conky/Notify/oncal"
should i chang i too or not?

[ATTACH]182914[/ATTACH]

---

### Post by alecive on 2011-02-07
Have you read the english tutorial inside the README file?

Because you have to change ALL those paths to paths according to the place in wich you set the "Conky" folder!

So, for example, you have to change this:

"/home/alecive/Artwork/GrayRevenge/Conky/Notify/oncal"

in this:

"/home/till/Conky/Notify/oncal"

---

### Post by militarist on 2011-02-07
i changed them and it seems going to work but they dont look good,
how about cpu and ram indicaotrs? and clock?
look at screenshot

[ATTACH]182920[/ATTACH]

---

### Post by alecive on 2011-02-07
close all conky-related stuff:
```
killall conky
```

and post the result of:
```
conky -c /home/till/Conky/bottom
```


then, do the same as previous but post the result of:
```
conky -c /home/till/Conky/top
```

---

### Post by Action_Radar on 2011-02-07
Hey. I figured it out. I didn't know which value to change to actually change the position of the conky on my desktop. Found out that I had to change the "gap_x" and "gap_y" parameters. I attached a screenshot of the my current setup. 

One question though about the calendar: Could it be that it doesn't work right combined with the notes? I tried to enter a note for february 22nd but it's displayed on february 19th. 
to have it displayed on 22nd i have to enter: 

```
***Febbraio***

25 "some random note"
```

But i have to say you did an absolutely awesome job on that theme man

---

### Post by militarist on 2011-02-07
if you want these result to help me with CPU and ram indicators i should say that i modified bottom and fixed them, i also added another cpu :D but here is the result for additional information

**bottom**
```
till@till-Studio-1555:~$ conky -c /home/till/Conky/bottom
Conky: desktop window (2200181) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x1200001)
Conky: drawing to double buffer
sh: conkyEmail: not found
```**top**
```
till@till-Studio-1555:~$ conky -c /home/till/Conky/top
Conky: desktop window (2200181) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x1200001)
Conky: drawing to double buffer
```my only problem is with checkcal, checkwet and checkmem as you see in screen-shot they dont show completely and i just can see lower part of them.

some good news, i found something with top script, the battery bar is always empty and the reason is this:

```
TEXT
${battery_bar BAT1}
```if we change it to:

```
TEXT
${battery_bar BAT0}
```we will see the full bar, and we can also change it like this:

```
TEXT
${battery_bar BAT0}
${battery_time BAT0}
```to see battery time under bar :D
here is my screen-shot, don't forget my problem :(
thank

[ATTACH]182959[/ATTACH]

---

### Post by alecive on 2011-02-08
@all: Thanks to Action_Radar, I found a bug in the script for the calendar, because this issue happens also to me (but the problem took time to be found).. it's quite stupid, because it happens only in February (because it has 28 days ;)). However, I attach the correct file: replace this instead of file located in "Conky/Notify/note.py"!!! ;)

@Action_Radar: thanks mate, I'm glad to know that you appreciated it! :)

@militarist: I don't forget any problem, be sure.. :D However, few things: 
1. are you sure to use the correct resolution background? Because in my opinion yours it's not the background fitted for 1366x768 screens.. 
2. the first command gave this error: "sh: conkyEmail: not found". So you have to install conkyemail! ;)
3. it comes natural this other question: have you installed and set up correctly conkyforecast?
4. for calendar: have you correctly set up file called "Note.txt" in your home directory?

---

### Post by militarist on 2011-02-08
hey alecive, i finally fixed all of problems, i modified notify* files and i changed some parts so they work.
and now i want to start my own script :D
 i am thinking about moving sync lyrics and LRC file format. it will be good for music and lyric freaks :guitar: :D
so i need some information, i thought you may know
something about how to make text move or about
auto scrolling texts in conky.

waiting for your answer.

---

### Post by alecive on 2011-02-09
Try the ${scroll} token.. but I never used it, so I really don't know how to use it! :(

---

### Post by Action_Radar on 2011-02-09
Thanks for the edited note.py. works perfectly! keep up the good work.

---

### Post by alecive on 2011-02-10
So your desktop works fine right?

As soon as possible I'll update the new version with also a background that fits perfectly your resolution.. ;)

---

### Post by madnorthnorthwest on 2011-02-10
> **alecive said:**
> @madnorthnorthwest: it's really really strange and I can't find the reason.. I have a question: when you shutoff the computer and re-start it, the value inside that ${image} command remains the value that you set up before, or returns the old value?

yes, the value stays the same.

---

### Post by h313 on 2011-02-10
Hello friend:KS
Hats off to your theme. Superb!!! what an eye candy.
Within a night more than a dozen of my friends have requested for the themes.
 But i cannot fulfill their request untill, i successfully solve every problem which i am facing.
I have the some problem regarding conky too :confused:

I am unable to install conkyForecast and conkyEmail on ubuntu10-04.

Also my conkycal and conkywet is not working
Even though conkymem is on it overlaps the bottom bar.
The same is with the top battery meter, not working.

Please help me

---

### Post by alecive on 2011-02-10
@madnorthnorthwest: Maybe the conkystart launchs wrong files? 
Post this:

```
cat conkystart.sh
```

Then, type this:
```
killall conky
```

And post the result of this (wait almost 30-45 seconds before pasting its output):
```
./conkystart.sh
```

@h313: Before correcting your problem we have to solve your issue with conkyforecast&email. Why you cannot install them? Have you read this: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
I'm on 10.04 too but I installed without any problem!

Another thing: read carefully this thread, there many of the solutions for your problem! ;)

---

### Post by h313 on 2011-02-11
thanks for your help.
I sailed through the first part.
The conky's are working.
But i want them on start up.
Each time i boot, no conky is loaded properly.
Its bottom part is reflected in the screen.
I have to 
```

killall conky
```
Then i have to manually run the conky again.
I want a long term solution for it.

Also, can you write a script to automatically change the relative paths for the files.

---

### Post by madnorthnorthwest on 2011-02-13
> **alecive said:**
> @madnorthnorthwest: Maybe the conkystart launchs wrong files? 
Post this:

```
cat conkystart.sh
```Then, type this:
```
killall conky
```And post the result of this (wait almost 30-45 seconds before pasting its output):
```
./conkystart.sh
```

here you go.

cat conkystart.sh

```

#!/bin/bash
sleep 20
conky -d -c ~/Conky/top
sleep 2
conky -d -c ~/Conky/bottom
exit

```./conkystart.sh

```
Conky: forked to background, pid is 1750

Conky: desktop window (22000a6) is subwindow of root window (ac)
Conky: window type - override
Conky: drawing to created window (0x4000001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT1/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT1/state: No such file or directory
Conky: forked to background, pid is 1753
isi@isi-Aspire-3620:~$ 
Conky: desktop window (22000a6) is subwindow of root window (ac)
Conky: window type - override
Conky: drawing to created window (0x4200001)
Conky: drawing to double buffer
Conky: Unable to load image '/home/isi/Conky/Notify/notifywet2.png'
Conky: can't open /proc/acpi/battery/BAT1/state: No such file or directory
Conky: can't open /proc/acpi/battery/BAT1/state: No such file or directory

```

lots of errors it seems. :-(

---

### Post by alecive on 2011-02-13
@ h313: I need a screenshot to understand your problem.. the script would be fine, but I don't know how to do it! :(

@madnorthnorthwest: you don't have BAT1 in /proc/acpi/battery.. open the "top" file and replace BAT1 with BAT0; then re-do the second command and re-post the last command (waiting 60 secs before doing this).
Another thing: after posted it, close the terminal, re-type the last command, open the launcher related to weather and post here also this result! :)

@all: I uploaded the new version; nothing interesting, except from the script note.py that I've already send to you, and the background at 1920x1200 resolution as requested by Action_Radar! ;)

---

### Post by josephtsui on 2011-02-14
Im having problem with CoverGloobus. I have the theme in the .file but it is looking like a black rectangle. I can sort of see the shape of the design but it's not showing up as it should. And Im not playing anything using covergloobus if that's a problem.

Also I can't get the awn theme to work. It is looking like the normal dock. Do I have to enable desktop effect for it to work?

Please help, thx.

---

### Post by alecive on 2011-02-16
What is ".file"?

Can you please take a screenshot of both the issues?

---

### Post by Kwod12 on 2011-02-23
Hi,, I have some questions...

There a line in todo.py that says:
> inp = open('/home/alecive/Documenti/da fare.txt','r')
I don't know where to find the file fare.txt :S

And something else: How it suppose to work the calendar?? I write a new event in google caledar,, but the conky doesn't show it.

And... Can you post your /usr/share/emailconky/conkyemail.py??
I think I change something there :S

Thanks for your time!! :)

---

### Post by alecive on 2011-03-01
Hi Kwod12, sorry for the late reply. However, here are the answers for your question:

1. Don't care about "todo.py", the new version is "note.py"! "todo.py" was only a try that I did some month ago (and quickly forgot :) )

2. Conky calendar is supposed to work reading from a file called "Note.txt" (check the line #27 of "note.py" file). To understand how it works, just read previous posts of this thread, so you'll get a better understanding! If you have other questions about this, just ask.. ;)

3. I've never modified conkyemail, expecially from /usr/share! The best way is using the ppa.. so uninstall it and then re-install it, if you've any problem! :)

Alecive

---

### Post by Kwod12 on 2011-03-02
So why do we have to set our gmail account in the bottom conky??
I supposed that was because it takes the information from google calendar to fill that information...

If you can do that,, would be awesome xD

---

### Post by alecive on 2011-03-03
Gmail account (and/or other accounts if you want) it's used in the bottom left part of the conky, to check the number of unread emails of your account!

It would be awesome doing something so cool with Google calendar, but it's far (very far) from my capacities doing something like this.. :(

---

### Post by Kwod12 on 2011-03-03
> **alecive said:**
> Gmail account (and/or other accounts if you want) it's used in the bottom left part of the conky, to check the number of unread emails of your account!

Oh! I see :D

> **alecive said:**
> It would be awesome doing something so cool with Google calendar, but it's far (very far) from my capacities doing something like this.. :(

Well... Anyway you did a great job doing all this work... 
Thanks a lot!

---

### Post by alecive on 2011-03-03
You're welcome! ;)

---

### Post by polardude1983 on 2011-04-22
Thanks for replying to me on Deviantart. Anyways I just wanted to say thank you for such a brilliant theme. It wasn't what I originally was looking for but I found it and thought I would try it out and it's very nice.

But I wanted to say that the dimensions for each desktop is different. Yes you did do a brilliant job with the bottom conky in doing this. But there are some dimension changes that need to be made in the clickable conky's and I think also in the bottom conky too.

Also I noticed when you did the backgrounds for the clickable conky, that you also included the background picture. But when you included the background picture you did it for your desktop dimensions and not mine. Meaning the clickable conky backgrounds don't match up for my wallpaper dimensions. Anyways it is easily remedied by creating a new transparent background.  You can see what I did basically in this file. This will work for other 1440x900s. [Download here]("http://dl.dropbox.com/u/525938/apps/SummerRebirth_Conky_1440by900.zip") 

Also I had to expand the width of the background image for checkwet. Because when it says what kind of weather it is and when it says "Scattered Thunderstorms" it was too long for the background image. So I extended the background image by 40px.

Anyways I zipped up mine for the 1440x900, and all mine display in Fahrenheit. just fyi

---

### Post by polardude1983 on 2011-04-22
Currently here is a screenshot of my desktop, and how it looks like with the clickable conky's backgrounds with a dark grey at 60%.

---

### Post by alecive on 2011-05-13
Sorry for the late reply.. I was out of my home for a lot of time!

You're right for the clickable conky background, but the problem is that original images add also a gaussian blur behind them, and I like it very much! To mantain this effect, I'd have to draw those images for all screen resolutions.. an huuge work! :S

However, I'll think about adding simply transparent images.. :)

And you're right also for checkwet: in my original idea, I would have increased the width, but I forgot to do so! :) The problem here is that I would know every language and foresee the biggest length for the forecasts!

However, regarding the screenshot, I see two things: the battery bar on the top right doesn't show the battery status, the date in the bottom is not aligned, and there're no notes in the middle clickable conky. If you're using this theme even now, I will be glad to help you in this! :)

---

### Post by scarface777 on 2011-10-02
I just want to thank you for this exelent theme (Gray Revenge).
I had some problems with the conkys, but every thing is just fine now.
Thanks again

---

