---
title: "Changing Screen Resolution"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-05-08
Hi gang

i'm on a windows machine that's using VNC to view an ubuntu machine... i'm doing this cause i have only one screen and my windows machie in need it for my job. anyway... when i have the monitor connected to the ubuntu machine... the resolution is 800 by 600 or a little higher... however when i have the ubuntu machine without a monitor... when i VNC into it via my windows machine (machine with the screen...duh) i only get a 640x480 resolution... very crampt view of my ubuntu... when i use the "preferences... screen resolution... i cannot change the resolution to anything higher...

is there a way around it so that i may get a HIGHER resolution?? can i use a set of terminal commands to execute /  bypass this restriction and make the resolution larger (even though the machine has no screen!)

... can i tell ubuntu to IGNORE my screen detection at startup?

thanks for the help...

---

### Post by louis_nichols on 2006-05-08
I've experienced that once. I tracked it down to the system not detecting any monitors when booting. A video card can detect the monitor and let you choose resolutions and refresh rates it can support and if it doesn't detect anything, then I guess it will turn to some kind of defaults.

There isn't something you can really do. I guess a workaround would be to boot your machine with the monitor connected, select your desired resolution, then unplug your monitor and plug it where you need it. I'm not 100% sure it will work, in the sense that the machine will keep the resolution after unplugging the monitor, but it might. Still, you'll have to do this every time you boot.

EDIT: typo

---

### Post by ProjectGod on 2006-05-08
:-( 

i'm not too fond of plugging a monitor in/out while a machine is running... i've got this fear of electrical devices... believe it or not... i've had way tooooooooo many power supplies bursting into flames at plug in to want to try something like that... its almost like a phobia... hopefully i can shake it off. :p 

thanks for the advice though. guess i'll have to manage with a crampt screen...

cheers.

---

### Post by ProjectGod on 2006-05-08
on second thought... umm i guess linux should have a command or two to edit "default resolution"... or perhaps the default 640 480 is "etched" into the video card by the manufacturer... 

it worked perfectly the other way around... ubuntu with a monitor and 800 600 above resolutino and a VNC session with windows (very new machine) withOUT a monitor... perhaps because of the "good" video card...

oh well.

---

### Post by louis_nichols on 2006-05-08
The resolution isn't provided by the video card, but by the monitor.

Now that you mention it, I guess you could try to edit your xorg.conf to contain (only) the resolution you want. It might work. My setup was different, with windows being without a monitor (you should consider that - it deserves it! :p *joking*) and Ubuntu as vncviewer and, even though I tried to uncheck the option for displaying resolutions my monitor cannot handle, it still wouldn't set to it.

---

### Post by ProjectGod on 2006-05-08
ah of course... silly me. the monitor.  

i would like to permently use ubuntu... but i'm still a newbie. and i've got so many apps and VPN connections on my windows machine that if i didnt have windows now. i'd be rendered totally helpless.

editing the xorg... i wouldnt have a clue on how to do that... i'll wait for someone else to do so and if it works great. i'll follow. 

cheers :D

---

### Post by pkkid on 2006-05-08
I just figured this out today as well.  I am running Ubuntu in the same exact fashion.. :)

see here:
[http://www.ubuntuforums.org/showthread.php?t=172525](http://www.ubuntuforums.org/showthread.php?t=172525)

---

### Post by ProjectGod on 2006-05-09
BRILLIANT PKKID! BRILLIANT! ahem. i havent tried it yet so cross my fingers. 

not bad for someone who've only had their "first cup"... applause... cheers

:-D

---

### Post by ProjectGod on 2006-05-09
IT WORKS! 

i didnt use the Vert refresh line...

had trouble editing the conf file... it was read only!

enabled my root account with 

**sudo passwd root**

then... 

**gksudo gedit **...... (opened the file and was able to write)

OR at the terminal

**sudo su**

type password in

changed to the directory cd etc/x11/

typed:

**gedit xorg.conf**

after a restart it was BEAUTIFUL!!!!! could even use GUI tool "screen resolution" to change to many other resolutions...

WONDERFUL.

---

