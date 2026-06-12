---
title: "Automatic Login and start programme"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Titus A Duxass on 2006-01-15
Hi,
I have a pc set up and running GiantDisc Jukebox (see more at [www.GiantDisc.org)](www.GiantDisc.org)), it has kubuntu installed as a server (i.e. server-expert at boot from CD) so I have no GUI.

Two questions:

1. How do I get a user to be automatically logged in on start up by command line?  The user does not require a password because I have already deleted the password with passwd -d user.

2. How do I get it to run the command gdd.pl (this starts GiantDisc) on boot.

I need to be able to do this because the finalized set-up will not have no monitor or keyboard.  In SuSE I would place a command in rc.d but I have no idea with ubuntu.

Thanks in advance.
Titus.

---

### Post by mcmillan on 2006-01-15
I haven't really messed with this much so I don't know for sure. But ubuntu has a set of a bunch of different folders that are rc#.d. I think each of these refer to what is running for the different runlevels. It seems like you put a link to the command you want to run for the level you'd be in.

---

### Post by The Mekon on 2006-01-15
If you click on System / Administration / Login In Screen Set Up and enter Password you can select Automatic Log In at first boot.

Then Click System / Prefernces / Sessions and insert Start Up Program Command.

My system automatically logs me in and starts Thunderbird Mail Reader for me so I can switch it on in the mornining, have my shower and have my mail automatically downloaded for when I return.

---

### Post by Titus A Duxass on 2006-01-16
Mekon, I do not have a GUI so cannot follow your instructions.

mcmillian, thanks for that tip.  I think I will have to look into either rc.1 or rc.2.

Cheers
Titus

---

