---
title: "stepmania menu troubles"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Statik on 2007-07-07
Hi all,

I've downloaded and installed stepmania in Feisty and it works great . . . if I browse to it in Nautilus or if I execute it in terminal. I'm trying to get it to run from a menu tho, and it just doesn't start. I'm not sure what I'm doing wrong.

The command run from terminal is /home/statik/.stepmania/StepMania-3.9/stepmania and this is the same command in the menu. I tried telling the menu to run it as 'Application in Terminal' and I can see the terminal pop up for a split second. I tried to print-screen it to see what it is saying, and it says it cannot find a sound-driver that works. 

Any ideas?

Rod

---

### Post by AJB2K3 on 2007-07-07
how did you achieve that?
I can't even get it to extract !

---

### Post by Statik on 2007-11-12
Well, I figured out what the problem is, but I don't know how to solve it.

I can now start stepmania from the menu. The menu command is: ```
sh -c "cd /home/statik/.stepmania/StepMania-3.9 && ./stepmania"
```

The problem is that when I click on an item in my menu, I have menu sounds turned on . . . you know, the little 'tik' when you click on the menu. Well, when stepmania starts it checks the sound system state and it finds that the system is still busy so it fails out. Is there a way to pause the start for say 1 second?

As for how I installed stepmania, there was an RPM that I ALIEN'd and installed. Worked fine. Great little program. I even have a step pad that I made from an old joystick and an old one piece stepper game that I got for $1.98 at a clearance sale. Too bad the old game is wired straight and the joystick is wired grid. I don't have the inclination to take this thing apart. Maybe I can build my own or something.

Statik

---

### Post by jeremiebergeron on 2007-11-23
I've gotten the same problem on my computer. Sometimes I need to close all of my open applications (including Firefox!) to free the sound driver. I haven't gotten the problem where I couldn't start it as a shortcut though. Usually I just have to close all other open programs (literally all!).

---

### Post by 99bluefoxx on 2007-12-03
just install he windows version through WINE, i use that one and its a LOT less hassle, works fine with wow, firefox, and many other apps running too
easire to install songs too, just open up you .wine directory
['-']
hope i could help
also, if your interested, i have found a way to modifey the step timing in the game too, makes it easire to play some songs
peace~

---

