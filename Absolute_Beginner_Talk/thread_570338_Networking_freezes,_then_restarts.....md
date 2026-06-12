---
title: "Networking freezes, then restarts...."
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by drhiii on 2007-10-08
I have tried a bazillion things to find out why the following... 

Every few minutes, network activity just freezes for approx. 28-30 seconds.  it is very consistent the amount of time it is stopped.  

However, I cannot figure out what is causing it.  I have run Opera, not run Opera, run Mozilla, not run Mozilla.  Run streaming media apps in the BG, turned them off.   I installed Beryl and ran it, then did not run it.  I disabled Samba services, thinking that might have something to do with it.  No go.  I have looked at the processes running and disabled other things to see if there was something just creating a conflict.  Nothing.  

I have tried to observer in the system logs anything that would indicate what is run at the moment the networking hoses.  Nothing else stops.  Mouse activity, switching virtual windows (running Gnome), all proggies, continue to work.  I don't see anything that suggests there is some something that conflicts.   When it freezes is not consistent.  But the length of time it does, is consistent.   I am not running a wireless NIC but am using a NIC to connect to a wireless bridge.  None of my other machines exhibit this problem using the same wirelsss bridge.

Has another experienced something like this?  I have three other Ubuntu installations running Feisty (and upgrading religiously), and none have this issue.

I know this is some scant info, but thoughts anyone, or at least if someone else has experienced this????

tx

---

### Post by SpiritIsReality on 2007-10-08
> **drhiii said:**
> I have tried a bazillion things to find out why the following... 

Every few minutes, network activity just freezes for approx. 28-30 seconds.  it is very consistent the amount of time it is stopped.  

However, I cannot figure out what is causing it.  I have run Opera, not run Opera, run Mozilla, not run Mozilla.  Run streaming media apps in the BG, turned them off.   I installed Beryl and ran it, then did not run it.  I disabled Samba services, thinking that might have something to do with it.  No go.  I have looked at the processes running and disabled other things to see if there was something just creating a conflict.  Nothing.  

I have tried to observer in the system logs anything that would indicate what is run at the moment the networking hoses.  Nothing else stops.  Mouse activity, switching virtual windows (running Gnome), all proggies, continue to work.  I don't see anything that suggests there is some something that conflicts.   When it freezes is not consistent.  But the length of time it does, is consistent.   I am not running a wireless NIC but am using a NIC to connect to a wireless bridge.  None of my other machines exhibit this problem using the same wirelsss bridge.

Has another experienced something like this?  I have three other Ubuntu installations running Feisty (and upgrading religiously), and none have this issue.

I know this is some scant info, but thoughts anyone, or at least if someone else has experienced this????

txthoughts...possibly an intermittent pci connection of the nic card. remove and replace a couple of times and make sure it's seated properly again. Maybe try the pc on a connection cable that is good, that's being used by another pc right now that works, to check if it's a cable,,put the good connection pc on the poor connection line, is it poor now?

---

### Post by jfinkels on 2007-10-09
Is this a wireless network connection or a wired ethernet network connection?

---

### Post by SpiritIsReality on 2007-10-10
> **jfinkels said:**
> Is this a wireless network connection or a wired ethernet network connection?
I am not running a wireless NIC but am using a NIC to connect to a wireless bridge. None of my other machines exhibit this problem using the same wirelsss bridge.

---

### Post by drhiii on 2007-10-12
Hello,

It is a wireless network, but utilizing a bridge.  So several machines, all Ubuntu, are hardwired into a switch which then communicates wirelessly.  

On the other machines, I can ping and watch a steady ping count.  On this machine that freezes for approximately 30 second every few minutes, the pinging stops on this machine, and I have had several windows open with different sites being pinged, but on the other machines... everything continues uninterrupted.  I am confident that it is within the system in question and not the network.  

Have read of more frezing applications in Ubuntu, but nothing that has this particular characteristic...

Thoughts?



> **jfinkels said:**
> Is this a wireless network connection or a wired ethernet network connection?

---

### Post by SpiritIsReality on 2007-10-12
I would try switching the pc to a known working cable connectin.
then try switching nic cards, or reseating the nic card, to try to rule out a hardware cause?
what are your thoughts?

---

### Post by jfinkels on 2007-10-12
You've stumped me. Maybe someone else will know. Do you get any useful information if you run ```
top
```? Does it show any process doing something crazy while these freezes occur?

Have you ever considered that the port in your bridge is bad? Or perhaps your CAT5 cable? Try connecting the computer to a different port with a different cable.

---

### Post by SpiritIsReality on 2007-10-13
howdy
it could be hardware. Please try another nic. another cable. ones that you know work.
try reseating the nic in intermittent pc.
also there is a better thread than the one I found about noob12 stating something about a connection reading hinting at a bad seat of the nic, but I can't seem to find it right now.
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+noob12+intermittent+nic&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+noob12+intermittent+nic&btnG=Search&meta=)
trails

---

