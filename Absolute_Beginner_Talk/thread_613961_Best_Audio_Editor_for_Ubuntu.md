---
title: "Best Audio Editor for Ubuntu"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by AgHawke on 2007-11-15
Hi All:

I'm looking for a good Audio Editor that works in Ubuntu.I have tried to install Audacity,Sweep,Ubuntu Studio,Rezound with no luck. I haven't had much luck using Terminal ,or Synaptic, I either get no response or file not found. Any suggestions??

Thanks AgHawke

---

### Post by silent1643 on 2007-11-15
not sure what you looking to do but.. here are some

[http://zynaddsubfx.sourceforge.net/](http://zynaddsubfx.sourceforge.net/)
A opensource synthesizer capable of making a countless number of of instruments. Project started in 2002 and seems to be maintained up until 2005.

[http://www.hydrogen-music.org/](http://www.hydrogen-music.org/)
An advanced drum machine for GNU/Linux. It&#8217;s main goal is to bring professional yet simple and intuitive pattern-based drum programming.

[http://www.ardour.org/](http://www.ardour.org/)
Ardour is a digital audio workstation. You can use it to record, edit and mix multi-track audio. You can produce your own CDs, mix video soundtracks, or just experiment with new ideas about music and sound.

[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)
LMMS aims to be a free alternative to popular (but commercial and closed- source) programs like FruityLoops/FL Studio, Cubase and Logic allowing you to produce music with your computer. This includes creation of loops, synthesizing and mixing sounds, arranging samples, having fun with your MIDI-keyboard and much more&#8230;

[http://mixxx.sourceforge.net/index.php](http://mixxx.sourceforge.net/index.php)
Mixxx is an open source DJ tool designed for both professional and amateur DJs alike



any questions :D

---

### Post by rsambuca on 2007-11-15
Those audio editors pretty much will cover it.  What exactly is it that you are trying to do? My guess is that at least one of those methods will work!

---

### Post by AgHawke on 2007-11-15
Hi All:

The main reason I'm looking for good audio editors is that I do alot of electric voice phenomenon.I use at least two programs at any given time just to double check my work.As far as using the above listed programs I'm sure they are as good as any but my problem is trying to install them.I have tried using the sudo commands in terminal,and synaptic package manager with less than stellar results.So I would like to know what i'm doing wrong.

Thanks
AgHawke

---

### Post by rsambuca on 2007-11-15
> **AgHawke said:**
> Hi All:

The main reason I'm looking for good audio editors is that I do alot of electric voice phenomenon.I use at least two programs at any given time just to double check my work.As far as using the above listed programs I'm sure they are as good as any but my problem is trying to install them.I have tried using the sudo commands in terminal,and synaptic package manager with less than stellar results.So I would like to know what i'm doing wrong.

Thanks
AgHawke

What do you mean by "less than stellar results"?  Have you managed to install anything?  Or are you installing but they don't work?

---

### Post by Sawman on 2007-11-15
You didn't say which distro of Ubuntu your using, but I recommend 7.10 Studio  as it comes with these programs and are installed when you install the distro.

---

### Post by AgHawke on 2007-11-15
Hi All:

 Sawman I tried Ubuntu Studio 7.10 and it lock up on me, so I'm just not sure what to do or which version to install.

Thanks

AgHawke

---

### Post by AgHawke on 2007-11-15
Hi All:

Rsambuca I tried to install all the audio programs I stated in my original post.The only one to install was Audacity 1.3.3  it could play and do a few other tasks but wouldn't record.
I hope this clears up a few things.
thanks 

AgHawke

---

### Post by silent1643 on 2007-11-15
how are you installing a program?
what errors are you getting?
what type of system are you running this sh*t on?

:D

---

### Post by AgHawke on 2007-11-15
Hi All:

Silent the problem is the terminal and synaptic can't find,or install any of the above audio programs.

AgHawke

System is Ubuntu7.10

---

### Post by rsambuca on 2007-11-15
Then you need to activate your repositories.  Go to "System -> Administration -> Software Sources".  Make sure all of the boxes are checked and then try again.

---

### Post by AgHawke on 2007-11-16
Hi all:
 

 After updating Ubuntu I tried to install Audacity 1.2.6. Here is what I typed in terminal.
sudo  apt-get install audacity 1.2.6
read package list...done
building dependency tree
read state information
E:couldn't find Audacity

 What am I not doing to get this installed.

Thanks
AgHawke

---

### Post by rsambuca on 2007-11-16
You don't need the numbers in this case.```
sudo apt-get install audacity
```

---

### Post by AgHawke on 2007-11-16
Hi All

 Rsambuca I just ran your code ,this is what I got.

sudo  apt-get install audacity
read package list...done
build dependency tree
read state information...done
audacity is the newest version 0 upgrade 0newly installed,0 to remove and 0 not upgrades

AgHawke

---

### Post by rahimveron on 2007-11-16
You got that message bcoz you have already install the latest version of Audacity.

---

### Post by AgHawke on 2007-11-16
Hi All:

Well  Audacity,Sweep,Mhwaveedit are installed -how -don't know. My problem now is no sound to go with these programs, and is there an audio pkg that needs to downloaded as well?If so please let me know which one to download.

Thanks
AgHawke

---

### Post by jerrynewt on 2007-11-16
Go to Applications>Add/Remove. Ardour GTK2 is available for installation under the sound and video section. Looks like it might be what you are looking for.

---

### Post by Kundalinux on 2007-11-23
So which is better, ZynAddSubFX or LMMS?
I just want to easily create good quality tracks using drum beats and synthesized sounds, without going into too much trouble.

Thanks in advance :)

---

