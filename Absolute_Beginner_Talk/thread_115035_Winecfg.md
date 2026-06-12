---
title: "Winecfg???"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by nu2this on 2006-01-09
I used Automatix originally to install Fx1.5, & in the process I got Wine which I was thinking of installing anyway. In the Automatix sticky thereis this line:

U need to run winecfg manually after install

What exactly does that mean? How is that done, is it done thru terminal?

---

### Post by lha on 2006-01-09
You got it right, open a terminal: Applications -> Accessories -> Terminal. Type winecfg and press enter. It will open up a program that lets you configure some settings for wine, this like what parts of your filesystem programs run with wine see.

---

### Post by nu2this on 2006-01-10
OK, I did that & got this:

     fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

On the dialog box for audio selected the OSS then r clicked the configure then clicked the OK. What if anything needs to be done next?

---

### Post by lha on 2006-01-13
[QUOTE=nu2this]OK, I did that & got this:

     fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

On the dialog box for audio selected the OSS then r clicked the configure then clicked the OK. What if anything needs to be done next?[/QUOTE]

That fixme tells you don't have jack installed. Jack is am alternative to OSS, ALSA and ESD. (It makes sounds work.) As long as sounds work as you want, there's no need to care about that fixme. (And usually not even when your sound doesn't work as you want.) Just try if you are able to use your Windows apps. I have had no need for further configuration of Wine.

---

### Post by rigsnet on 2006-01-17
doing better than me... i installed automatix. went to run winecfg in the terminal... and... command not found.

---

### Post by mustang on 2006-01-17
[QUOTE=rigsnet]doing better than me... i installed automatix. went to run winecfg in the terminal... and... command not found.[/QUOTE]

This may sound trivial but you did install wine through automatix right? You're not mistakenly assuming automatix autoinstalled everything for you?

---

### Post by Shampyon on 2006-03-21
[QUOTE=rigsnet]doing better than me... i installed automatix. went to run winecfg in the terminal... and... command not found.[/QUOTE]

I think it has something to do with the version of wine that Automatix is trying to access isn't the right one. Basically, you just bypass wine in Automatix, and get it thorough apt-get:

**sudo apt-get install wine**

Then type winecfg to set it up.

I had sound problems, getting this error:

[B][myusername]@ubuntu:~$ winecfg
ALSA lib seq_hw.c:455snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/user/.kde/socket-ubuntu.
can't create mcop directory[/B]

So you enter:
**sudo modprobe snd-seq**
to get rid of that first error.

Then you make that missing link yourself:
**mkdir -p ~/.kde/socket-<hostname>**
Hostname's whatever you entered as your hostname when you installed Ubuntu. It's ubuntu by default , so for most people it'll be:
**mkdir -p ~/.kde/socket-ubuntu**

Now you might get an error like this:
[B][myusername]@ubuntu:~$ winecfg
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack[/B]

From what I gather, it's only a problem if you use Jack for your sound. You're far more likely to be using ALSA or OSS, so unless you have problems when using your Windows apps, you should be fine.

---

### Post by tchoklat on 2006-11-05
I have installed wine thru automatix, and come to the winecfg.

Typing winecfg into a terminal I get the config applcation but how do I do the following after installing DVD Shrink3.2?

In winecfg be sure to turn on "show dots" for this application or the browse folder dialog box will hang
(as per the winehq website)

and,

[FONT=verdana][SIZE=2]Add the following lines to ~/.wine/config:
[AppDefaults\\DVD Shrink 3.2.exe\\Version]
  "Windows"="win2k" 
(as per frankscorner.org)

or do I need to do this?

Tony
[/SIZE][/FONT]

---

