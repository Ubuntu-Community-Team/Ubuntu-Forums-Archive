---
title: "controlling Rhythmbox using the terminal"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-10-06
Is there a way for me to open Rhythmbox and play a certain song through the terminal?  How would I do this?
Also, is there a way for me to open up Rhythmbox at a specified time of day through a script?

---

### Post by adwait on 2005-10-06
I don't really think you can play a specific song in rhythmbox through the command line........but you can start it at a specific time using a script Just add the following to a file
```
rhythmbox
```
No make the file executable:
```
chmod +x <filename>
```

Now in user this command to open up your crontab file
```
sudo gedit /etc/crontab
```

And enter the entry with your time....

---

### Post by 3david on 2005-10-24
I don't know how to play a song directly from the terminal using rhythmbox,
but it can be done with xmms, beep-media-player, mpg321, ogg123 and more...

just run:
```
{program name} {song filename}
```

(where program name is either xmms, beep-media-player, mpg321 or ogg123)

if you just want to add the file to xmms or beep-media-player's playlist run:
```
 xmms -e {song filename} 
```
or:
```
 beep-media-player -e {song filename} 
```

see "xmms --help" or "beep-media-player --help" for more options,

oh, and i almost forgot Music Player Daemon (mpd), which you can do practically anything from the terminal.

---

