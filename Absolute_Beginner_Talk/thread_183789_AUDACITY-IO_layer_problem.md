---
title: "AUDACITY-I/O layer problem"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by bigben on 2006-05-28
When i start up audacity,a warning screen comes up saying that i dont have the i/0 layer configured or smth..
I do have sound and i can listen to music ect...what do i have to do in order to fix this problem?
AUdacity is one of the most important programms for my as i use it for my djset recordings..
any help highly apreciated
greetz

---

### Post by lha on 2006-05-29
[QUOTE=bigben]When i start up audacity,a warning screen comes up saying that i dont have the i/0 layer configured or smth..
I do have sound and i can listen to music ect...what do i have to do in order to fix this problem?
AUdacity is one of the most important programms for my as i use it for my djset recordings..
any help highly apreciated
greetz[/QUOTE]

Run
```
sudo sh -c 'echo -e "#!/bin/sh\nesddsp /usr/bin/audacity">>/usr/local/bin/audacity;chmod a+x /usr/local/bin/audacity'
``` It creates script that will be automatically used when you start audacity. It uses esddsp to route audacity's output to esd. (You may need to install esound-clients.) It may not work that well, though. Audio playback may slow down. Another option is to kill esd before starting audacity. (This works for me.) Run
```
sudo sh -c 'echo -e "#!/bin/sh\nkillall esd\n/usr/bin/audacity">>/usr/local/bin/audacity;chmod a+x /usr/local/bin/audacity'
``` to create a script that does the trick. There's drawback in this: Because esd gets killed, no other audio (well, the most of) won't work until you restart esd or you computer. If you want to remove this sript, use ```
sudo rm /usr/local/bin/audacity
```.

---

### Post by Zimmer on 2006-05-29
[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

sorted my Audacity issues....

And there is more interesting reading on Sound here

[http://www.ubuntuforums.org/showthread.php?t=101125](http://www.ubuntuforums.org/showthread.php?t=101125)

---

### Post by bigben on 2006-05-29
thanx for the answers,Iha,the second code seems to work for me,i can play audio now,haven't tried recording yet..will i be able to export wav files to mp3 or do i need to install lame encoder ? if so,what is the best way? cheers :)

---

### Post by Zimmer on 2006-05-30
[QUOTE=bigben]thanx for the answers,Iha,the second code seems to work for me,i can play audio now,haven't tried recording yet..will i be able to export wav files to mp3 or do i need to install lame encoder ? if so,what is the best way? cheers :)[/QUOTE]
[http://www-users.york.ac.uk/~raa110/audacity/AudacityHelp.html#LAME](http://www-users.york.ac.uk/~raa110/audacity/AudacityHelp.html#LAME)
Yes, you need the LAME encoder , and When you first export to mp3 a dialog box will ask for the location of the encoder... or you can set it in the preferences, I think...either way, it only needs to be done the once.
Install from Synaptic gstreamer0.8-lame (and lame and liblame0 if they are not installed as dependencies)

---

### Post by arphe_el on 2006-05-31
Dear Zimmer,

Is there a link that provide information on how to record audio music from tape recorder to cd using audacity.

A step by step procedure will help me. Any help greatly appreciated. thank you and GODspeed!

Best regards,


Rowell

---

### Post by Zimmer on 2006-05-31
[QUOTE=arphe_el]Dear Zimmer,

Is there a link that provide information on how to record audio music from tape recorder to cd using audacity.

A step by step procedure will help me. Any help greatly appreciated. thank you and GODspeed!

Best regards,
Rowell[/QUOTE]
I have not seen a How to on this but it is quite simple. Read  in the HELP file for the  Meter Toolbar which will give you some general hints on recording levels.

Connect the Tape player output to the line-in socket on the PC (or Mic if there is no Line-in) ,
Open Audacity and on the mixer toolbar select the input source (Line-in or Mic).
Press record Button in Audacity, press play on tape player. 
Check the levels to get a good signal without clipping.
Have a cup of tea. (optional) ;) 
Come back when song/abum has played. 
Press stop in Audacity and save/export  the results to whatever format you wish.
It is then possible to use Gnomebaker or Serpentine to create an audio CD from the tracks.

Watch out for the size of files!! wav files can be rather large....

---

