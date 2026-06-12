---
title: "why launcher is not launching gnu backgammon"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by nikosal on 2008-01-19
Hello, 
I just installed **gnu backgammon** through Synaptic. 
Small problems: 
a) Gnu Backgammon has not appeared in any "applications" window. Neither in "games", nor in anywhere else. Should I add it manually if I want to have it there? 
b) the only way to execute program, is using console. Initially I created a launcher (desktop icon pointing in usr/games/gnubg), but while it seems to start the program (start up window of gnu backgammon appears briefly and "welcome" sound heard), in less than a second both disappear/mute and application doesn't start
c) 3D view of application is very slow, checkers move veeeeery slow. In the same pc, in windows OS I don't have the same problem. I guess this is because I don't use vendor's graphics card driver...? (as it is not open source)

Any suggestion for any or all of the a-b-c above will be appreciated. 
Nikos

---

### Post by ryanVickers on 2008-01-19
run "glxgears" in the terminal...

if your framerate average for the 5 seconds is under a couple thousand I'd say you need different video drivers...

---

### Post by Majorix on 2008-01-19
Hi from Turkey ;)

a) Run alacarte from the terminal. There choose the appropriate menu and click "Add a new launcher" or whatever it is called. I am currently on Xubuntu so don't have alacarte :)
b) Look at above.
c) I would install the fglrx (for ati) or the nvidia drivers. They would speed up the graphics a lot.

---

### Post by nikosal on 2008-01-20
Ryan - Majorix thanks both of you for your time. 

@ Ryan: My frames were found 3840 using glxgears, so I guess this is not what causes the 3D problem.

@Majorix:** a - solved.** I didn't know about alacarte, that is fine now
b - not solved. I added gnu bg at menu / games, but when I try to launch it from there, occurs the same problem (of course) as when I try to launch it from the desktop launcher: Program will try to start, start up window appears briefly and then disappears. So still I can start it **only from console**. (As I said at message #1, I point launcher at usr/games/gnubg and I type the same at console, I guess this is correct, at least it would be correct if I was running windows). 
c - not solved. Initially I had installed the non open source graphics driver, as submitted by vendor, but I had problem starting ubuntu, so I removed it. Will try again. 

Thanks again
NIkos

---

### Post by mcduck on 2008-01-20
> **nikosal said:**
> . Initially I created a launcher (desktop icon pointing in usr/games/gnubg)
Are you sure you are using the right file to start the program? Executable files for programs are pretty much always located in /usr/bin.. Run 'which gnubg' to get path to the right file.

---

### Post by nikosal on 2008-01-20
> **mcduck said:**
> Are you sure you are using the right file to start the program? Executable files for programs are pretty much always located in /usr/bin.. Run 'which gnubg' to get path to the right file.

Sorry guys for insisting on this, but I would really like to understand it. 

I run "which gnubg" and yes, it is located at usr/games. Please see first attached picture. I remind you here that Synaptic installed the program for me, I didn't choose the installation directory. 

When I try to run program from the console, everything is fine. Please see second attached picture. 

When I try to run it from launcher, I have this half second appearance of start up window (see previous messages) and nothing happens. Please see third attached picture to see how I have configured launcher. 

My windows knowledge tells me that either console or launcher I am doing exactly the same thing. 

So what is wrong? 

Nikos

---

### Post by koleoptero on 2008-01-22
&#915;&#949;&#953;&#940; &#963;&#959;&#965; &#925;&#943;&#954;&#959; :) &#932;&#959; &#948;&#959;&#954;&#943;&#956;&#945;&#963;&#945; &#954;&#945;&#953; &#956;&#959;&#965; &#948;&#959;&#973;&#955;&#949;&#968;&#949; &#946;&#940;&#950;&#959;&#957;&#964;&#945;&#962; &#963;&#964;&#959;&#957; &#949;&#954;&#954;&#953;&#957;&#951;&#964;&#942; gnubg -w. &#916;&#959;&#954;&#943;&#956;&#945;&#963;&#941; &#964;&#959; &#954;&#945;&#953; &#960;&#941;&#962; &#956;&#959;&#965;. :)

---

### Post by nikosal on 2008-01-22
&#917;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974;!! Thanks koleoptero! 

The solution is to add -w after gnubg in launcher line.

---

### Post by diatondas on 2008-04-07
I run into the same problem and came across this thread.
I created a menu item with alacarte using gnubg -w switch and it works fine.

Many thanks for the solution koleoptero !

---

