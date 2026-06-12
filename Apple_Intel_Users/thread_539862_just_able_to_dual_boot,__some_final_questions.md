---
title: "just able to dual boot,  some final questions"
date: 2007-08-31
forum: Apple Intel Users
---

### Post by constantgamer247 on 2007-08-31
im extreamly new to linux. I just got my 1.83 Ghz intel core duo (not core 2 duo its the old core duo) macbook to dual boot mac and linux. now i have a few questions. how can i get the mouse to work exactly like in osx. I want to be able to 2 finger scroll and click. Also when I turned up the sensitivity the mouse did not speed up. 

can you also explain what hibernate and suspend means.

and i also found this but not shore what to do with it
------------------------------------------------------------------------------------------------
To fix the whining noise that some MacBooks make Add the following to /etc/init.d/acpid (at the very end before the exit statement) 
echo 2 > /sys/module/processor/parameters/max_cstate

thx for all you help.
------------------------------------------------------------

the wire less works but i think the signal strength meter is wrong cuz on mac it is at full bars and on linux its on half. I am on the same computer on the same router in the same location. So my guess is its linux

thx again

---

### Post by ronocdh on 2007-08-31
> **constantgamer247 said:**
> how can i get the mouse to work exactly like in osx. I want to be able to 2 finger scroll and click. Also when I turned up the sensitivity the mouse did not speed up.
I think that by "mouse" you mean the trackpad, yes? I know for my system I use the **qsynaptics** package, although some prefer **gsynaptics**. To add, just type in the terminal:
```
sudo apt-get install qsynaptics
```
You will find plenty of help in this forum if you search for "trackpad setup" or "qsynaptics."
> can you also explain what hibernate and suspend means.
As I understand, suspend keeps data stored in RAM and thus requires power, whereas hibernate writes the contents of RAM to disk and therefore requires no power while the computer sleeps.
> and i also found this but not shore what to do with it
------------------------------------------------------------------------------------------------
To fix the whining noise that some MacBooks make Add the following to /etc/init.d/acpid (at the very end before the exit statement) 
echo 2 > /sys/module/processor/parameters/max_cstate
What this means is that there's a text file which you must edit by adding the text given. To do this, type the following in a terminal:
```
sudo gedit /etc/init.d/acpid
```
Then paste in the **echo 2** line you were given, but make sure that you do it "at the very end before the exit statement."
> the wire less works but i think the signal strength meter is wrong cuz on mac it is at full bars and on linux its on half. I am on the same computer on the same router in the same location.I do not think this is a mistake. The drivers in Linux are probably open source and were blackboxed, so they likely are not taking full advantage of your hardware. In OS X, of course, the operating system understands the hardware much better, and thus the increased performance.

I don't know whether this would help, but there's [an old post on Lifehacker]("http://lifehacker.com/software/router/hack-attack-turn-your-60-router-into-a-600-router-178132.php") about juicing up your router to get a stronger signal. If the decreased reception in Linux is a problem for you, perhaps this would compensate.

Good luck, and welcome aboard!

---

### Post by constantgamer247 on 2007-09-01
thx so much.  I am on OSX now.  I am now rebouting to add all of this to linux.

---

