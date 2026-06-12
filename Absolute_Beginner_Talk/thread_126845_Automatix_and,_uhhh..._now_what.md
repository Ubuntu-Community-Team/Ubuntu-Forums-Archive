---
title: "Automatix and, uhhh... now what?"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by Mike_SMD on 2006-02-07
Hello everybody.
I'm a newbie who's just three hours old, and confused as all sin itself. I'm working on learning, but frazzled by the mystical esoterism of the command shell... I just need an answer to the following question (which I'm going to have to put into plain language as at this point I haven't quite acquired the knack of speaking in linux).

I installed what I assume is the most recent version of Ubuntu, the one with the Gnome desktop. Naturally I haven't the slightest clue how one checks a version number yet. I have an ATI Radeon 9500 Pro graphics card. How do I enable 3D support?

I ran the 'automatix' thing (not sure if it counts as a 'script' or a 'program' or if there's any difference between the two terms yet) thinking that might do it but nothing seems to have changed. Oh! I'm basing this observation on that 'gears' screensaver which seems to be stuck at running a choppy fifteen or so frames per second... and looks suspiciously hardware rendered to me. If I'm wrong about that just let me know how to check or what the easiest way for a complete virgin is to modify their graphics settings.

What I need is a front end of some kind that allows one to set whatever it is that needs to be set... see? That's more or less where I've gotten so far. I need a thing to do some thing that I only vaguely think might be worth doing because all the other stuff that is probably more important and useful both sounds like greek and is sort of frightening. No offense to the greeks.

If this sounds like you six months ago... well, take pity and please give me a hand.

Thanks in advance,


Mike_SMD.

---

### Post by kaamos on 2006-02-07
Hello!
Here are instructions how to install the ati driver from ubuntu repositories [http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)

You can use this command to check your 3d
```
glxgears -printfps
```
Over 1000 is good, I get ~2000 with mobility radeon 9000.

Hope this helps!

---

### Post by welsh_spud on 2006-02-07
You say that you have used automatix to try and get your graphics card up and running. Just to double check, in Automatix select item number 38. Once it has worked its magic, you will need to restart your computer.

Once you have checked you have done that, run **glxgears -printfps** in the command line. This will just test if you have hardware acceleration

---

### Post by Sutekh on 2006-02-07
[QUOTE=Mike_SMD]
I ran the 'automatix' thing (not sure if it counts as a 'script' or a 'program' or if there's any difference between the two terms yet) thinking that might do it but nothing seems to have changed. 

...

What I need is a front end of some kind that allows one to set whatever it is that needs to be set... see? That's more or less where I've gotten so far. [/QUOTE]

This makes me think that you have only installed Automatix, but haven't yet run it.  If you had you should have seen a big front end asking you to choose which options for Automatix to install.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=3210&d=1130474279[/IMG]

To get this go to the Applications -> SYstem Tools Menu and Choose Automatix, OR press **Alt**+**F2** and type in **automatix** to run the program.  Then you can chooose the options that you want installed.  Including (as suggested by **welsh_spud**) option #38 for ATI drivers.

---

### Post by Mike_SMD on 2006-02-07
Sorry, I should have been more clear there... I did run the program and I did come across that screen. Also, checked off the option for the ati drivers.

Been reading the advice here ([http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)) and this is the output I keep getting from the terminal:

mike@ubuntu:~$ glxgears -printfps
923 frames in 5.5 seconds = 166.577 FPS
840 frames in 5.2 seconds = 160.833 FPS
840 frames in 5.2 seconds = 160.410 FPS
840 frames in 5.3 seconds = 159.175 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
mike@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


I also tried editing my xorg.conf file so that it uses 'fglrx' instead of 'ati' in the section labelled driver. Doesn't seem to have done much. I restarted X using the control-alt-backspace right after this was done. 

Are there any other diagnostic tools or tips that you folks have to offer? As you might have guessed, considering that I'm learning the command line pretty much as we go along I don't have even the slightest clue as to what to try next.

Thanks for everything so far,


Mike.

---

### Post by Mike_SMD on 2006-02-07
Ok... 
Things aren't exactly going along all that great and I'm going to end this thread and begin again. I think that the heading is keeping folks from checking it out to offer advice (though all hearty thanks to those who have so far) and right now I need all of it that I can handle.

Thank you all so very much for the time you've invested so far, I begin this post again with some more description to it...

NOW!


Mike_SMD

---

### Post by Sutekh on 2006-02-07
There is a separate section on the Forums for AUtomatix.  You might get more help if you posted there.  Especiallyafter reading this new thread from arnieboy

[http://ubuntuforums.org/showthread.php?t=126926]("http://ubuntuforums.org/showthread.php?t=126926")

---

