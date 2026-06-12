---
title: "Can one person help me do just one task"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-03-11
It seems that I can't get anything that didn't automatically work to work in this OS.  I've been reading the manuals/help files.  Nothing seems to work.

For instance, how do I use the CD command to change directories.

If I use the ls command, I see to directories, one with my user name 'caruso' and the other 'desktop'

I cannot cd to either of those, and no other directories show up.

How would I get to 'home' for example.

How to find my software in a way that i can make it run?

I know linux in any flavor cannot be this difficult.

is there someone out there willing to show me some very very basic steps so i can get started?

Thanks.

Caruso

---

### Post by heathguy on 2007-03-11
Hey man..Stick in there

This site is great for useful commands on getting started in the wide world of linux

[ http://www.linux.org/lessons/ ]( http://www.linux.org/lessons/ )

---

### Post by igknighted on 2007-03-11
Linux is case sensitive... therefor cd desktop wont do anything.  You need cd Desktop.  Also, to show the files in that directory use "ls".  This is the rough equivelent of "dir" in dos.  As for launching programs, almost anything you install is in /usr/bin.  To launch it you just need to type the program name in, you don't need to cd there.  Sometimes a program installed manually will end up in /opt or /usr/local/bin, in which case you need to append the path to the command to run the program.  For instance, if I want to launch Gaim from the terminal I just type "gaim" and it launches, but if I want to launch Swiftfox (it's in /opt) I need to use "/opt/swiftfox/swiftfox".

---

### Post by Detonate on 2007-03-11
One of my favorite places:

[http://www.chongluo.com/books/rute/](http://www.chongluo.com/books/rute/)

---

### Post by Erlander on 2007-03-11
Most applications you have installed will show up in the "Applications" menu on the top left of your screen.

Rob

---

### Post by IYY on 2007-03-11
> It seems that I can't get anything that didn't automatically work to work in this OS. I've been reading the manuals/help files. Nothing seems to work.


Don't give up, the learning curve is steep, but not too long.

> For instance, how do I use the CD command to change directories.

If I use the ls command, I see to directories, one with my user name 'caruso' and the other 'desktop'

I cannot cd to either of those, and no other directories show up.


It's case sensitive. Desktop is uppercase, so you would use

```
cd Desktop
```

> How would I get to 'home' for example.

If you mean your home directory, it should be the default place where you start when you launch a terminal. You can also get to it with

```
cd
```

or


```
cd ~
```

If you mean the location /home, where all the home directories are stored, you can get to it by typing

```
cd /home
```

or, if you are currently in your home directory and just want to go one step up:

```
cd ..
```

> How to find my software in a way that i can make it run?

The Add/Remove Programs is the easiest way to install software. It's in your Applications menu. Another way is Synaptic, located in System > Administration > Synaptic.

---

### Post by carusoswi on 2007-03-11
Heathguy:
Thanks.  That was helpful.  At least I can navigate my directories, now.  That program ecasound is nowhere to be found as a program on my drive.  I can find the package, but no file that appears to be a running file.

Don't know how to figure that out.

I downloaded audacity, it runs, but complains that I have no audio device.  That's strange since ubuntu is playing through my audio card just fine.

Caruso

---

### Post by SishGupta on 2007-03-11
ecasound is a command line application
to run it you have to open a terminal and type 'ecasound' and hit enter.

Unfortunately i don't think ecasound is what you really want. It seems rather hard to use because of the command line interface.

When installing programs I always check the description to see if it is command line or GUI.

---

as for audacity, you need to change the sound playback and recording driver to ALSA (instead of OSS which is default)

edit>preferences
on the audio IO tab, playback>device drop down menu>ALSA (pick the first ALSA is you have more than one)

same for recording.

ESD has trouble with more than one track at a time, ALSA is much more robust and can handle a lot more.

---

