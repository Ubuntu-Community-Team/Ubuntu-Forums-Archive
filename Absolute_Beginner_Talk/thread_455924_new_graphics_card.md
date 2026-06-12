---
title: "new graphics card"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by snyling on 2007-05-27
OK so I bought a Nvidia 6600 to replace my current outdated card. Everything slots in fine but upon turning on the computer the monitor stays blank with the orange light. I doubt it's the monitor refresh rates or anything because it's a brand new new Acer LCD. I also don't know how it could be any BIOS setting because I had the onboard adapter disabled with the old card. Any help would greatly appreciated.

---

### Post by JavaIsRobust on 2007-05-27
This is just a guess, but is there a power connector on the card that you were suppose to or forgot to plug in?

---

### Post by alienexplorers on 2007-05-27
Do you have the most current Nvidia drivers installed.  If not try the Envy script.
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by snyling on 2007-05-27
Javaisrobust was right it was a power issue. However now when I try to get into gnome I get a very wierd error. It says something about the card not being configured. The error message is bordered by strange letter characters. Is this a known issue? How would I go about configuring the card.

---

### Post by JavaIsRobust on 2007-05-27
I'm a noob at linux but this is what I would do in your case.  Under grub, boot into your restore mode or whatever it's called.  Then at the command prompt type in

sudo dpkg-reconfigure -phigh xserver-xorg

It should bring up a blue screen with some options.  Just choose vesa or whatever is defualt.

That should bring your xorg.conf file to it's orginal.

Then type reboot or reboot your system however you can.

Then start your system like normal and you'll probably have to reconfigure your xorg.conf file to use which ever drivers you want.

---

### Post by snyling on 2007-05-27
when I get into grup it skips straight into ubuntu. What do I do to get into the restore mode?

---

### Post by JavaIsRobust on 2007-05-27
Hmm, I don't know the shortcut keys for grub.

Try... when you get the part where your screen is all messed up.

press Ctrl+alt+F1

I think any of F1 through F6 should work, maybe F2, I don't know

That should bring up a terminal type screen.  From there see if you can type in the dpkg reconfigure xorg command

---

### Post by snyling on 2007-05-27
ok so I got into the recovery mode by pressing ESC before GRUB had a chance to start ubuntu. I typed in what you said and pressed enter. I picked the default as you said and pressed enter. The next screen puzzles me however. It's talking about resolutions so I did what it told me. I typed reboot but the computer just restarts and comes up with the same error. Is there something I did wrong with the resolutions screen?

---

### Post by JavaIsRobust on 2007-05-27
No.  I thought your xorg.conf file was setup for your old graphic card and giving you a problem.  I had to do that early today and it worked for me with a similar issue like yours.  Are you sure your power supply has enough wattage for your new card?

---

### Post by snyling on 2007-05-27
I'm going to be perfectly honest, I have no idea how much the card requires. All I know is that I have a 250watt PSU. Anywho I'm not to pushed as it's not like I do any graphics intensive work on the computer. Thanks for the help anyway.

---

### Post by snyling on 2007-05-27
OK big problem, the error comes up with my old card. Possibly because I tried to change that xorg-conf file. Please help.

---

### Post by quinnten83 on 2007-05-27
snyling, try setting the default path depht to something lower in the xorg.conf, maybe 16 instead of 24
and if you could like write down the contents of the resolution and default depht parts of your xorg.conf, perhaps someone else might be able to help you.

---

### Post by snyling on 2007-05-27
thanks for the reply. How do I access the file to find out all of that and change that value?

---

### Post by snyling on 2007-05-27
I'm going to try to reinstall ubuntu with the new card in it. Maybe starting from scratch is the ticket

---

### Post by JavaIsRobust on 2007-05-27
Editing the xorg file the way you did shoudn't cause the same issue with the old card.

to edit your xorg file

pico /etc/X11/xorg.conf

---

### Post by snyling on 2007-05-27
thanks, I'm installing again with the 6600 in the machine. Seems to be working.

---

### Post by snyling on 2007-05-27
Ubuntu finished installing. Everything is working fine now. Thanks for everyone's help.

---

