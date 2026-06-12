---
title: "rhythmbox unable to import mp3"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by davidcrandle on 2006-03-06
This may be a very basic question.. but i have the 6.04 dapper drake beta... with rhtyhmbox and rhythmbox comes up with the error:
The file is not an audio stream.
when i try to import mp3 files.
the mp3 files are on an ntfs hdd, but i can access the files and play them through xmms.. but i prefer rhythmbox.

Thanx

---

### Post by engla on 2006-03-06
Basically, MP3 support is not included in Ubuntu because that file format is not *free*.

The general information & howto link is this:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by ericsk on 2006-03-06
[QUOTE=davidcrandle]This may be a very basic question.. but i have the 6.04 dapper drake beta... with rhtyhmbox and rhythmbox comes up with the error:
The file is not an audio stream.
when i try to import mp3 files.
the mp3 files are on an ntfs hdd, but i can access the files and play them through xmms.. but i prefer rhythmbox.

Thanx[/QUOTE]

You can try to install **gstreamer0.10-ffmpeg** and **gstreamer0.10-plugins-ugly**. 
It will make your rhythmbox recognizes the MP3 files.

---

### Post by aysiu on 2006-03-06
It seems odd that XMMS would play MP3 but Rhythmbox wouldn't.

---

### Post by davidcrandle on 2006-03-06
thanx.. i got the files.. but what exactly is the install comand.. i'm using:

davidcrandle@ubuntu:~$ install /home/davidcrandle/desktop/gstreamer0.10-ffmpeg install: missing destination file operand after `/home/davidcrandle/desktop/gstreamer0.10-ffmpeg'

but thats not working.. and the files are on the desktop...

thanx for the help so far

---

### Post by Sutekh on 2006-03-06
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly
```

No need to go and get them yourself, let apt-get do the leg work for you

Have a read of this link [http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php") (Section 1)

---

### Post by morguns on 2006-03-07
[QUOTE=Sutekh]```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly
```

No need to go and get them yourself, let apt-get do the leg work for you

Have a read of this link [http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php") (Section 1)[/QUOTE]
i get the following error:```
$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.10-ffmpeg
```do i need to update sources and/or do something with the universe? i'm new to linux, any and all help appreciated. i'm checking out the psychocats link now, looks like great information!

edit: i just updated rhythmbox to 0.9.2 to get podcasts functionality working.

---

### Post by morguns on 2006-03-07
after reading [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php) i checked /etc/apt/sources.list (comments left out for brevity):
```
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```i'm no expert here, but it looks like universe and multiverse are already there. are gstreamer0.10-ffmpeg and gstreamer0.10-plugins-ugly in a repository that's not covered here? if so, how would someone (me!) know where exactly??

---

### Post by Sutekh on 2006-03-07
After you change the sources.list, do a
```
sudo apt-get update
```
Then try installing them

The plugins are there in universe

[http://packages.ubuntu.com/dapper/libs/gstreamer0.10-plugins-ugly]("http://packages.ubuntu.com/dapper/libs/gstreamer0.10-plugins-ugly")

[http://packages.ubuntu.com/dapper/libs/gstreamer0.10-ffmpeg]("http://packages.ubuntu.com/dapper/libs/gstreamer0.10-ffmpeg")

---

### Post by morguns on 2006-03-07
thx Sutekh, but i'm not following. the sources.list info i pasted was ALREADY there, i did NOT have to modify it. therefore, no need to do "sudo apt-get update". just to make sure though, i went ahead and ran "sudo apt-get update" and then tried the install again: no joy, same error. so my question is why did ```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly
```fail? if the sources.list file is right (is it?), do i have another problem? after looking at my sources.list file, do i have the necessary references/repositories there?

i clicked on the links you gave, and they take me to pages with a whole lot of info that is greek to me. i thought maybe i'd find a .deb file i would run sudo dpkg -i on, but not even that. what can i do next? thx for the help, i really appreciate it.

---

### Post by Sutekh on 2006-03-07
[QUOTE=morguns]after reading [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php) i checked /etc/apt/sources.list (comments left out for brevity):
```
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```i'm no expert here, but it looks like universe and multiverse are already there. are gstreamer0.10-ffmpeg and gstreamer0.10-plugins-ugly in a repository that's not covered here? if so, how would someone (me!) know where exactly??[/QUOTE]
Ah! So obvious I couldn't see it.  The original poster was using Dapper 6.04, not Breezy 5.10 which you are.  You *can* get those packages f you want, but it'd probably cause more problems.  You should realy just follow the Breezy applicable instructions here.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

To play MP3's you need this
```
sudo apt-get install  gstreamer0.8-mad
```

---

### Post by morguns on 2006-03-07
Sutekh, you da man!! (or woman, whichever the case may be lol) gstreamer0.8-mad did the trick! woot!! i completely missed the fact that i was replying to a dapper thread. i've been scouring these forums and came across several threads, just assumed i'd stuck with one that focused on breezy. thx VERY much for the info!! podcasts are working like a champ in rhythmbox now, sweet!! i'm just making the switch to linux and i must admit it's a humbling experience. would you happen to know why an mp3 cd is not recognized by breezy? sorry to toss this out like this, i haven't even looked for an answer yet. it's one of the things on my to-do list.

---

### Post by Sutekh on 2006-03-07
Its okay I almost missed the fact that you were a different poster, because I knew the OP was using Dapper.  Glad its working.  

An MP3 CD?  Recognised in what way?  As in the CD isn't recgnised and you can't browse it?  Or the CD isn't recognised you can't add it to your rhythmbox playlist?

---

### Post by morguns on 2006-03-07
i insert the cd, ubuntu doesn't mount it or otherwise recognize it, and i can't browse it at all. fwiw, normally the eject button doesn't work, i have to right-click the icon on the desktop to eject, but this mp3 cd (burned with itunes in winxp) isn't recognized at all.

---

### Post by The Warlock on 2006-03-07
[QUOTE=morguns]i insert the cd, ubuntu doesn't mount it or otherwise recognize it, and i can't browse it at all. fwiw, normally the eject button doesn't work, i have to right-click the icon on the desktop to eject, but this mp3 cd (burned with itunes in winxp) isn't recognized at all.[/QUOTE]

It, um, shouldn't act like that. You sure it isn't scratched?

---

### Post by morguns on 2006-03-08
looks like i was just being impatient, came back from eating some dinner and all was well.

---

### Post by Sutekh on 2006-03-08
That's totally wierd, but if it works...

---

### Post by xplode_me on 2006-03-09
[QUOTE=ericsk]You can try to install **gstreamer0.10-ffmpeg** and **gstreamer0.10-plugins-ugly**. 
It will make your rhythmbox recognizes the MP3 files.[/QUOTE]


Thanks ALOT! :) Now my rhythmbox is working.. FINNALY! :D

10x again! ;)

---

### Post by landotter on 2006-03-14
w00t! I needed the ugly! that did it. 

:D 

Otherwise, Dapper's been flawless for me. :up:

---

### Post by Klejs on 2006-03-15
Thanks for the help **engla**!!

---

### Post by paritybit on 2006-04-22
as a side note. I had to do
```
sudo gst-register-0.8
```
after i installed the necessary stuff.

---

