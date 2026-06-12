---
title: "wma frustration!!!"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-05-27
Hi all!

Well, I have been searching the forum for hours now and frustration is taking hold!

I have finally been able to play mp3's but still can't get ubuntu to play wma's.  I think I did the w32codec thing right, but nothing will play wma's.  Totem will only play wmv and nothing else.  Exaile will play mp3's but nothing else.  I have installed the AUD-DVD codecs in Automatix, so what now?  I have gone through the "restricted formats" page but still nothing works.  ](*,) 

Can anyone help? :confused: 

Russty

---

### Post by richbarna on 2006-05-27
Here's a good thread :-
[http://www.ubuntuforums.org/showthread.php?t=182902]("http://www.ubuntuforums.org/showthread.php?t=182902")

---

### Post by Russty of Oz on 2006-05-27
I have tried that, and it says in the Read Me that your double click on the EasyUbuntu file and then click Run.   Well, I did the first and a box opened with nothing in it and all there was to click was Open, so I did that and a few messages came up then nothing!

What am I doing wrong?

---

### Post by Russty of Oz on 2006-05-27
I just checked and I have the w32codecs installed in    usr/lib/codecs   

so what is wrong, why wont they work?

---

### Post by skippy81 on 2006-05-27
Are you sure your WMAs arnt digitally locked?

One of the upgrades to M$ Windows Media player basically tricked loads of users into 'locking' any CD tracks they burnt to their windows PC.  

Have you tried testing to see if your WMAs will play on a different windows system to the one you burnt them on? 

I had the same problem with a mates computer, he reinstalled windows and was therefore unable to play half of his old songs he had ripped.  Microsoft disabled the crappy feature on later versions after getting tons of abusive phonecalls, but there are still a lot of users out there with locked WMAs.

---

### Post by mlind on 2006-05-27
[QUOTE=Russty of Oz]I just checked and I have the w32codecs installed in    usr/lib/codecs   

so what is wrong, why wont they work?[/QUOTE]

Totem uses probably Gstreamer framework for displaying media content.
In my experience, **mplayer** is the best for .wma video types and it actually uses
w32codecs package.

You may also have success with VLC, which is IMO the best video player for linux
today, but you'll have to install additional gstreamer codecs.
gstreamer0.xx-plugins-ugly should help, and maybe gstreamer0.xx-pitfdll too.

Totem is okay, but has still some shortcomings.

---

### Post by Russty of Oz on 2006-05-27
[QUOTE=skippy81]Are you sure your WMAs arnt digitally locked?

One of the upgrades to M$ Windows Media player basically tricked loads of users into 'locking' any CD tracks they burnt to their windows PC.  

Have you tried testing to see if your WMAs will play on a different windows system to the one you burnt them on? 

I had the same problem with a mates computer, he reinstalled windows and was therefore unable to play half of his old songs he had ripped.  Microsoft disabled the crappy feature on later versions after getting tons of abusive phonecalls, but there are still a lot of users out there with locked WMAs.[/QUOTE]


They used to play on Ubuntu before, it's just that I had to do a complete reinstall of Ubuntu and now I can't get them to work.

---

### Post by Russty of Oz on 2006-05-27
[QUOTE=mlind]Totem uses probably Gstreamer framework for displaying media content.
In my experience, **mplayer** is the best for .wma video types and it actually uses
w32codecs package.

You may also have success with VLC, which is IMO the best video player for linux
today, but you'll have to install additional gstreamer codecs.
gstreamer0.xx-plugins-ugly should help, and maybe gstreamer0.xx-pitfdll too.

Totem is okay, but has still some shortcomings.[/QUOTE]

I will try to get mplayer and let you know if it works.  Now, where will I find it.....?

---

### Post by mlind on 2006-05-27
[QUOTE=Russty of Oz]I will try to get mplayer and let you know if it works.  Now, where will I find it.....?[/QUOTE]

```

$ apt-cache policy mplayer
mplayer:
  Installed: 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8
  Candidate: 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8
  Version table:
 *** 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 0
        500 http://fi.archive.ubuntu.com dapper/multiverse Packages
        100 /var/lib/dpkg/status

```

It's on multiverse.

---

### Post by Russty of Oz on 2006-05-27
it says it is not installed.

any help here?

---

### Post by Sef on 2006-05-27
> it says it is not installed.

any help here?

1) Are your repositories enabled?  If not, then go to [Adding repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto").

2) System > Administration > Synaptic Package Manager > search MPlayer > highlight Mplayer > apply

---

### Post by Russty of Oz on 2006-05-27
All the repositories are enabled.  I found a series of Mplayer's in the Synaptic Package Manager but they would not install.  

Ho Hum!

---

### Post by mlind on 2006-05-27
[QUOTE=Russty of Oz]All the repositories are enabled.  I found a series of Mplayer's in the Synaptic Package Manager but they would not install.  

Ho Hum![/QUOTE]

You must "update " file lists after enabling new repository

