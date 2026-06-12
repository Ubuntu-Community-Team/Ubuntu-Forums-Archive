---
title: "playing some commercial formats ( like mp3 )"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-02
I'm using Ubuntu 6.10. Can someone give me a link to a tutorial on installing plugins for Rythmbox or Totem player. Since i need to play some commercial formats. mp3 mostly, avi, and such.

---

### Post by viciouslime on 2007-01-02
Here you go: :) 

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

Use the command from the "how to make things work in a hurry" section and you can't go wrong.

---

### Post by Lord Illidan on 2007-01-02
Sure, and welcome to the forums.

[RestrictedFormats - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9")

---

### Post by Lord Illidan on 2007-01-02
> **viciouslime said:**
> Here you go: :) 

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

arggh..beaten by mere seconds!! ](*,)

---

### Post by viciouslime on 2007-01-02
> **Lord Illidan said:**
> arggh..beaten by mere seconds!! ](*,)

He he :p

---

### Post by Sasa_Ivanovic on 2007-01-02
thanks everyone!

---

### Post by spockrock on 2007-01-02
also check out easy ubuntu or automatix........

---

### Post by Sasa_Ivanovic on 2007-01-02
ok, a problem occured...
heres the screenshot
[http://img92.imageshack.us/img92/2186/screenshotyj0.png]("http://img92.imageshack.us/img92/2186/screenshotyj0.png")

---

### Post by viciouslime on 2007-01-02
Oh yeh, I should've mentioned that, if you read the bit above it should tell you that you need the multiverse and universe repos enabled. To do this, go to System/Administration/Software Sources and then tick the two boxes. :D

---

### Post by Sasa_Ivanovic on 2007-01-02
thanks again!

---

### Post by viciouslime on 2007-01-02
> **Sasa_Ivanovic said:**
> thanks again!

You're very welcome and welcome to Ubuntu!

---

### Post by Sasa_Ivanovic on 2007-01-02
i'm sorry to bring this up. But it still doesn't work for some reason. Here's the terminal output  :

```

sasa@sasa-desktop:~$ sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liba52-0.7.4 libdvdread3 libfaac0 libfaad2-0 libgsm1 libid3tag0 liblame0
  libmad0 libmms0 libmodplug0c2 libmp4v2-0 libmpcdec3 libmpeg2-4 libsidplay1
  libswfdec0.3 libwavpack0 libxine1 libxvidcore4 libxvmc1
Suggested packages:
  realplayer libdvdcss2 libdvdcss gxineplugin sidplay-base xsidplay libartsc0
Recommended packages:
  w32codecs
The following NEW packages will be installed:
  gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse gxine liba52-0.7.4 libdvdread3
  libfaac0 libfaad2-0 libgsm1 libid3tag0 liblame0 libmad0 libmms0
  libmodplug0c2 libmp4v2-0 libmpcdec3 libmpeg2-4 libsidplay1 libswfdec0.3
  libwavpack0 libxine-extracodecs libxine-main1 libxine1 libxvidcore4 libxvmc1
  ogle ogle-gui
0 upgraded, 30 newly installed, 0 to remove and 82 not upgraded.
Need to get 8905kB of archives.
After unpacking 23.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://mk.archive.ubuntu.com edgy/universe gstreamer0.10-ffmpeg 0.10.1-2ubuntu1 [1357kB]
Get:2 http://security.ubuntu.com edgy-security/main libxine1 1.1.2+repacked1-0ubuntu3.2 [3222kB]
Get:3 http://security.ubuntu.com edgy-security/universe libxine-main1 1.1.2+repacked1-0ubuntu3.2 [38.9kB]
Get:4 http://mk.archive.ubuntu.com edgy/universe gstreamer0.10-pitfdll 0.9.1.1+cvs20060515-1 [81.5kB]
Err http://mk.archive.ubuntu.com edgy/universe gstreamer0.10-pitfdll 0.9.1.1+cvs20060515-1
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Get:5 http://mk.archive.ubuntu.com edgy/main libgsm1 1.0.10-13 [28.1kB]        
Get:6 http://mk.archive.ubuntu.com edgy/universe libmms0 0.2-7 [20.5kB]        
Get:7 http://mk.archive.ubuntu.com edgy/main libmpcdec3 1.2.2-1 [25.3kB]       
Get:8 http://mk.archive.ubuntu.com edgy/main libmad0 0.15.1b-2.1 [76.9kB]      
Get:9 http://mk.archive.ubuntu.com edgy/universe libswfdec0.3 0.3.6-2ubuntu2 [272kB]
Get:10 http://mk.archive.ubuntu.com edgy/universe libwavpack0 4.32-2ubuntu2 [70.7kB]
Get:11 http://mk.archive.ubuntu.com edgy/universe gstreamer0.10-plugins-bad 0.10.3+cvs20060918-0ubuntu1 [436kB]
Get:12 http://mk.archive.ubuntu.com edgy/multiverse libmp4v2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 [214kB]
Get:13 http://mk.archive.ubuntu.com edgy/multiverse libfaac0 1.24clean-0ubuntu4 [55.2kB]
Get:14 http://mk.archive.ubuntu.com edgy/multiverse libfaad2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 [198kB]
Get:15 http://mk.archive.ubuntu.com edgy/multiverse libxvidcore4 2:1.1.0-final-0.1ubuntu1 [202kB]
Get:16 http://mk.archive.ubuntu.com edgy/multiverse gstreamer0.10-plugins-bad-multiverse 0.10.3+cvs20060918-1 [62.5kB]
Get:17 http://mk.archive.ubuntu.com edgy/universe liba52-0.7.4 0.7.4-3 [26.2kB]
Get:18 http://mk.archive.ubuntu.com edgy/universe libdvdread3 0.9.6-3ubuntu1 [55.0kB]
Get:19 http://mk.archive.ubuntu.com edgy/main libid3tag0 0.15.1b-8 [34.9kB]    
Get:20 http://mk.archive.ubuntu.com edgy/universe libmpeg2-4 0.4.0b-4ubuntu1 [61.9kB]
Get:21 http://mk.archive.ubuntu.com edgy/universe libsidplay1 1.36.59-4 [65.9kB]
Get:22 http://mk.archive.ubuntu.com edgy/universe gstreamer0.10-plugins-ugly 0.10.4-0ubuntu3 [203kB]
Get:23 http://mk.archive.ubuntu.com edgy/multiverse liblame0 3.96.1-2 [187kB]  
Get:24 http://mk.archive.ubuntu.com edgy/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.4-2 [38.3kB]
Get:25 http://mk.archive.ubuntu.com edgy/main libmodplug0c2 1:0.7-5 [115kB]    
Get:26 http://mk.archive.ubuntu.com edgy/main libxvmc1 2:1.0.2-0ubuntu2 [12.1kB]
Get:27 http://mk.archive.ubuntu.com edgy/main gxine 0.5.7-1ubuntu6 [278kB]     
Get:28 http://mk.archive.ubuntu.com edgy/multiverse libxine-extracodecs 1.1.2-0ubuntu2 [1146kB]
Get:29 http://mk.archive.ubuntu.com edgy/universe ogle 0.9.2-5 [247kB]         
Get:30 http://mk.archive.ubuntu.com edgy/universe ogle-gui 0.9.2-4 [76.4kB]    
Fetched 8824kB in 3m51s (38.2kB/s)                                             
Failed to fetch http://mk.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515-1_i386.deb  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
sasa@sasa-desktop:~$ 
sasa@sasa-desktop:~$ 

```

---

### Post by Lord Illidan on 2007-01-02
You probably have a bad sources.list or else your repository mirrors are not working.

Can you post your /etc/apt/sources.list here?

---

### Post by Sasa_Ivanovic on 2007-01-02
there
```


deb http://mk.archive.ubuntu.com/ubuntu/ edgy main multiverse restricted
deb-src http://mk.archive.ubuntu.com/ubuntu/ edgy main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mk.archive.ubuntu.com/ubuntu/ edgy-updates main multiverse restricted
deb-src http://mk.archive.ubuntu.com/ubuntu/ edgy-updates main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://mk.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://mk.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mk.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://mk.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by spockrock on 2007-01-02
try doing this,

sudo apt-get update and then do the sudo apt-get install.....

---

### Post by Lord Illidan on 2007-01-02
> **spockrock said:**
> try doing this,

sudo apt-get update and then do the sudo apt-get install.....

After that, if it still doesn't work, edit your /etc/apt/sources.list file gedit, and rename the links leaving it out the mk. Like this :

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by Sasa_Ivanovic on 2007-01-02
I don't know what that does. But it's a miracle, 'cause know everything works!
I really appreciate it!

---

### Post by Lord Illidan on 2007-01-02
> **Sasa_Ivanovic said:**
> I don't know what that does. But it's a miracle, 'cause know everything works!
I really appreciate it!

What don't you know?

---

### Post by Sasa_Ivanovic on 2007-01-02
> **spockrock said:**
> 
sudo apt-get update and then do the sudo apt-get install.....

You know i just started learning linux this very day, so i gues i can't understand it right now. But i don't care as long as it works.
Also i was programming in C++ and Java in windows so i have some basic knowladge ( or what it's spelled ).

Anyway thanks.:KS

---

### Post by Lord Illidan on 2007-01-02
> **Sasa_Ivanovic said:**
> You know i just started learning linux this very day, so i gues i can't understand it right now. But i don't care as long as it works.
Also i was programming in C++ and Java in windows so i have some basic knowladge ( or what it's spelled ).

Anyway thanks.:KS

That's cool, for a beginner. I am not ashamed to tell you that I screamed like a baby when I found out that I had to use terminal commands in Linux.

But it's actually quite easy. And google or searching this forum will take care of a lot of your problems.

About the apt-get, look at this : [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

---

