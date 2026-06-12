---
title: "How to save?"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-10-10
Hello im running 
vi savage in terminal how to save after compiling?;)

---

### Post by meng on 2006-10-10
After compiling? or after editing?
To save what you have done in your vi session, esc : (colon)wq-ENTER.
Unless I misunderstood your question completely.

---

### Post by Timothy Butwinick on 2006-10-10
Press ESC
Write:
```
:w
```
(Don't forget the colon!)

That should do the trick.

---

### Post by haxer on 2006-10-10
Ok but i have this error when i hit esc then typeing in :w and pressing enter it says 







#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd /home/oem/games/Savage
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin $@ /home/oem/games/Savage
exit 0
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
E45: 'readonly' flag is set (add ! to force)  

whooot should i do now?

---

### Post by haxer on 2006-10-10
Please help me ](*,)

---

### Post by meng on 2006-10-10
Okay, first I should say, "Be patient!" No one likes a whiner.
Second, what is the name of this file? Is it savage? What are the existing permissions on the file (assuming it is an existing file), otherwise if it is a completely new file, what are the existing permissions on the directory.
Again, please understand these are forums, and volunteers are offering their time for no material reward. If you have to wait for 12 minutes, do not panic. If you can't wait for 12 minutes, you're in the wrong place.

---

### Post by Aberrix on 2006-10-10
open it with

```
sudo vi filename
```

then

```
:x
```

to save and quit

---

