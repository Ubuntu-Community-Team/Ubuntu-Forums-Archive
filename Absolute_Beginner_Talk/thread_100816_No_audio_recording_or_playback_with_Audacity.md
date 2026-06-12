---
title: "No audio recording or playback with Audacity"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by greymaus on 2005-12-08
I just installed the version of Audacity that's bundled with the new Ubuntu distro.  When I started it up I got the un-nerving message, "There was an error initializing the audio I/O layer. You will not be able to play or record audio."  No indication of what that error was, or what I can do to rectify it. 

An audio utility that can't play or record audio is of little use.

---

### Post by landotter on 2005-12-08
do you have another audio program running at the same time? Audacity is a little old fashioned and doesn't play nice with others. Close out all other audio apps and restart it.

Sometimes you need to kill the sound server in order for it to be happy, in a terminal, you'd type "killall esd" and press enter. If you're using Kubuntu make that "killall artsd" ;)

---

### Post by greymaus on 2005-12-08
No other systems open at the time, Landotter.  A "killall" command results in the message "No processes killed."  And I still can't record or playback thru Audacity.

---

### Post by Howitzer on 2005-12-11
I had the same problem.

Install the alsa-oss wrapper with synaptic.

Then open the console and type **aoss audacity**.

Information taken from [http://audacityteam.org/forum/forum.php?req=thread&id=35](http://audacityteam.org/forum/forum.php?req=thread&id=35)

EDIT:

Sorry, this doesn't work either.  Your only solution is to download the windows version of Audacity.

EDIT2:

Audacity 1.0.0 works fine with Wine.  Any version above that will have interface errors.

---

### Post by Mustard on 2005-12-11
I fixed this problem by setting up my system to use ALSA and disabling the sound server.

The options to do so are in the multimedia selector menu option and the sound menu option, both found in your System>>Preferences menu.

The problem is usually an ESD process running in the background (this relates to the sound server).

You could do this command to see if there is an esd process running,

```
ps -e | grep esd #this command list all processes running but only displays those that contain the letters 'esd'
```

To kill esd running in the background,

```
killall esd
```

---

### Post by BoyOfDestiny on 2005-12-11
[QUOTE=Mustard]I fixed this problem by setting up my system to use ALSA and disabling the sound server.

The options to do so are in the multimedia selector menu option and the sound menu option, both found in your System>>Preferences menu.

The problem is usually an ESD process running in the background (this relates to the sound server).

You could do this command to see if there is an esd process running,

```
ps -e | grep esd #this command list all processes running but only displays those that contain the letters 'esd'
```

To kill esd running in the background,

```
killall esd
```[/QUOTE]

I can verify this does the trick. I solved all my sound problems this way (since hoary), and I get to use hardware mixing (audigy2). Yay!

---

### Post by Howitzer on 2005-12-11
Yeah, that works! Unfortunately I lost my sound effects in the process.  Is there any way you can have both the sound effects and Audacity?

---

### Post by Mustard on 2005-12-11
[QUOTE=Howitzer]Yeah, that works! Unfortunately I lost my sound effects in the process.  Is there any way you can have both the sound effects and Audacity?[/QUOTE]

I havent managed to find a way yet.  I just live without the sound server.  I use skype quite a bit too and it doesn't play nice with other sound processes either, so all in all, I find the luxury of having sounds play for the different functions and alerts on ubuntu is something I can live without to make sure that my others apps function without any problems.

-edit-

When I sit and contemplate the issue, I suppose you could call those apps with a script of some kind that would shut down the sound server first and kill any background esd processes.  How you would write that script however I don't know. :)

Upon leaving the application though, there would still need to be some method of restarting the sound server afterwards.

I don't know the intricacies of ALSA and ESD, so I'm as much in the dark as anyone else in this regard.  I'm hopeful that at some future stage some hardworking open source software programmer will come up with the answer. ;)

---

### Post by Howitzer on 2005-12-11
Ah.  Well, I don't use Audacity every single day so I guess when I need it I'll just killall esd.  I also have Audacity 1.0.0 for Windows installed, and while it's older, it should fit my needs. (I had to download the lame_enc.dll to encode mp3)

Thanks for all the help :)

---

### Post by Zimmer on 2005-12-11
[QUOTE=Howitzer]Ah.  Well, I don't use Audacity every single day so I guess when I need it I'll just killall esd.  I also have Audacity 1.0.0 for Windows installed, and while it's older, it should fit my needs. (I had to download the lame_enc.dll to encode mp3)

Thanks for all the help :)[/QUOTE]

Easier still, 
Have a look here 
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)
and....
reconfigure esd at startup...

(the exact file is /etc/esound/esd.conf )

[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-as 5

make sure gstreamer defaults are set to alsasink and alsasrc .
Ensure system sounds is de-selected (as in previous posts here)
Audacity plays and records for me....and I am not using aoss audacity, either...

Zimmer

---

### Post by Howitzer on 2005-12-11
Good information!

To tell you the truth, this does fix a nagging problem I've been having with a few programs.

For example, XMMS will refuse to play a song because something else is blocking it.  This only happens (I've tested it) directly after clicking something that makes a sound effect.  Eventually it will play, but only after hitting play several times.  Disableing the sound server fixes it.  This same problem occurs in VLC, and even the Windows version of Audacity.

I can live without bells and whistles.

Thanks for the information!  I hope someone fixes this issue someday.

---

### Post by anil_robo on 2005-12-17
Good news!
 I have successfully recorded sound in Ubuntu few times just half an hour back! Read my post [here]("http://www.ubuntuforums.org/showthread.php?t=102377#6")

---

