---
title: "Cursor problem in Firefox"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by doctor bangali on 2007-03-28
Hi, 
USING : Dapper Drake, Firefox 1.5.0.11

When I type something in a text area and use the left/right arrow keys to navigate to a particular point instead of one line representing the cursor at its current location I see this whole row of cursors one  for each point I have passed through.

It looks ugly and makes editing posts a painful experience, for I can't really determine where the actual cursor location is. If I press the backspace or the return key many of these zombie cursors vanish, though not all.

Any idea why this happens?

---

### Post by zorkerz on 2007-03-29
And you only get this in firefox?
I would personally first try an upgrade. If you have some reason not to do this I don't quite know where to go.
cheers

---

### Post by doctor bangali on 2007-04-01
I upgraded to edgy, same problem. Clean install

I noticed similar problems in thunderbird.

---

### Post by zorkerz on 2007-04-02
interesting so it seems to only occur with mozilla apps?  What version of the programs are you using now?

This is a very odd problem i would hope you could find someone who could replicate it or has some idea what is going on.

Possibly it is a setting in firefox. You could also try uninstalling firefox and removing all the config files for it. The only one I know of is .firefox in your home directory.  Then when you reinstall it the setting may be default again.
good luck

Any other problems with the upgrade?

---

### Post by doctor bangali on 2007-04-02
Installed Opera in frustration, no such problem here.

---

### Post by doctor bangali on 2007-04-02
Firefox version 2.0.0.3

---

### Post by zorkerz on 2007-04-02
ephiphany is the gnome browser that prolly works as well.

---

### Post by John Wiersba on 2007-04-09
I also have this problem in Firefox 2.0.0.3 using Edgy with latest updates.  I'm using a Dell Latitude d820 laptop.  This occurs in various kinds of Firefox text boxes, such as the URL  and search boxes and this Post Reply box that I'm using right now.  It happens when I use the arrow keys to move the cursor around.  Pieces of cursor remnants are left cluttering up the text and making it almost unusable.  Any kind of screen refresh will make them go away.

---

### Post by xoltan on 2007-04-09
I'm seeing this problem in all my applications.  It happens when I highlight text or when I move the cursor around.  I also notice that when the cursor blinks it doesn't completely clear, it looks like it shrinks down to a period then back to a vertical line.  Does anyone have a fix or know what's causing the problem?

---

### Post by alanjackson on 2007-04-09
I have had the same problem in Edgy as well. Very frustrating. I suspect it is an issue with the nvidia driver myself. Does everyone with this problem have an Nvidia card?

---

### Post by smurf killer on 2007-04-09
what graphics card are you using? try getting the latest driver and make sure to get rid of the old ones first. it sounds like a graphic card problem

---

### Post by xoltan on 2007-04-09
Now that you mention it I am using an nvidia video card.  Are you using the 'nv' or 'nvidia' driver?

---

### Post by alanjackson on 2007-04-09
I use the default nv driver

---

### Post by xoltan on 2007-04-09
I'm pretty sure I'm using the same one .. I'll check when I get home.  Be sure to post a fix if you ever discover one.

---

### Post by John Wiersba on 2007-04-09
I have an NVIDIA Quadro NVS 110M.  What command(s) do you use to check the driver and how do you get the latest driver?  I don't see the graphics card in Device Manager.  I find that any screen refresh will clear it up (like minimizing the window and restoring it)

I've also got some flakey USB mouse behavior with it sometimes jumping to the edge of the screen.

---

### Post by John Wiersba on 2007-04-09
Following up on the clue about the nVidia driver, I replaced my driver by following the instructions in [ubuntuguide.org/wiki/Ubuntu_Edgy (section 1.11.2.1)]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29") and it seems to have fixed the problem.  I used Synaptic to install the nvidia-glx package and then ran sudo nvidia-xconfig.  Then I restarted Gnome with Ctl-Alt-Backspace.

---

### Post by Mitch on 2007-04-18
I just wanted to confirm that this worked for me.  I already had the nvidia-glx package installed. I just hit ctrl-alt-F1 typed "sudo nvidia-xconfig" followed by a "sudo /etc/init.d/gdm restart" and everything was great.

---

