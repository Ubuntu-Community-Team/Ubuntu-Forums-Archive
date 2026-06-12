---
title: "Loading the GUI"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by Siiig on 2005-11-17
Alright, i feel pretty new right now...

I have installed Ubuntu (was not easy without CD support, but it will be easier now that i know how). Now im currently at the part drectly after you login. It appears to be a root folder.

Now i understand the GUI Desktop to be Gnome, and im wondering. Do i have to install Gnome or do i just boot it with a command?

Either one of these answears can someone point me to a guide, or post here on how to do it?

All the help is appriciated. Thank You in advanced.

-=|Siiig|=-

---

### Post by quietglow on 2005-11-17
If your install went properly, Gnome should automatically start up. Did you choose  to install a server setup?

You can try giving the command "startx" and see what you get--it will try to start the windowing interface.

---

### Post by Siiig on 2005-11-17
I get the message

"-bash: startx: command not found"

I didnt install the server version, you have to do somthing different for that dont you? Like type in server before you install the program?

---

### Post by Kyral on 2005-11-17
If you have server version you can choose any GUI you want. Check this out for the options and how to install them

[http://www.ubuntuforums.org/showthread.php?t=87276](http://www.ubuntuforums.org/showthread.php?t=87276)

---

### Post by Yoda_Oz on 2005-11-17
mate,
it looks like your installed buggered up somewhere.
i suggest trying again and making a note of everything (and every option you check) you do when you installed.
it took me a few times to install properly, however gnome booted up beautifully each time... so im not sure whats going on with yours.
do you have a directory called /etc/X11/ ???
if not then you dont have X installed. (x is the gui).

---

### Post by quietglow on 2005-11-17
Yeah, sounds like you got dumped into the CL because of the install not working properly--you don't have X installed. Time to start over and pay very close attention (writing stuff down is a great idea!) to the decisions you make in the installer and also any errors you get before it stops. We'll have to have something to work with to help you out--specifics about your hardware as well.

---

### Post by Kyral on 2005-11-18
It looked like he chose the "server" or expert options. Both of which could easily drop him to the terminal at reboot

---

### Post by Siiig on 2005-11-18
Well i will attempt to re-install. And as for specifics on the hardware they go as follows (as far as i know, lol)

Computer: IBM ThinkPad 765D
Proc: Pentium  (i belived it to be a 2, but its looking like its a 1 now)
Memory: 48152KB (According to the bios)
HDD: 3.0GB

The rest of the computer is all on-board except network.

Network Card:
PCMCIA 3Com Air Connect

...

When i tryed to install a window manager i gave the computer the command
> sudo apt-get install kubuntu-desktop
I let it sit (it seemed to go well starting out) and left it on over night, when i woke up, it had a black screen. So i turned it off and turned it back on, logged in like normal... Still command line... So i type startx and somthing tryed to happen but didnt, ill post the error in an edit..
-=|Edit|=-
Alright, heres the error i end up with when i use "StartX"
> (EE) VESA(0): No Matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The.X.Org Foundation for support. at [http://wiki.X.org](http://wiki.X.org) for help

Please also check the log file at "/var/log/Xorg.0.log" For additional information

XIO: Fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

Well, hope that helps... Was wondering,  remember the window manager asking me about resolutions, but i didnt change anything on the window, could that be causing a problem, the computers monitor doesent support over 1024x768.

Just to add this, this computer can run Windows 98SE (i figured if it can run that it can run this).

---

### Post by Kyral on 2005-11-18
A 3 GB HD...

Dude, space is REALLY tight. A normal install takes 1.8 GB. I'd reinstall, choosing the server option, then installing a lightweight GUI like Fluxbox, and stuff like Firefox. You don't have space to spare it seems. Kubuntu prolly failed because it ran out of space

---

### Post by Jussi Kukkonen on 2005-11-18
with <50MB of memory you are not going to run KDE or gnome, that much is certain.

How do you end up with 48152 kB by the way? Broken chips?

---

### Post by Biased turkey on 2005-11-18
[QUOTE=quietglow]If your install went properly, Gnome should automatically start up. Did you choose  to install a server setup?

You can try giving the command "startx" and see what you get--it will try to start the windowing interface.[/QUOTE]

Or his problem might be that some hardware ( monitor ) has not been detected and/or configured properly and after login he is jut thrown back into console mode.

---

### Post by Yoda_Oz on 2005-11-18
what does your "/etc/X11/xorg.conf" say? can you post it please?

---

### Post by Siiig on 2005-11-18
Uhm, lets see, On the matter of tight space, im only looking to put maybe the GUI and firefox.

On the broken chip though, its a pretty old computer, and i agree, 49 doesent make sense, but thats what the bio's is giving me and i dont feel like questioning it.

On the thought of a monitor problem, i dought thats the problem. I think i must have just configed it wrong and the monitor couldnt run at the resolution ubuntu tryed to run it at.

Finaly, i got an error when i tryed to install FluxBox. Ill post it here.
> Code Used: sudo apt-get install fluxbox fbdesk fbpager fluxconf

-=|Long List of Code's (errors)|=-

E: Couldn't find package Fluxbox

That was the last on the list of codes.

---

### Post by Jussi Kukkonen on 2005-11-23
Siiig, fluxbox is in universe-repository -- have you added extra repositories into your apt sources?

See ubuntuguide.org if you need instructions.

---

