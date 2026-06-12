---
title: "problems with azureus"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by s0198hb on 2007-06-09
i have been using azureus this morning and now when i load it, the splash screen  loads and then Disappears any ideas

---

### Post by diatribe on 2007-06-09
try running it from a terminal and see what happens

---

### Post by s0198hb on 2007-06-09
how do i do that

---

### Post by diatribe on 2007-06-09
open a terminal and type /opt/share/azureus?

---

### Post by s0198hb on 2007-06-09
it tells me no such directory

---

### Post by diatribe on 2007-06-09
in a terminal type whereis azureus, that will tell you where the executable is, then run that

---

### Post by RomeReactor on 2007-06-09
Hi. Just enter **azureus** in the terminal and it should pop up then.

---

### Post by s0198hb on 2007-06-09
thanks what work. when i type azureus terminal i get this #
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb4822172, pid=9651, tid=3084884880
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid9651.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by RomeReactor on 2007-06-09
Do you also have **azureus-gcj** installed?

---

### Post by s0198hb on 2007-06-09
no i dont have it installed 

should i?

---

### Post by RomeReactor on 2007-06-09
I remember Azureus crashing a lot the first time I installed in Edgy; I installed a lot of Java packages I didn't have at the time and it still crashed, so I gave up. Now that I'm running Feisty, I installed it again and it crashed; I installed that package (search for **azureus-gcj** in Synaptic, it's a recommended package for Azureus) and it doesn't crash anymore. Also I recommend you go into **/home/YOU/.azureus/logs** and delete the files there (but not the "save" folder).

---

### Post by fenian on 2007-06-09
Open a terminal and enter these commands...
> 
rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

Azureus should then be able to run.

---

### Post by durrell on 2007-06-09
Yes, azureus uses Java.

Edit: I swear this place moves too fast.

---

### Post by s0198hb on 2007-06-09
so what u are saying is install azureus-gcj and clear the logs

---

### Post by RomeReactor on 2007-06-09
Yes.

---

### Post by s0198hb on 2007-06-09
thanks guys for the help

---

