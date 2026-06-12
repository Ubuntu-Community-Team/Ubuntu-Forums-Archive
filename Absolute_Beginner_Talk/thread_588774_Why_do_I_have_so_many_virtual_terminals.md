---
title: "Why do I have so many virtual terminals?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-10-23
Not sure what I can add to the thread title other than why have 6 virtual terminals?  And what are they for?  Safety backups when you fubar your system?

---

### Post by jpyanowski on 2007-10-23
How many do you want? 8-[

---

### Post by markp1989 on 2007-10-23
i would like to know aswell i think you may be right about it being aback up for if you break  somthing

---

### Post by Vansinnesvisan on 2007-10-23
Terminals may seem antiquated by today's standards; but they are more efficient in use and in taxing the system's resources, as well as a much more powerful way to administrate the system. GUIs can get in the way of accomplishing a task and the CLI can be faster in achieving others. They are still heavily used in servers, mainframes, supercomputers.

Some things can not be administrated while in a graphical setting and need to be done at the command line.

Other operating systems stay away from the CLI due to its higher learning curve. But mixing CLI with GUI is optimal, IMO.

The amount of virtual terminals can be changed by editing inittab under /etc with most distributions. But Ubuntu uses some other system, I believe. Six virtual terminals is pretty much standard. I reduce mine to two, though. 

There are some CLI programs I keep handy - just in case I break something badly. MC (midnight commander) for a file manager. MOCP (music on console) for audio play back. Links for web browsing. Nano for text editing.

---

### Post by linfidel on 2007-10-29
I believe I know why they were there originally.  If you logged on with no GUI, you had a terminal screen (emphasis on "a").  So, if you were in the middle of something like editing a config file, and needed to do something as another user, usually root, but didn't want to quit whatever you were doing, you could switch to another terminal session easily and log in, make changes, etc.

With a GUI, you would simply run another terminal on the same screen.  So, I wonder if all those terminals are needed now.  It seems like you could set it up so you had one init level with the VTs for non-GUI operation, and a level without the VTs for GUI mode.

Maybe the power users are more used to running new VTs rather than new terminal instances, so they keep them around because of that. :)

---

### Post by x1a4 on 2007-11-06
> **cknight said:**
> ... why have 6 virtual terminals?  ...

Why not?  Personally, I'm only running 3 ttys and 3 X sessions by default.  You can configure Linux any which way you want.

---

### Post by Dr Small on 2007-11-06
I use my virtual terminals for command lines when GUI stops working, and I also start other X sessions with those Virtual terminals and have different window managers on them ;)

---

### Post by hyper_ch on 2007-11-06
I just love "screen" :) one terminal to control it all - and it's also detachable so you can start right where you stopped at another place ;)

---

### Post by linfidel on 2007-11-10
> **Dr Small said:**
> I use my virtual terminals for command lines when GUI stops working, and I also start other X sessions with those Virtual terminals and have different window managers on them ;)I'm curious - what method do you use to run more X sessions?  I've managed to run a 2nd one in the past, using :1 display, but I don't remember the details.  It seems like it may not have been totally smooth.  Maybe you can save me some time by steering me to the method you use (I hope).

---

### Post by roaldz on 2007-11-10
@x1a4:
Why would you possibly use three different X sessions?  Think that just slows things down. I´d rather use compiz, in combination with the multiple desktop configuration. You can even do it without compiz, just use your desktop switcher. 
I can understand that you maybe want one Xgl session, and a normal X session, if you´re an ATI user. What´s your reason for running three different X sessions, x1a4?

Greetings,


Roald

---

### Post by linfidel on 2007-11-11
> **roaldz said:**
> @x1a4:
Why would you possibly use three different X sessions?  Think that just slows things down. I´d rather use compiz, in combination with the multiple desktop configuration. You can even do it without compiz, just use your desktop switcher. 
I can understand that you maybe want one Xgl session, and a normal X session, if you´re an ATI user. What´s your reason for running three different X sessions, x1a4?

Greetings,


RoaldWhat if you're connecting to remote systems? Sometimes it's necessary, I think, to use a different X display for different systems - :0 for local, :1 for remote system 1, etc.

---

### Post by airtonix on 2007-11-12
different x's for : 
 1 - different resolutions
 2 - different outputs to different stations 
 3 - or monitors.
 4 - or for use by more than one person at same time....four people using four keyboards and mice connect to one linux box with four monitors.

and if you think the CLI is an ancient thing...If you thin that Vista is a modern browser since its managed to get rid of the CLI.

YOU ARE WRONG

the CLI is required in this Vista Fix: 

>  My LAN connection has been dog slow since day one with vista. I figured it&#8217;d be some new &#8216;feature&#8217; thats killing it. Looks like I was right.[INDENT]The synopsis is that their appears to be a problem with Vista being too smart for it&#8217;s own good, with the addition of the &#8220;Receive Window Auto-Tuning Level&#8221; setting in the TCP/IP stack.
 Disabling this setting fixed the timeout problem in FF2 and Windows Live Writer on my machine. Make sure you&#8217;re running as an Administrator (can open a command window as Administrator) and execute the following command at the prompt:
 &#8220;netsh interface tcp set global autotuninglevel=disabled&#8221;
 Changing &#8220;disabled&#8221; to &#8220;normal&#8221; will re-enable this setting, should you want to turn it back on again. The following command will list the status of the current TCP settings:
 &#8220;netsh interface tcp show global
[/INDENT]quoted : [http://tidky.jeffkaplan.net/2007/05/13/vista-slow-network/](http://tidky.jeffkaplan.net/2007/05/13/vista-slow-network/)

---

### Post by linfidel on 2007-11-18
> **airtonix said:**
> ...
and if you think the CLI is an ancient thing...If you thin that Vista is a modern browser since its managed to get rid of the CLI.

YOU ARE WRONG

the CLI is required in this Vista Fix: 

quoted : [http://tidky.jeffkaplan.net/2007/05/13/vista-slow-network/](http://tidky.jeffkaplan.net/2007/05/13/vista-slow-network/)I don't think anyone thinks the CLI is dead, but a lot of people don't want to use it, or don't even know how.

But I take issue with your assertion that CLI is _required_ simply because that was the way the "fix" was presented.  It's a lot easier to instruct someone to type a command than to explain how to navigate the GUI to get to some obscure setting in some tab of a property page, after pressing settings, advanced, etc, etc.

It's like when someone on this forum says to type "sudo apt-get install blah blah" rather than saying to open synaptic or run aptitude interactively; it doesn't prove the CLI is required to install that feature, just that it's much easier to cut and paste one line into a CLI than explain how to navigate.

Being a programmer, I just don't like "proofs" that prove nothing.

---

