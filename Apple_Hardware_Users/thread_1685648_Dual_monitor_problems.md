---
title: "Dual monitor problems"
date: 2011-02-11
forum: Apple Hardware Users
---

### Post by GLMantra663 on 2011-02-11
Hello all. Im extremely new to linux, and the forum so bare with me. I just installed ubuntu 10.10 on my mbp 7,1 and i love it. I have just run into one little problem that i cant seem to find a fix for im hoping someone can help. 

I used my vizio tv as a second monitor under osx, mainly just for watching shows and movies because I lack a cable outlet in my room, and i would like to do the same in ubuntu. But i can not find any sort of instructions on how to set up a second monitor.

I go to system>preferences>monitors when i click on that i get this:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

I click yes and it opens NVIDIA X Server Settings
Go to Display Configuration and in the layout area i see that its acknowledging a second display but its saying that its disabled. I am using Compiz but i wouldnt know if that has something to do with it.

How do i enable it and set it up so that the TV is my second monitor and i can drag windows between the two screens as i did in osx?

---

### Post by linuxopjemac on 2011-02-11
maybe you have to disable compiz first

---

### Post by GLMantra663 on 2011-02-11
I just disabled compiz and tried to set up the monitor again. Still didn't work. Its not really a big deal though. I still have a small osx partition on my drive so i can just reboot into that when i want to watch something. Which probably wont be much because im spending most of my free time messing around in ubuntu!

!:D!

---

### Post by oknoproblem on 2011-02-11
Hey GLMantra663, you're going to need twinview. The instructions can be found here: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
Cheers :D

---

### Post by nevius on 2011-02-13
It's fairly easy to set up twinview. The steps are as follows (as best I can remember it).

Do the following with the TV connected:
1) Open Terminal
2) Type "sudo nvidia-xconfig"
3) Type "sudo nvidia-settings"
4) Switch the setup to "twinview" using the nvidia-settings GUI.
5) Apply the settings and save them to the xorg.conf.

Sorry I can't be more precise on some of the steps. I'm currently too lazy to google it :)

---

### Post by GLMantra663 on 2011-02-16
thanks nevius! The tv is actually showing output! But my resolution is all shotty and it doesn't allow me to set the resolution to anything higher than 640x480 even though the tv screen is much larger than the screen on my laptop.

---

