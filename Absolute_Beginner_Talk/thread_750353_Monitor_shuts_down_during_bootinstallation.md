---
title: "Monitor shuts down during boot/installation"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by clykke on 2008-04-09
I have just tried to install ubuntu for the first time, and have come across the exact same problem as the guy in this thread: [http://ubuntuforums.org/showthread.php?t=662290](http://ubuntuforums.org/showthread.php?t=662290) but haven't been able to resolve the problem.

Chain of events:

Boot from ubuntu 7.10 64-bit live CD.
Pick boot/install (or boot in safe mod. Same result)
The "loading linux kernel" completes
Monitor shuts down

At this point I have to press reset.

I have tried adding the no-hlt command at the command line (while having the install option selected, I press F6, the write "no-hlt" at the end, just after "--") but to no avail.

I am absolutely clueless, and would greatly appreciate some help.

My system is:
Core 2 Due E8500, 3.16 Ghz
Asus Maximus Republic of Gamers 
Asus nVidia 8800GT
4GB Ram

Can I get some pointers? I have read just about anything I can find about this issue, and I have not been able to find an answer.

Thank you in advance.

---

### Post by ace007 on 2008-04-09
EDIT: upon re-reading your post and following the link and reading the depth of solutions you've already tried, I realize that my advice if basically useless to you.  ....Oops

this sounds like a graphics card issue.  I have had a number of experiences with the monitor shutting down right after the OS has loaded.  Ubuntu/Windows use different drivers and the issue could be there (Assuming the problem is non-existent in Windows).  If you have a dedicated graphics card I would try disabling it in the BIOS, or unplugging it completely, so that the on board graphics are being used.  And then try to boot the Live CD.    At the very least this will tell you for sure the issue is with the Graphics card.  As for how to fix the issue, I'm not exactly sure.  I had the same issue with Windows and I ended up just dumping the graphics card.

P.S. - I know that rolling back drivers helped fix my problems with Windows to a certain extent, but since you cant even boot Ubuntu, I don't know where to tell you to go next.

P.P.S. - this is just a thought.  but sometimes the refresh rate is turned too high, so trying to boot with a CRT then adjusting the settings can help.

---

### Post by namich2007 on 2008-04-09
I recently help a collegue with the exact same problem. It turned out that the ISO file he burned somehow got corrupted.

So we just downloaded it from a complete different mirror and burnt it again. Worked perfectly.

---

### Post by clykke on 2008-04-09
@ ace007

Onboard graphics? I don't think there is any onboard graphics. There is not output for it anyways. The only way I can connect my monitor is to the Gfx-card. 

Maybe I am misunderstanding something?

@ namich2007

I have tried both the CD I have ordered from ubuntu.com and a CD I have burned my self. I cannot completely rule out that the ISO is corrupted, but it would be strange if both CD's have the same problem. I will try it though, if I cannot solve the problem somehow.

---

### Post by ace007 on 2008-04-09
Most motherboards have some rinky-dink on board graphics, its possible your MoBo does not.  In which case, I would still bet there is some incorrect setting that causes your monitor to not display anything. 

I dunno, maybe try another monitor.  I have reached the limits of my knowledge, sorry I couldn't be more helpful.  


Dont give up on Ubuntu!

EDIT:

the ASUS Maximus Mobo has no on board graphics chip

EDIT: EDIT:

One last thought, try removing the quiet and splash flags for the command line boot and adding the "--nosplash" flag

---

### Post by clykke on 2008-04-09
I tried to remove the quiet and splash flags, and I added the nosplash. Now, the monitor does not shut down, it just remains black. Nothing is shown. I am not sure I am typing the flags correctly. I press F6, then I edit this:

"[lots of text] quiet splash --"

to this:

"[lots of text] --nosplash"

I also tried:

"[lots of text] nosplash --"

Am I doing this right?

---

### Post by mmillman on 2008-04-09
The "nosplash" and removal of the "quiet" method did work for me... (I'm using a 9600 GT).. but that doesn't necessarily mean it will work for you... especially considering I don't really understand HOW it works/helps in the first place... making the install verbose and removing a splash screen doesn't make any sense to me to make it work... but it did anyway =)

Anyway, can you even get to a tty out of the situation?  Next time you start it up, let it run for about a minute or so (even though there is no display on your monitor), and then try hitting Ctrl+Alt+F1.  If that enables you to input commands, you can always try[ this method]("http://ubuntuforums.org/showthread.php?t=690760") to get to at least the vesa driver.

---

### Post by ace007 on 2008-04-09
try just no in front of the 'splash'.  try removing the "--" all together.  Also, maybe try to boot to a resolution you know for sure will work with you card/monitor via--> [http://ubuntuforums.org/showthread.php?t=258484&highlight=vga%253D791+usplash](http://ubuntuforums.org/showthread.php?t=258484&highlight=vga%253D791+usplash)

the removal of quiet only serves to increase the verbosity of the boot process.  Maybe you can catch some kind of error on the screen

---

### Post by Neo0351 on 2008-04-09
try booting in graphics safe mode.  if that dont work, use the alternate install cd.  its your graphics card, the 8800 and 9600 have this problem.  once installed, use envy to install the proper drivers for you card.

---

### Post by clykke on 2008-04-09
@ Neo0351

It sounds like you are 100% sure that the alternate install cd is going to work? 

What is the difference between the two CD's, and is there anything I should know when using the alternate?

PS - I have tried graphics safe mode. It doesn't work either.

---

### Post by Neo0351 on 2008-04-09
nothing in this world is 100%, but im pretty sure it will work.  it doesnt use a GUI to install, it uses a text based installer.  many people have had success with it.  since most likely you graphics card is the problem, it takes it out of the equation.

---

### Post by clykke on 2008-04-10
Well, I am going to give the alternate CD a try, but I am not able to find a guide for installing with the CLI. Can someone help me out here?

---

### Post by gartenzwerg2 on 2008-04-10
Hi, I don't know if this is your problem, but I had a similar one:

I bought a preconfigured ubuntu system and tried to hitch it up with my old benq fp533 LCD monitor. The system booted ok, but shortly before the login window the monitor told me "out of range". I hitched the computer to another monitor and didn't have any problems there. I tried setting the resolution to one that the LCD could definitely handle, but the problem persisted. Funnily enough, if I entered my login blindly while the monitor told me "out of range", it did work after successful login. It turned out that my graphics chipset (SIS mirage) didn't communicate well with the monitor, to be more specific, the EDID probe of the monitor didn't work with it (that is why my older monitor worked fine).

I finally replaced the driver for the graphic chipset with one that didn't do the EDID probe, and it has since worked fine.( I know you don't have the SIS, but my sourec was [http://ubuntuforums.org/showthread.php?t=463077&page=4](http://ubuntuforums.org/showthread.php?t=463077&page=4))

good luck!

you might also want to have a look here: [http://ubuntuforums.org/showthread.php?p=4688452](http://ubuntuforums.org/showthread.php?p=4688452)

---

### Post by clykke on 2008-04-10
@gartnzwerg2

Not quite the same problem, but close enough that it might be related. I just bought a new monitor, 22" LG L227WT, does anyone know if there is a problem with it?

Can someone point me to an easy-to-undestand guide for installing with the alternate CD? I seriously need some help here to get ubuntu going.

---

### Post by clykke on 2008-04-10
Hmm, it seems like I have misunderstood something. I thought the alternate CD was based on a commandpromt (dos-like) but it looks like there are menus and stuff. Maybe I don't need a guide after all.

---

### Post by clykke on 2008-04-11
Just wanted to follow up on this, as some people might have the same problem.

This is what I did to make things work:
- Download a new ISO. I installed the 7.10 desktop 32-bit.
- Removed the "quite" parameter, and turned the "splash" into "nosplash".
- Resolution set to 800x600
- Picked the graphics safe mode

I have no idea which of the above solved the problem, or if it was all of them in combination.

---

