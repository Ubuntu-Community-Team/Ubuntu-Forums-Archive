---
title: "Another install problem"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by KMW on 2007-05-06
After installing Feisty on a HDD when I try to boot it I receive an error.
 Failed to start X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
Have tried this on 2 different machines with the same result. One is a GF6100 and the other is a Compaq with an Intel 810 chipset.
Don't know what to do next!

---

### Post by igknighted on 2007-05-06
> **KMW said:**
> After installing Feisty on a HDD when I try to boot it I receive an error.
 Failed to start X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
Have tried this on 2 different machines with the same result. One is a GF6100 and the other is a Compaq with an Intel 810 chipset.
Don't know what to do next!

Can you scroll down to view the log when this happens?  There should be a "fatal" error somewhere along with some lines that start with =EE=, posting these would be very helpful.

Neither of those graphics cards should be any issue, so I might consider re-burning the CD (@ 4x burn speed).  Also, which installer are you using?  The liveCD or the alternate install cd?

---

### Post by HereInOz on 2007-05-06
After you get through all the "do you want to do this and that" you will eventually be at a command line screen, where you can enter the following command.

sudo dpkg-reconfigure xserver-xorg

you will then be asked for your password, which is your login password.

This will then run a utility that will enable you to re-configure the X-server - which controls how the display looks - resolution, refresh rate, etc.

It may take you a couple of runs through to get used to it, but essentially it sounds like your OS is trying to fire up the X-server with too high a resolution for your hardware, and it is failing.

So have a play with reconfiguring the x-server and you will get it right.  Once you know how this all works, it gets real easy.

Cheers,

Alan

---

### Post by KMW on 2007-05-06
> **igknighted said:**
> Can you scroll down to view the log when this happens?  There should be a "fatal" error somewhere along with some lines that start with =EE=, posting these would be very helpful.

Neither of those graphics cards should be any issue, so I might consider re-burning the CD (@ 4x burn speed).  Also, which installer are you using?  The liveCD or the alternate install cd?

I don't remember seeing a fatal error mesg. in the view error but I did see the codes listed at the bottom. I'll go back and look for the =EE=. 
The installer was the Live CD which worked fine on both and did run the check CD. It was burned at 8X using Nero.

Also had a problem at first to get it to load because the res. was at 800X600 and was cutting off the bottom of the screen so that the "NEXT" and Cancel buttons wouldn't show but was able to move to the next screen by hitting Enter.

---

### Post by KMW on 2007-05-06
> **HereInOz said:**
> After you get through all the "do you want to do this and that" you will eventually be at a command line screen, where you can enter the following command.

sudo dpkg-reconfigure xserver-xorg

you will then be asked for your password, which is your login password.

This will then run a utility that will enable you to re-configure the X-server - which controls how the display looks - resolution, refresh rate, etc.

It may take you a couple of runs through to get used to it, but essentially it sounds like your OS is trying to fire up the X-server with too high a resolution for your hardware, and it is failing.

So have a play with reconfiguring the x-server and you will get it right.  Once you know how this all works, it gets real easy.

Cheers,

Alan

From the view X server output screen htting esc. twice I get to "X server is now disabled, restart GDM when it is configured correctly".
I'll try that command, see what happens! Thanks.

---

### Post by igknighted on 2007-05-06
> **KMW said:**
> I don't remember seeing a fatal error mesg. in the view error but I did see the codes listed at the bottom. I'll go back and look for the =EE=. 
The installer was the Live CD which worked fine on both and did run the check CD. It was burned at 8X using Nero.

Also had a problem at first to get it to load because the res. was at 800X600 and was cutting off the bottom of the screen so that the "NEXT" and Cancel buttons wouldn't show but was able to move to the next screen by hitting Enter.

1) On those screens you should be able to use the down arrow to scroll down to see the whole log.  The error is likely towards the bottom.

2) Just because the liveCD ran fine doesn't mean there wasn't a disk error that messed up the install

3) You can hit ctrl+alt+F1 to get to a terminal and then type "sudo dpkg-reconfigure -phigh xserver-xorg" into the prompt, then select the resolutions you want.  Then hit ctrl+alt+F7 to get back to the GUI, then ctrl+alt+backspc to restart the gui with the new res settings.  Do this on the liveCD to get a better resolution.

4) If the above doesn't help, you can use alt+click to drag the window around so you can see the important parts.

---

### Post by KMW on 2007-05-06
Just tried reinstalling it on the compaq and this time it worked.

Will say this though, on a Compaq Presario with a 566 Celeron and only 320 megs of memory with an ATA33 8.5 gig IBM  hdd this thing isn't very fast. But you know what? It works even on this old thing! Can't wait to see what it wi;; do on my new machine with an A64 4000+ on a GF6100 MB with 512 memory.:)

---

