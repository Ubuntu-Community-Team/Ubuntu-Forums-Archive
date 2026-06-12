---
title: "All codecs you ever wanted, Xvid, divx, mp3, wmv, mkv, etc.."
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by edurm on 2005-10-08
After installing Ubuntu 5.04 how can I play Mpeg4 movies, VCD, SVCD, mp3/wmv audios, subtitles, and all others?

is there a codec pack like windows?


is there a HOWTO guide teaching n00bs like me ? :D 



Thks'n advanced

---

### Post by bionnaki on 2005-10-08
[http://ubuntuguide.org](http://ubuntuguide.org)

Just follow it from top to bottom.

---

### Post by nerdman on 2005-10-08
XD thats a little harsh.

hit Ctrl+F and find "XMMS"
its just a player, its nearly identical to winamp and plays just about all audio types of media.

Also, the multimedia codec packages there aren't all working I've found, but to increase your chances make sure you add more repositories. (also on the guide).

---

### Post by landotter on 2005-10-08
download codec pack from mplayer website.

unpack into /usr/lib/win32

this is a really really really really common question--the search function on the forum front page will give you an answer faster than posting.

---

### Post by Wolki on 2005-10-08
A wealth of information regarding codecs and stuff:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

It's always good to use the wiki for such information, since it's usually the most up-to-date and detailed enough.

---

### Post by tseliot on 2005-10-08
You can use my guide if you need the video codecs:

[http://ubuntuforums.org/showthread.php?t=70227]("http://ubuntuforums.org/showthread.php?t=70227")

---

### Post by edurm on 2005-10-09
[QUOTE=tseliot]You can use my guide if you need the video codecs:

[http://ubuntuforums.org/showthread.php?t=70227]("http://ubuntuforums.org/showthread.php?t=70227")[/QUOTE]



Thank You Everybody!




> 3) Launch Xine (or Totem) and try to play a video (this will create a .config file)


after install both programs, I could not find a shortcut to Xine :confused: 

I already had TOTEM Movie Player, It came with default DVD instalation, is this totem-xine different from the original ?

---

### Post by varunus on 2005-10-09
How to get almost every codec you'll ever need:

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

Make sure to follow their "add extra repositories" section too.

---

### Post by landotter on 2005-10-09
alt+f2 will give you a run dialog, you can type "xine" or the name of any program you want to run into it, best of all it tab completes.

---

### Post by edurm on 2005-10-09
```

root@ubuntu:~/public# mv essential-20050412/* /usr/lib/win32
mv: when moving multiple files, last argument must be a directory
Try `mv --help' for more information.

```


anyhelp ?

---

### Post by edurm on 2005-10-09
[QUOTE=edurm]```

root@ubuntu:~/public# mv essential-20050412/* /usr/lib/win32
mv: when moving multiple files, last argument must be a directory
Try `mv --help' for more information.

```


anyhelp ?[/QUOTE]



OPPS, n00b detected, I forgot to create /usr/lib/win32 directory :rolleyes:

---

### Post by edurm on 2005-10-09
I can't wait untill Ubuntu 5.10 be released, to use EASY UBUNTU 2.3 :p 


[http://www.ubuntuforums.org/showthread.php?t=64629](http://www.ubuntuforums.org/showthread.php?t=64629)

---

### Post by tseliot on 2005-10-09
[QUOTE=edurm]```

root@ubuntu:~/public# mv essential-20050412/* /usr/lib/win32
mv: when moving multiple files, last argument must be a directory
Try `mv --help' for more information.

```


anyhelp ?[/QUOTE]
sudo mkdir /usr/lib/win32 
and try again

EDIT: I hadn't noticed you noticed :p

---

