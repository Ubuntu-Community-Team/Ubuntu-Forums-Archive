---
title: "Hmm...Dual Monitor probs"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Le_Petit_Lapin on 2007-08-30
Just installed Ubuntu, alongside Vista, wanted to have a look at Cadega and see if I can get EVE-Online, Teamspeak etc running under Linux.....for a laugh. : /

Anyway, installation of Ubuntu was fine...easy even, some notification popped up saying I needed to get some updates....done that and re-booted, and then came to my first problem. My second monitor wasnt working, or if it was working, it looked like a 8bit arcade game mixed with a bad acid trip. 

Sooo....driver problem I assumed. Clicked about a few things to see if there was some driver-updater program in Ubuntu, didnt find one, so went a grabbed the drivers off NVidia website. Downloaded them....and....oh....damn, you cant just double click them. :( I need a shell prompt dont I for that, according to the instructions on NVidia site anyway. Failed to find that as well. :oops:

Wondered what to do. Tried clicking Desktop Effects. Ah! Its asking me to install a restricted driver! Sounds good to me! Went ahead and done that, and re-booted......and now the xserver doesnt start up. I get a lovely black screen. Reboot into Vista, see someone else is having this problem, and that I need to start in "text mode" and type "sudo dpkg-reconfigure -phigh xserver.org". Do that, go through it, and type startx.

Yay! Graphics have returned.....but wait....whats going on here? Now my second monitor is being used as my display and my main monitor isnt working...Arrrgghh....but at least I have got the right resolution on my second monitor!

So...... the questions:

How do I get it to display on my main monitor again? 
How do I get both monitors working together?
Can I have a different resolution on each monitor? (Needs to be 1680x1050 on main, and 1440x900 on second)
Can my desktop be expanded onto the second monitor, even though its at a different resolution, and if so, how do I do this? 

:)

---

### Post by derekr44 on 2007-08-30
Do you have TwinView working?  Might want to check this thread out.

[http://ubuntuforums.org/showthread.php?t=537717&highlight=twinview](http://ubuntuforums.org/showthread.php?t=537717&highlight=twinview)

Also, run > sudo apt-get install nvidia-settings in terminal.  nVidia Settings allows you to work with your TwinView settings from a GUI.

---

