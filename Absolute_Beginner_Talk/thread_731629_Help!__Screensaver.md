---
title: "Help!  Screensaver"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-03-22
No matter what I try, I can't get the screensaver of my computer to stop coming on.  I have looked in power settings, everywhere.  I'm trying to watch a movie without getting up every 20 minutes.  How can I turn this screensaver off?!
I'm running on a laptop if it makes any difference.

---

### Post by FreewareFan on 2008-03-22
I hate to ask the obvious, but did you check the settings in System - Preferences - Screensaver??

---

### Post by Malta paul on 2008-03-22
Hi, I must admit I don't know how to disable the screensaver, but when I watch a Video I move the time slider to its maximum of 2 hours :)

---

### Post by ad_267 on 2008-03-22
> **Malta paul said:**
> Hi, I must admit I don't know how to disable the screensaver, but when I watch a Video I move the time slider to its maximum of 2 hours :)

Under System -> Preferences -> Screensaver there should be an option for "Activate Screensaver when computer is idle"
There is for me on Gutsy

---

### Post by FreewareFan on 2008-03-22
> **ad_267 said:**
> Under System -> Preferences -> Screensaver there should be an option for "Activate Screensaver when computer is idle"
There is for me on Gutsy

Correct.  This is the way to disable the screensaver.  If that checkbox is checked, then the screensaver will kick in at the time specified by the slider just above it.  If that box is not checked, then the screensaver will never kick in, effectively rendering it disabled.

---

### Post by ~&#730;JaZ&#730;~ on 2008-03-22
hi! i have the same problem...and i tried all that has been described in this thread...any other ideas....pls...because u cant rally imagine how disturbing that is...to watch a movie....and the screensaver goes on every 10 min....

---

### Post by ~&#730;JaZ&#730;~ on 2008-03-22
hi...me again...i dont think that there is a problem with the screensaver...because its not the screensaver that goes on...its the monitro that goes off, like power sawing...but i have chacked the power saving settings...they are all set never to go on...so...again pls...any help...

---

### Post by FreewareFan on 2008-03-22
OK, if it's not a screensaver, then try this:

Open a terminal, and paste in the following code:

xset dpms 0 0 3600

Then go back to watching a movie.  If you monitor does not go blank, then you can make a launcher and paste that same code into it as the command.  Use that launcher to prevent your monitor from blanking whenever you want to watch a movie...  

Hope this helps!

FwF

---

### Post by ~&#730;JaZ&#730;~ on 2008-03-22
nop....that didnt work...my monitor just torns off every 10 min....

---

### Post by FreewareFan on 2008-03-22
Hummm...   I'm outta ideas for you.  Maybe someone else will have a better idea of what's going on with your monitor...   Hope you figure it out!

---

### Post by Schalken on 2008-03-22
I also have to ask the obvious, have you tried going to System > Preferences > Power Management and moving the slider under "Display, Put display to sleep when inactive for:" all the way to the right so it says "Never"?

---

### Post by ~&#730;JaZ&#730;~ on 2008-03-22
tnx anyway;):P....hmmm....i am geting used to it by now...hehe...i hope my problem might go away with the new distro....:P

---

### Post by jordank on 2008-03-23
Alright.  I have set the power management to Never, 2 hours, don't idle all that stuff. Played around in screensaver and power management and screensaver.  THE PROBLEM IS NOT IN THERE.  as said before, it's not the screensaver that goes on, but the monitor that goes off.   if anyone knows how to disable this so i can watch my movie without having to get out of bed every 10 minutes that would be so helpful.

---

### Post by jordank on 2008-03-23
also, I tried:

xset dpms 0 0 3600

that did nothing :S

Any ideas would be appreciated to get this working.

It's a Dell Inspiron 6400

---

### Post by FreewareFan on 2008-03-23
OK, a thought just came to me...  Perhaps you don't have dpms enabled on your system.  Here's a quick way to find out...  Fire up a terminal, and type in the following code, then hit enter...

xset dpms 0 0 5

Now, make SURE that you don't move the mouse, or touch any keys after you press Enter.  

You should see your monitor go totally blank in 5 seconds after you press Enter.

If it does go blank, you can just move the mouse to come out of it.

Let me know.....

---

### Post by jordank on 2008-03-23
Tried three seperate times, waiting about 12 seconds after each attempt.  Nothing causes my screen to go black.  It just stays at the terminal.


kristie@kristie-laptop:~$ xset dpms 0 0 5
kristie@kristie-laptop:~$ xset dpms 0 0 5
kristie@kristie-laptop:~$ xset dpms 0 0 5


i'm assuming dpms isn't set?

---

### Post by FreewareFan on 2008-03-23
Looks like it's not enabled.  To enable it, get to a terminal, and enter the following code:
```
sudo gedit /etc/X11/xorg.conf
```

When your xorg.conf file comes up in the editor, look for the following section, and make the section look like this.  Note:  Your monitor may have a specific name as an Identifer.  IF so, leave it as it is, and only add the Option line:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

```

When that's done, save, and exit the editor...

Now you can log off, or reboot, and when you get back to your desktop, try the command again of   ```
xset dpms 0 0 5
```

See if your monitor will blank now....

---

### Post by FreewareFan on 2008-03-24
Well, did it work?

---

### Post by jordank on 2008-04-08
The part in the xorg was already set to this:


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection


What should I do from here?

---

### Post by paydaydaddy on 2008-04-08
Have you checked the bios settings? There is probably an area in your bios that deals with "resource management". Name varies from board to board. An improperly ticked option in the bios may be causing your screen to go into power saving mode.

---

