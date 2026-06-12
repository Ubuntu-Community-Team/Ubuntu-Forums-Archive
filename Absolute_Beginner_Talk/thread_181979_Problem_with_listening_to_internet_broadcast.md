---
title: "Problem with listening to internet broadcast"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by superwurm on 2006-05-25
Hi, I've just installed Kubuntu Draper or something like that
most stuff works fine but I got a few things that I can't figure out

If I want to listen to internet broadcast (with Amarok) I hear nothing allthough he says that he's playing, I also see the playlist and stuff like that
it's in MP3 format (shoutcast)

and if I wanna see video's on websites in windows media format, I see only black pictures with no sound. Is that usual (caus it's windows) or do I need to install anything?

---

### Post by superwurm on 2006-05-25
by the way
yes I've checked kmix allready en all the sound settings where on

I've the feeling that it has something to do with codex maybe
when I tried to rip a CD I got a message about codex, but when I checked I saw that I have them, so what's the problem? But anyway, I couldn't rip them

---

### Post by nalmeth on 2006-05-25
Check out the bumps multimedia script, to install codecs and to install the mplayer-mozilla plugin. Are you certain you installed Dapper?

---

### Post by superwurm on 2006-05-25
[QUOTE=nalmeth]Check out the bumps multimedia script, to install codecs and to install the mplayer-mozilla plugin. Are you certain you installed Dapper?[/QUOTE]Yeah I think so
I downloaded dapper live i386
If I browse the CD and I check the readme file, it says "DISKNAME  Kubuntu 6.06 "Dapper Drake" - Alpha i386"
But if I put the disc in my windows machine I get a Ubuntu 5.10 discscreen

Ny the way, I have Konqueror webbrowser. I couldn't get Firefox installed
and I try to listen with Amarok, but I hear no sound

and if I rip a CD, it is able to rip in wave, but not in MP3
allthough I sellected the lame encoder in the settings

---

### Post by superwurm on 2006-05-25
[QUOTE=nalmeth]Check out the bumps multimedia script[/QUOTE]
Where is this Bumb multimedia script? Or do I first have to install it?

---

### Post by nalmeth on 2006-05-25
I'm confused.

If you're certain it's dapper you installed, check out the [bumps multimedia script]("http://ubuntuforums.org/bumps%20multimedia%20script")

If you've installed breezy 5.10 then you want automatix.

---

### Post by superwurm on 2006-05-25
[QUOTE=nalmeth]I'm confused.
If you've installed breezy 5.10 then you want automatix.[/QUOTE]
thnx I'll try the script

Automatiks didn;t work. I tried it before, but after I sellected everything, and started it, it didn't go anyfurther than 0%

---

### Post by superwurm on 2006-05-25
where can I actualy download that bumps file? I've seen allready 3 different pages where they talk about this Bumps project and for download they recoment eachother. But where can I get the file?

---

### Post by superwurm on 2006-05-25
nevermind, I found the tar (thnx google)

---

### Post by superwurm on 2006-05-25
well, I tried the script
this was the result:

gnome-terminal: No such file or directory
gnome-terminal died with exit status 1
./bumps: line 9: zenity: command not found
./bumps: line 78: zenity: command not found

I don;t have Gnome, I've KDE

---

### Post by nalmeth on 2006-05-25
ok, did you extract the tarball somewhere on your /home folder?
You can do this graphically, just right-click and extract.
I believe you can then just double-click the bumps executable.

For the terminal route, you browse to the folder it's in, if you put it on your desktop, and run the executable.

```
cd /home/superwurm/Desktop/bumps
./bumps
```

---

