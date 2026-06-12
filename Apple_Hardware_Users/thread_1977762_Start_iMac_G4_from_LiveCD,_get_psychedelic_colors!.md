---
title: "Start iMac G4 from LiveCD, get psychedelic colors?!"
date: 2012-05-10
forum: Apple Hardware Users
---

### Post by Ubobtu on 2012-05-10
So I have this nice bowl on the bottom G4 (ppc) and thought I would make it useful with the most recent version of Ubuntu.

So after getting the CD started, I'm finding that I cant get far past the first 13 seconds. No matter what I do at the first prompt, either just pressing enter or doing commands like nosplash-powerpc, I get the same result.

First it looks like it's about to go, then I get a weird image were the bottom-portion of the display is black but the top is this weird "soup" of rotating blobs of color. Mostly yellow and gray. I hear the CD drive going, but even after leaving it for several hours it is still showing nothing.

[IMG]http://i49.tinypic.com/jz6urc.jpg[/IMG]


Great for if I needed a lava lamp, but it doest get me any further for using ubuntu. I'm stumped, but I can only assume I'm not the only person that has had this problem even after digging through dozens of posts of stuff that sort of seemed like what I'm experiencing. How did anyone get past this? Thanks for any help.

---

### Post by conal on 2012-05-11
Have you tried using the alternate install install CD instead?

---

### Post by Ubobtu on 2012-05-11
> **conal said:**
> Have you tried using the alternate install install CD instead?

Did that. Waited 2 hours for it to install. Got to the first boot, and it is still nothing but the exact same result.

---

### Post by conal on 2012-05-14
Lots of people have problems with graphics on power pc. Normally I'd suggest that you install without a graphical desktop using the alternate install, then try and get x working (there are heaps on of threads on these forums about this as I'm sure you have seen), however - this problem seems even stranger. Is it possible that there is something physically wrong with the mac? To test this I suggest downloading a very old version of Ubuntu powerpc live cd. In my experience the old versions will boot on any of my G4's - go back a few versions, e.g: [http://old-releases.ubuntu.com/releases/6.10/](http://old-releases.ubuntu.com/releases/6.10/)

If that boots up with a GUI then your problems with the newer versions can hopefully be fixed!

---

### Post by rsavage on 2012-05-14
> **conal said:**
> Lots of people have problems with graphics on power pc.

This is not true (or shouldn't be if they read the Known Issues or PowerPC FAQ pages). 
 
> 
 Normally I'd suggest that you install without a graphical desktop using the alternate install, then try and get x working (there are heaps on of threads on these forums about this as I'm sure you have seen), however - this problem seems even stranger. 

Nope pretty typical for an IMac G4 800/700 using nouveau.
 
>   
Is it possible that there is something physically wrong with the mac? To test this I suggest downloading a very old version of Ubuntu powerpc live cd. In my experience the old versions will boot on any of my G4's - go back a few versions, e.g: [http://old-releases.ubuntu.com/releases/6.10/](http://old-releases.ubuntu.com/releases/6.10/)

You are just wasting the persons time.
 
> 
If that boots up with a GUI then your problems with the newer versions can hopefully be fixed!
They can of course be fixed.  All you have to do is read the PowerPC documentation.

---

### Post by conal on 2012-05-14
OK Rsavage, I was just trying to be helpful because I saw nobody else had replied. I am assuming this person has read the POWER-PC FAQ  already, perhaps not.

I have found testing with an old version to be helpful in the past - it eliminates the problem of there being something physically wrong with the mac. I have tried to install on a G4 in the past - spent a lot of time thinking the problems was to do with nouveau, only to discover their was visible physical damage inside causing the graphics to fail (turned out the graphics were wonky on OS X too)

I think I'll leave replying to people on the forums to experts such as yourself in future - My aim is not to to waste time, but the best I can do is go through the trouble shooting process in the way I know best (which has, of course, benefited from your contribution to the PowerPC FAQ).

---

### Post by rsavage on 2012-05-14
> **conal said:**
> 
I think I'll leave replying to people on the forums to experts such as yourself in future
 
I'm sorry if you are going to do that.  
 
This forum needs people who actually have nouveau cards to contribute, experiment, report bugs and generally help people out.  
 
Nobody who owns a G4 iMac has reported on the results of disabling phantom outputs.  It is therefore impossible for non-nouveau people (like myself) to give detailed advice on what the best solution for the original poster is.
 
I've taken the FAQ and Known Issues pages as far as I can.  If people don't read them then that is their problem.  I'm not replying to messages that are covered by the documentation anymore.  It is also for others to update and improve the PowerPC documentation from now on.

---

### Post by Knightwise on 2012-05-24
Hey Guys 

I seem to have the same problem. I have a G4 imac (800 Mhz, 768 megs of ram) with a 17 inch display. When i try to boot from cd (using either the 'alt' key or the 'c' key) I get some fancy colors (kind of the same as mentioned above) and then the screen just goes blank.

i've tried the regular 12.04 cd and the alternative install. But the problem is also the same with the Debian PPC version that is out there. 

The cd spins up, the screen goes blank .. and that is it. :(

---

