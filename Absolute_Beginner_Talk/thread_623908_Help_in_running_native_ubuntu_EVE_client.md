---
title: "Help in running native ubuntu EVE client"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by graeme_was_here on 2007-11-26
Hello i'm asking for help as i am pretty new to ubuntu 7.04 

I am a vivid EVE player and was overjoyed at the idea of EVE having a ubuntu client which i installed the problem is once the EVE loading splash screen disappears nothing happens at all as if the program has disappeared no error messages or anything.

---

### Post by PeterJS on 2007-11-26
Just a heads up, I'm sorry you bought in to their lies, but there is no native linux client, it's just the windows client packaged and wrapped with wine. I'm not sure how it's set up exactly, but your best bet would be to track down where the actual windows executable is and then manually run that under wine, it should produce an error message we can work with.

---

### Post by daengbo on 2007-11-26
Have you tried starting the client from a terminal and watching the output? You can paste the output here and someone should be able to help you.

---

### Post by aabo on 2007-11-30
Hi!

I've got the same problem. Running it from the terminal i get:
Single-user install...
This is the update checker... 
Running /home/myname/.cedega/.updater/cedega_updater.py
/home/myname/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Running... /home/myname/.cedega/.ui/runGUI
/home/myname/.cedega/.ui/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
myname@laptop:~$ 

Do i need to update the python thingy? How can i do that?

 -aabo

---

### Post by cytg on 2007-12-25
just installed it, and running through character setup right now .. didnt work out of the box, couldnt locate game file or something, but there's an option to dl from the net.. that worked just fine.
(did a preemtive troubleshotting search prior to installing it, and ran into this thread, just a heads up)

---

### Post by dpar on 2007-12-25
I used the eve/cedega wrapper for a bit, but the frame rates were terrible. I'd get killed before I even knew anyone was there:)
I've heard that it runs under wine better, but to heck with it, if I want to play eve, I'll install windblows until they come out with a real client instead of a phony wrapper.

---

### Post by cytg on 2007-12-25
nevermind .. **** crashes .. 2 times about 30mins into gameplay .. dont even get to finish the tutorial... oh well, i wont be playing eve after all... problary for the best too..

---

### Post by ClintonEv on 2008-01-26
> **PeterJS said:**
> Just a heads up, I'm sorry you bought in to their lies, but there is no native linux client, it's just the windows client packaged and wrapped with wine. I'm not sure how it's set up exactly, but your best bet would be to track down where the actual windows executable is and then manually run that under wine, it should produce an error message we can work with.

Yes there is a native client check the website [http://www.eve-online.com/download/linux.asp](http://www.eve-online.com/download/linux.asp)  linux versions

I dont mean to barge in but i am having a similar problem except mine crashes on the character screen and when i run it through terminal thsi is the output:

Single-user install...
This is the update checker...
Running /home/clinton/.cedega/.updater/cedega_updater.py
/home/clinton/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Running... /home/clinton/.cedega/.ui/runGUI
/home/clinton/.cedega/.ui/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
clinton@Clinbuntu:~$ 0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 1
0004:  Bad stuff: client ignore setting select events for 0x9004fb68 to 0
                                                                         

Can anyone help me?

---

### Post by Vadi on 2008-01-26
It's not native, unfortunately. It's just cedega + windows binaries. Outside, it looks as if it's native.

(you'll get the same effect if you installed the windows version in wine is what I mean)

---

### Post by Incompetnce on 2008-02-03
i have the same problem. i went opened eve configuration and it tells me i fail the 3D acceleration test. I install some synaptic package which i thought was alternative drivers for my graphics card. now i fail both openGL direct rendering and 3D acceleration. although the gears thing displays fine when i do the tests...

can anyone point me to a nice guide on how to get the best drivers for your graphics card?

---

### Post by Vadi on 2008-02-03
What is your card? If it's barely on the edge of min requirements it might not work.

For example my card fails it's 3d test too. While my Compiz works just fine. But it's a Radeon 7500, which is very old.

---