### Post by haxer on 2006-10-10
Oh im sorry not ment to be whining im just tired ive got help thought this page [http://czarism.com/how-to-install-savage-on-ubuntu-debian-linux](http://czarism.com/how-to-install-savage-on-ubuntu-debian-linux) then i dont know how to save the file after using vi savage have tried with the :w enter thing didnt work as i was planing :P and i really like this forum i never ment to say something stupid but its like when you try to open a can of something and the look wont open and you struggle to death or something the last thing to do is just saw it up or something im tired of the guide on that site [http://czarism.com/how-to-install-savage-on-ubuntu-debian-linux](http://czarism.com/how-to-install-savage-on-ubuntu-debian-linux) and it seems that its out of date someone told me one person got it work not me:P and now im just trying to ask around untill i get help with it becuse im to noob to figure it out my self :) so thanks to all people who are helping out :)



and that with the sudo vi savage and then esc :x didnt work either :p

---

### Post by haxer on 2006-10-10
Didnt work either :( :-k

---

### Post by meng on 2006-10-10
One big difference between standard Debian and Ubuntu is that in Debian, the root account is enabled by default, whereas in Ubuntu is isn't.
Also, as much as I love vi, it is the least intuitive text editor in existence.

Can you exit to shell and show the output of:
ls -l

---

### Post by Aberrix on 2006-10-10
> **meng said:**
> Also, as much as I love vi, it is the least intuitive text editor in existence.

If you know how to use vi it's the best. It took lots of headaches learning and getting use to vi, but now that I know it... I'll never use anything else...

---

### Post by Aberrix on 2006-10-10
> **haxer said:**
> Didnt work either :( :-k

what did it tell you?

---

### Post by haxer on 2006-10-10
the same thing that las red label and black text saying something to add to force dont know really what that means?

And how to exit to shell? i meant this ls -l and i dont know how to get to shell so that one i need explain to :)

---

### Post by meng on 2006-10-10
> **Aberrix said:**
> If you know how to use vi it's the best. It took lots of headaches learning and getting use to vi, but now that I know it... I'll never use anything else...
Say Aberrix, as rude as it is to post a different problem in a thread, I have had trouble working out how to edit and navigate simultaneously (without pressing esc) in certain terminals. While editing (inserting OR replacing), are there other options for navigating besides the arrow keys?

---

### Post by haxer on 2006-10-10
if you mean this 
oem@haxer:~$ ls -l
total 1171444
-rw-r--r--  1 oem   oem         80 2006-10-08 02:42 81.226.202.138
-rw-r--r--  1 oem   oem    2641000 2006-07-16 02:50 amsn_0.97b_tcl0.95.deb
drwx------  2 oem   oem       4096 2006-09-10 02:10 amsn_received
-rw-r--r--  1 oem   oem        165 2006-10-09 18:56 automatix.log
-rw-r--r--  1 oem   oem      95046 2006-06-30 13:00 conky_1.4.2-0ubuntu1_i386.deb
-rw-r--r--  1 root  root     93622 2006-09-10 16:31 current.tar.bz2
-rw-r--r--  1 oem   oem     409142 2006-09-14 03:04 democracyplayer-data_0.9.0-1ubuntupcf_all.deb.1
drwxr-xr-x  6 oem   oem       4096 2006-10-10 20:58 Desktop
drwxr-xr-x 13 oem   oem       4096 2006-07-19 01:51 easyubuntu
drwx---r-x  4 haxer 1000      4096 2006-09-10 16:31 EasyUbuntu_2006-09-11
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz.1
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz.2
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz.3
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz.4
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz.5
-rw-r--r--  1 oem   oem     180407 2005-04-04 16:35 epsxe160lin.zip
-rwxr-xr-x  1 root  root 270965248 2005-06-06 13:22 et-linux-2.60.x86.run
lrwxrwxrwx  1 oem   oem         26 2006-09-08 23:51 Examples -> /usr/share/example-content
-rw-r--r--  1 oem   oem     433988 2006-09-22 20:14 Firefox_wallpaper.png
drwxr-xr-x  3 oem   oem       4096 2006-10-10 18:35 games
lrwxrwxrwx  1 oem   oem         35 2006-09-17 14:21 googleearth -> /home/oem/google-earth//googleearth
drwxr-xr-x  9 oem   oem       4096 2006-09-17 22:06 google-earth
-rwxr-xr-x  1 oem   oem   19786344 2006-09-15 08:02 GoogleEarthLinux.bin
-rw-r--r--  1 oem   oem     222056 2005-06-12 09:29 gpupeopssoftx117.tar.gz
-rw-r--r--  1 oem   oem     189449 2005-12-29 17:44 gpupetexgl208.tar.gz
drwxr-xr-x  5 oem   oem       4096 2006-09-09 11:47 gtk-gnutella-downloads
-rw-r--r--  1 oem   oem      22770 2006-09-15 19:32 hs_err_pid10533.log
-rw-r--r--  1 oem   oem      25960 2006-09-15 19:33 hs_err_pid10678.log
-rw-r--r--  1 oem   oem      26451 2006-09-22 20:11 hs_err_pid14324.log
-rw-r--r--  1 oem   oem      26438 2006-09-29 23:19 hs_err_pid20741.log
-rw-r--r--  1 oem   oem      26416 2006-09-27 16:41 hs_err_pid31345.log
drwxr-xr-x  2 oem   oem       4096 2006-09-14 00:48 Incomplete
-rw-r--r--  1 oem   oem        661 2006-09-11 21:16 index.html
-rw-r--r--  1 oem   oem      33686 2006-08-05 22:29 jriddell.key
-rw-r--r--  1 oem   oem       1730 2006-08-27 05:41 key.gpg.asc
-rw-r--r--  1 oem   oem       1730 2006-09-16 20:53 key.gpg.asc.1
-rw-r--r--  1 oem   oem     348261 2005-04-08 22:24 libiec61883-1.0.0.tar.gz
drwxr-xr-x  6 oem   oem       4096 2006-10-09 14:15 libraw1394-1.2.0
-rw-r--r--  1 oem   oem     376314 2005-02-19 17:58 libraw1394-1.2.0.tar.gz
drwxr-xr-x  2 oem   oem       4096 2006-09-16 15:29 logs
drwxr-xr-x 16 oem   oem       4096 2006-10-09 14:11 mythplugins
drwxr-xr-x 15 oem   oem       4096 2006-10-09 14:14 myththemes
drwxr-xr-x 14 oem   oem       4096 2006-10-09 14:16 mythtv
-rw-------  1 root  root        39 2006-09-08 22:04 nano.save
-rw-r--r--  1 oem   oem       1787 2006-08-05 22:36 quinn1.key
-rw-r--r--  1 oem   oem       1690 2006-08-05 22:37 quinn2.key
lrwxrwxrwx  1 oem   oem         29 2006-10-10 18:35 savage -> /home/oem/games/Savage/savage
-rw-r--r--  1 oem   oem  331204271 2006-09-05 20:44 savage_linux.sh
-rw-r--r--  1 oem   oem   76732118 2004-01-27 22:53 savage_patch_200b.tar.gz
-rw-r--r--  1 oem   oem    1441305 2004-01-27 22:50 savage_patch_200b_to_200c.tar.gz
-rw-r--r--  1 oem   oem      40695 2004-09-19 12:53 spupeopsoss109.tar.gz
drwxr-xr-x  3 root  root      4096 2006-09-08 22:51 steam4linux
-rw-r--r--  1 root  root      3796 2006-08-13 15:08 steam4linux.tar.gz
-rw-r--r--  1 oem   oem       3796 2006-08-13 15:08 steam4linux.tar.gz.1
-rw-r--r--  1 oem   oem       3796 2006-08-13 15:08 steam4linux.tar.gz.2
drwxr-xr-x  2 oem   oem       4096 2006-09-08 23:07 steam_bin
drwxr-xr-x  2 oem   oem       4096 2006-09-14 04:33 steam_download_path
-rw-r--r--  1 oem   oem    1521168 2006-02-02 00:50 tcl8.5_8.5.0-1~neto3_i386.deb
drwxr-xr-x  5 oem   oem       4096 2006-09-09 20:22 TeamSpeak2RC2
lrwxrwxrwx  1 oem   oem         41 2006-10-02 14:46 TransGaming_Drive -> /home/oem/.cedega/Dot TransGaming/c_drive
-rwxr-xr-x  1 oem   oem  475313208 2006-09-29 17:02 true.combat.elite_0.49-english.run
-rw-r--r--  1 oem   oem   14253210 2006-09-12 10:31 w32codecs_20060611-1plf1_i386.deb
-rw-r--r--  1 oem   oem    1063082 2006-09-29 22:32 wget-log
drwxr-xr-x  6 oem   oem       4096 2006-09-27 18:37 winexs
-rw-r--r--  1 oem   oem      71652 2006-01-05 09:55 xmms-wma_1.0.4-2_i386.deb

---

### Post by meng on 2006-10-10
Ok, in that directory you have a symbolic link called "savage" and then you're trying to save an actual file on top of that called "savage". How about you try this from shell:
rm savage
vi savage
(then edit and save)

---

### Post by Aberrix on 2006-10-10
> **meng said:**
> Say Aberrix, as rude as it is to post a different problem in a thread, I have had trouble working out how to edit and navigate simultaneously (without pressing esc) in certain terminals. While editing (inserting OR replacing), are there other options for navigating besides the arrow keys?

As much as I use vi I am no expert, I still find my self referencing command sheets, but to answer your question; yes there is: [http://atlas.scs.carleton.ca/~youngsoo/misc/vi.html](http://atlas.scs.carleton.ca/~youngsoo/misc/vi.html)

---

### Post by meng on 2006-10-10
> **Aberrix said:**
> As much as I use vi I am no expert, I still find my self referencing command sheets, but to answer your question; yes there is: [http://atlas.scs.carleton.ca/~youngsoo/misc/vi.html](http://atlas.scs.carleton.ca/~youngsoo/misc/vi.html)
Thanks anyway, but those other options won't work in entry mode (e.g. you can't press h in entry mode and expect to get anything other than 'h'!). I'll keep looking!

---

### Post by haxer on 2006-10-10
nope the rv savage just cleans the document if thats the meaning i dont know then i try to insert this 

#LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./savage.bin /home/oem/games/Savage
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin $@ /home/oem/games/Savage
exit 0 

then pressed esc then typed in :w then enter didnt work still the same error 

E45: 'readonly' flag is set (Add ! to force)

---

### Post by Aberrix on 2006-10-10
> **haxer said:**
> nope the rv savage just cleans the document if thats the meaning i dont know then i try to insert this

rv or rm?

---

### Post by haxer on 2006-10-10
rm wrote wrong in reply sorry :( but it didnt work :)

---

### Post by meng on 2006-10-10
Okay, I'm not sure I understood your last post, did you exit to shell first? If not, you exit to shell from vi like this
(esc) :q!

then at the command prompt type
rm savage
vi savage

But if may have already tried this, and if so, then please show the output of:
ls -l ..
(with the two periods at the end)

---

### Post by meng on 2006-10-10
Ah, no sorry my last post won't really help you!
Here's what I suggest: edit the file again with vi, and when you're done, press
(escape) :wq! (enter)

That's all I can think of.

---

### Post by haxer on 2006-10-10
> **meng said:**
> Okay, I'm not sure I understood your last post, did you exit to shell first? If not, you exit to shell from vi like this
(esc) :q!

then at the command prompt type
rm savage
vi savage

But if may have already tried this, and if so, then please show the output of:
ls -l ..
(with the two periods at the end)

ok now we are not talking about the same where should i type in exc :q if you mean in the savage i dont know but i already done the rm savage  and vi savage and compiling but i cant save so its gone like the wind and should i try ls -l now? :S :-k


Edit: Ok now i understand :)

---

### Post by Aberrix on 2006-10-10
I am kinda reaching and dont know if this would work, but..

```
sudo rm savage
```

?

---

### Post by meng on 2006-10-10
No, just try:
vi savage
(edit the file - it's not called compiling, that's something different)
and when you've finished editing, try

(esc) :wq! (enter)

---

### Post by haxer on 2006-10-10
meng your on the right track now i editited it and saved it trough wq! or what it was but now when i try to start the game typeing in 
oem@haxer:~$ ~/savage
bash: /home/oem/savage: Permission denied


so im on the track now :) but i need permison :p and dont know how

---

### Post by Timothy Butwinick on 2006-10-10
"sudo ./savage" and enter your password.

---

### Post by meng on 2006-10-10
from prompt (where you were just then), run:
ls -l savage

also:
ls -l ~

and show us results.

---

### Post by haxer on 2006-10-10
sweden :D i get this output 

oem@haxer:~$ sudo ./savage
sudo: ./savage: command not found

---

### Post by haxer on 2006-10-10
and meng first i get this 

oem@haxer:~$ ls -l savage
-rw-r--r-- 1 oem oem 297 2006-10-10 21:29 savage
oem@haxer:~$

then i get this 

oem@haxer:~$ ls -l ~
total 1171448
-rw-r--r--  1 oem   oem         80 2006-10-08 02:42 81.226.202.138
-rw-r--r--  1 oem   oem    2641000 2006-07-16 02:50 amsn_0.97b_tcl0.95.deb
drwx------  2 oem   oem       4096 2006-09-10 02:10 amsn_received
-rw-r--r--  1 oem   oem        165 2006-10-09 18:56 automatix.log
-rw-r--r--  1 oem   oem      95046 2006-06-30 13:00 conky_1.4.2-0ubuntu1_i386.deb
-rw-r--r--  1 root  root     93622 2006-09-10 16:31 current.tar.bz2
-rw-r--r--  1 oem   oem     409142 2006-09-14 03:04 democracyplayer-data_0.9.0-1ubuntupcf_all.deb.1
drwxr-xr-x  6 oem   oem       4096 2006-10-10 20:58 Desktop
drwxr-xr-x 13 oem   oem       4096 2006-07-19 01:51 easyubuntu
drwx---r-x  4 haxer 1000      4096 2006-09-10 16:31 EasyUbuntu_2006-09-11
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz.1
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz.2
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz.3
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz.4
-rw-r--r--  1 oem   oem      92665 2006-07-19 01:59 easyubuntu-3.022.tar.gz.5
-rw-r--r--  1 oem   oem     180407 2005-04-04 16:35 epsxe160lin.zip
-rwxr-xr-x  1 root  root 270965248 2005-06-06 13:22 et-linux-2.60.x86.run
lrwxrwxrwx  1 oem   oem         26 2006-09-08 23:51 Examples -> /usr/share/example-content
-rw-r--r--  1 oem   oem     433988 2006-09-22 20:14 Firefox_wallpaper.png
drwxr-xr-x  3 oem   oem       4096 2006-10-10 18:35 games
lrwxrwxrwx  1 oem   oem         35 2006-09-17 14:21 googleearth -> /home/oem/google-earth//googleearth
drwxr-xr-x  9 oem   oem       4096 2006-09-17 22:06 google-earth
-rwxr-xr-x  1 oem   oem   19786344 2006-09-15 08:02 GoogleEarthLinux.bin
-rw-r--r--  1 oem   oem     222056 2005-06-12 09:29 gpupeopssoftx117.tar.gz
-rw-r--r--  1 oem   oem     189449 2005-12-29 17:44 gpupetexgl208.tar.gz
drwxr-xr-x  5 oem   oem       4096 2006-09-09 11:47 gtk-gnutella-downloads
-rw-r--r--  1 oem   oem      22770 2006-09-15 19:32 hs_err_pid10533.log
-rw-r--r--  1 oem   oem      25960 2006-09-15 19:33 hs_err_pid10678.log
-rw-r--r--  1 oem   oem      26451 2006-09-22 20:11 hs_err_pid14324.log
-rw-r--r--  1 oem   oem      26438 2006-09-29 23:19 hs_err_pid20741.log
-rw-r--r--  1 oem   oem      26416 2006-09-27 16:41 hs_err_pid31345.log
drwxr-xr-x  2 oem   oem       4096 2006-09-14 00:48 Incomplete
-rw-r--r--  1 oem   oem        661 2006-09-11 21:16 index.html
-rw-r--r--  1 oem   oem      33686 2006-08-05 22:29 jriddell.key
-rw-r--r--  1 oem   oem       1730 2006-08-27 05:41 key.gpg.asc
-rw-r--r--  1 oem   oem       1730 2006-09-16 20:53 key.gpg.asc.1
-rw-r--r--  1 oem   oem     348261 2005-04-08 22:24 libiec61883-1.0.0.tar.gz
drwxr-xr-x  6 oem   oem       4096 2006-10-09 14:15 libraw1394-1.2.0
-rw-r--r--  1 oem   oem     376314 2005-02-19 17:58 libraw1394-1.2.0.tar.gz
drwxr-xr-x  2 oem   oem       4096 2006-09-16 15:29 logs
drwxr-xr-x 16 oem   oem       4096 2006-10-09 14:11 mythplugins
drwxr-xr-x 15 oem   oem       4096 2006-10-09 14:14 myththemes
drwxr-xr-x 14 oem   oem       4096 2006-10-09 14:16 mythtv
-rw-------  1 root  root        39 2006-09-08 22:04 nano.save
-rw-r--r--  1 oem   oem       1787 2006-08-05 22:36 quinn1.key
-rw-r--r--  1 oem   oem       1690 2006-08-05 22:37 quinn2.key
-rw-r--r--  1 oem   oem        297 2006-10-10 21:29 savage
-rw-r--r--  1 oem   oem  331204271 2006-09-05 20:44 savage_linux.sh
-rw-r--r--  1 oem   oem   76732118 2004-01-27 22:53 savage_patch_200b.tar.gz
-rw-r--r--  1 oem   oem    1441305 2004-01-27 22:50 savage_patch_200b_to_200c.tar.gz
-rw-r--r--  1 oem   oem      40695 2004-09-19 12:53 spupeopsoss109.tar.gz
drwxr-xr-x  3 root  root      4096 2006-09-08 22:51 steam4linux
-rw-r--r--  1 root  root      3796 2006-08-13 15:08 steam4linux.tar.gz
-rw-r--r--  1 oem   oem       3796 2006-08-13 15:08 steam4linux.tar.gz.1
-rw-r--r--  1 oem   oem       3796 2006-08-13 15:08 steam4linux.tar.gz.2
drwxr-xr-x  2 oem   oem       4096 2006-09-08 23:07 steam_bin
drwxr-xr-x  2 oem   oem       4096 2006-09-14 04:33 steam_download_path
-rw-r--r--  1 oem   oem    1521168 2006-02-02 00:50 tcl8.5_8.5.0-1~neto3_i386.deb
drwxr-xr-x  5 oem   oem       4096 2006-09-09 20:22 TeamSpeak2RC2
lrwxrwxrwx  1 oem   oem         41 2006-10-02 14:46 TransGaming_Drive -> /home/oem/.cedega/Dot TransGaming/c_drive
-rwxr-xr-x  1 oem   oem  475313208 2006-09-29 17:02 true.combat.elite_0.49-english.run
-rw-r--r--  1 oem   oem   14253210 2006-09-12 10:31 w32codecs_20060611-1plf1_i386.deb
-rw-r--r--  1 oem   oem    1063082 2006-09-29 22:32 wget-log
drwxr-xr-x  6 oem   oem       4096 2006-09-27 18:37 winexs
-rw-r--r--  1 oem   oem      71652 2006-01-05 09:55 xmms-wma_1.0.4-2_i386.deb

---

### Post by meng on 2006-10-10
Ah I know:
chmod a+x savage

then run it.

---

### Post by Timothy Butwinick on 2006-10-10
Please delete this. I type to slowly...

---

### Post by haxer on 2006-10-10
That worked great but i tryid to creat me an caracter after the cd key is 000000000000  and i says cant resolve server something.something.something :S

---

### Post by haxer on 2006-10-10
And i get this in terminal after the ~/savage and before it starts 

oem@haxer:~$ ~/savage
./silverback.bin: /usr/lib/libGL.so.1: no version information available (required by ./silverback.bin)
System_Init()
no startup.cfg found, generating one for you...
Unknown command: '/home/oem/games/Savage'

---

### Post by meng on 2006-10-10
Sorry that's as much as I'm able to help.

---

### Post by haxer on 2006-10-10
Ok no problems :) thanks for helping me out really kind of you all im really happy right now :) 8)

---

