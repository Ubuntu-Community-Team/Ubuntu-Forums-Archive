---
title: "console mp3 player"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by krang on 2006-06-08
Hi there,

I'm searching for a mp3 player for good old console. 

With mpg321, for example, the player does not include all my subdirectories. When I ask it to play ./music/* it only plays the few mp3-files directly in there. The player wasn't able to read the playlist from xmms probably and I don't want to write one by hand... ;)

thx for help :)

---

### Post by IYY on 2006-06-08
I would also be interested in something like this. Tell me if you find it, and if you don't maybe I could write a shell script that uses the 'play' command to act as a full command-line media player.

---

### Post by jrattner on 2006-06-08
If you investigate the man page of mpg321 you'll find this:

1).  -@ list, --list list
                 Use  the  file  list  for a playlist. The list should be in a
                 format of filenames followed by a line feed. Multiple  -@  or
                 --list specifiers will be ignored; only the last -@ or --list
                 option will be used. The playlist is concatenated with  fileâ
                 names  specified  on  the  command-line to produce one master
                 playlist. A filename of â-â will cause standard input  to  be
                 read as a playlist.


That may or may not solve your play list problem, but I still understand that most of the problem is derived from the fact that mpg321 does not recursively search the directory.

---

### Post by Juippisi on 2006-06-08
I like MPD. You can control MPD with mpc or ncmpc in the console.

[http://www.musicpd.org/](http://www.musicpd.org/)
[http://www.musicpd.org/clients.shtml](http://www.musicpd.org/clients.shtml)

Nowadays MPD supports even unicode.

---

### Post by krang on 2006-06-08
[QUOTE=jrattner]man page of mpg321[/QUOTE]

It works somehow or not. The problem is, that the player has problems with spaces or special characters.

And I don't want to rewrite my existing playlist by hand... This is too much work for a lazy guy like myself. ;)

---

### Post by krang on 2006-06-08
[QUOTE=Juippisi]I like MPD. You can control MPD with mpc or ncmpc in the console.

[http://www.musicpd.org/](http://www.musicpd.org/)
[http://www.musicpd.org/clients.shtml](http://www.musicpd.org/clients.shtml)

Nowadays MPD supports even unicode.[/QUOTE]

Ok, this seems to work fine and I can broadcast my music through the intranet here. Maybe I'll try that soon... ;)
Have to get used to it then.

What I don't like is to run a deamon for it. Even my old PC was able to connect to it and with top it seems like mpd runs several times. I can kill the process but it restarts all the time or sth. like that :confused:

---

