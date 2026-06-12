---
title: "What to do if Ubuntu crashes due to a bad system restart?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-05-31
I installed Ubuntu using Wubi. Had a bad system restart and Ubuntu won't load for me now… Any ways to recover this installation? More details [here]("http://ubuntuforums.org/showthread.php?t=460424").

---

### Post by abn91c on 2007-05-31
reboot to windows Xp, when you get to the user nane screen on XP restart computer from there. his will let you get into Ubuntu.

---

### Post by Sushubh on 2007-05-31
are u sure? coz this sounds to be doing nothing to fix the ubuntu installation?

---

### Post by abn91c on 2007-05-31
by looking at your screenshot, did you try one of the following from root
apt-get check, or apt-get update?
if the command line suggest a command try using it. It fixed some issues i had with apt the other day

---

### Post by deadgobby on 2007-05-31
With power going in and out. Sorry to hear about that in your part of the world. I am thinking of you have the ubuntu prompt at the start up. Type in 
sudo fsck  
and see if it will clean up and boot up.  Even if you have a second source of power like a UPS system. If it flickers from a power surge. It may corrupt the whole process. If night time is better time for %100 power to your dwelling than the day time. I would go that route. 
GObby

---

### Post by Sushubh on 2007-05-31
on trying to run that command it says apt not installed something... :|

---

### Post by Sushubh on 2007-05-31
command not found error on all the commands. 

looks like i would have to reinstall.

just tell me whether a regular installation would have these kind of possible hassles if system reboots abruptly. and if THAT indeed happens, would it corrupt my boot manager!

---