try using apt-get from terminal
```

sudo apt-get update
sudo apt-get install mplayer-???

```

where ??? is your kernel architechture. 
For amd use k7, for i386 it's 386 and for i686 it's 686.

---

### Post by Russty of Oz on 2006-05-27
it say "package mplayer has no installation canidate" ??

Perhaps it will be easier to convert all my wma's to mp3 and then they will play on Exaile!

---

### Post by patrick295767 on 2006-05-27
Have a look to my script multimedia.sh to configure your codecs ... easily !!
  (in my signature) 
  
Greetz !!

---

### Post by tartarian on 2006-05-27
You could just go to [http://www.nch.com.au/switch/plus.html]("http://www.nch.com.au/switch/plus.html")
and download Switch. Convert your WMA's to MP3's et volia!

---

### Post by Bagnaj97 on 2006-05-27
You can use xmms to play WMAs if you install xmms-wma. Download the RPM here [http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5-1.i386.rpm](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5-1.i386.rpm) and convert it to .deb using alien.

---

### Post by Russty of Oz on 2006-05-27
[QUOTE=tartarian]You could just go to [http://www.nch.com.au/switch/plus.html]("http://www.nch.com.au/switch/plus.html")
and download Switch. Convert your WMA's to MP3's et volia![/QUOTE]

I have already got  that on windows.  If all else fails I will do it, but I used to be able to play wma's on Ubuntu before I messed the whole thing up and had to start again.

---

### Post by Russty of Oz on 2006-05-27
[QUOTE=Bagnaj97]You can use xmms to play WMAs if you install xmms-wma. Download the RPM here [http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5-1.i386.rpm](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5-1.i386.rpm) and convert it to .deb using alien.[/QUOTE]

How do I find alien?  Synaptic says it is installed, but where?

---

### Post by Russty of Oz on 2006-05-27
[QUOTE=patrick295767]Have a look to my script multimedia.sh to configure your codecs ... easily !!
  (in my signature) 
  
Greetz !![/QUOTE]
 
I will have to try that one later, as Firefox says it cannot find your server!?

---

### Post by Bagnaj97 on 2006-05-28
[QUOTE=Russty of Oz]How do I find alien?  Synaptic says it is installed, but where?[/QUOTE]

alien is a command line tool. Open a terminal and type ```
sudo alien xmms-wma-1.0.5-1.i386.rpm
``` to make a .deb file. Then you use ```
sudo dpkg -i xmms-wma_1.0.5-2_i386.deb
``` to install it. Now xmms can play WMAs

---

### Post by richbarna on 2006-05-28
[QUOTE=Bagnaj97]You can use xmms to play WMAs if you install xmms-wma. Download the RPM here [http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5-1.i386.rpm](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5-1.i386.rpm) and convert it to .deb using alien.[/QUOTE]

xmms is in the repositories, why convert an rpm?
> sudo apt-get install xmms

This should be ok with the win32codec

---

### Post by aktiwers on 2006-05-28
Do as patrick295767 says, I did it, and I can now play everything.

Dont get scared of the codes, its simply copy paste all the way.

---

### Post by richbarna on 2006-05-28
[QUOTE=aktiwers]Do as patrick295767 says, I did it, and I can now play everything.

Dont get scared of the codes, its simply copy paste all the way.[/QUOTE]

There you go, someone found a solution that works :)
That's what I love about this forum.

---

### Post by Bagnaj97 on 2006-05-28
[QUOTE=richbarna]xmms is in the repositories, why convert an rpm?[/QUOTE]

Xmms is in the repositories, but the xmms-wma codec isn't and for me at least xmms wont play wmas without it.

---

### Post by Russty of Oz on 2006-05-29
[QUOTE=Bagnaj97]alien is a command line tool. Open a terminal and type ```
sudo alien xmms-wma-1.0.5-1.i386.rpm
``` to make a .deb file. Then you use ```
sudo dpkg -i xmms-wma_1.0.5-2_i386.deb
``` to install it. Now xmms can play WMAs[/QUOTE]

When I type the first one in it says that the file does not exist.  I have it saved to a folder called Software.  I even copied it to the desktop, still no go!

???????

---

### Post by Perfect Storm on 2006-05-29
and you made sure you cd /where/the/file/is first?

---

### Post by Russty of Oz on 2006-05-29
[QUOTE=Artificial Intelligence]and you made sure you cd /where/the/file/is first?[/QUOTE]

Huh?  If it is in Home Folder what should I type in?

---

### Post by Perfect Storm on 2006-05-29
Then you can just use
```
cd
```
It takes you to the home folder.
Or if it's on your desktop
```
cd && cd Desktop
```

---

### Post by Russty of Oz on 2006-05-29
[QUOTE=Artificial Intelligence]Then you can just use
```
cd
```
It takes you to the home folder.
Or if it's on your desktop
```
cd && cd Desktop
```[/QUOTE]

Great.  Thanks for that!

---

