---
title: "[SOLVED] Ubuntu 7.1-I hate to be ignorant but how do I shut down computer?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by jmucha on 2007-11-22
where is shut down button-log off doesn't do the trick

---

### Post by COLiNx86 on 2007-11-22
You see the top panel? not all the way to the right there should be a man running or a power button.

---

### Post by bumanie on 2007-11-22
There is a red power button next to the clock in the very right hand corner at the top of the screen.

---

### Post by jmucha on 2007-11-22
I know, none of the choices log me out as Windows does, I have to do a cold shut down or type in sudo halt. That can't be right!

---

### Post by gali98 on 2007-11-22
did you disable the power manager in either the session manager or the services manager?
And what choices do you have?
Kory

---

### Post by bromix on 2007-11-22
When you open your main menu, is there not a "Quit" option there?  Alternatively, you can right click your top panel, choose "Add to Panel", and choose the red "Quit" button there, adding it easily that way.

---

### Post by gali98 on 2007-11-22
> **bromix said:**
> When you open your main menu, is there not a "Quit" option there?  Alternatively, you can right click your top panel, choose "Add to Panel", and choose the red "Quit" button there, adding it easily that way.

I think you're talking of KDE. I don't think that is what the user is using.

---

### Post by bromix on 2007-11-22
> **gali98 said:**
> I think you're talking of KDE. I don't think that is what the user is using.

No, I haven't used KDE for almost a year. This is Gnome.

---

### Post by gali98 on 2007-11-22
Oh....
Never Mind I know what your talking about now..... Just kidding. I guees I just never use that.
Anyway, I know that when I shut off the power manager then I had trouble with the shutdown utility.

---

### Post by AvengingAngel718 on 2007-11-22
[QUOTE=gali98;3816577]did you disable the power manager in either the session manager or the services manager?

I have this same problem and can't figure out how to fix it. My options under the quit button are log out, switch user, lock screen, hibernate, and suspend. Shut down and Restart are no longer there and i'm not sure what i did to change it. I've been using linux for a long time now, but this is one thing i can't figure out :/

---

### Post by jmucha on 2007-11-22
the quit button is missing and I have no idea re session mgr or whatever, I'll try adding the button

thanks

---

### Post by jmucha on 2007-11-22
power down button is missing in quit

---

### Post by akiratheoni on 2007-11-22
Well you could always try in the terminal:

```
sudo shutdown -h now
```

Or to restart:

```
sudo shutdown -r now
```

---

### Post by gali98 on 2007-11-22
> **AvengingAngel718 said:**
> [QUOTE=gali98;3816577]did you disable the power manager in either the session manager or the services manager?

I have this same problem and can't figure out how to fix it. My options under the quit button are log out, switch user, lock screen, hibernate, and suspend. Shut down and Restart are no longer there and i'm not sure what i did to change it. I've been using linux for a long time now, but this is one thing i can't figure out :/

I haven't had this problem...(yet.. The power manager seems quirky on my machine.)
I have had some options disappear only to reappear after a reboot or even just canceling and reopening it again. I'm not sure what causes this. All I can tell you is that make sure you are updated. I know Gnome has been getting some updates lately.

@jmucha
The session manager is (in the top panel)
System>Preferences>Sessions
The Services is
System>Administration>Services
In both of these basically make sure anything saying something about power is checked. (don't uncheck anything as you could run into some major problems.)
If there is no power button in the top right hand corner of the screen you can go to 
System>Quit...
If this does not work go to the command line and do:
sudo shutdown -r now
after you reboot and log in the shutdown utility should work. (should is the key word here)
I hope this helps someone.
Kory

---

### Post by jfinkels on 2007-11-22
Did you start X by typing:```
startx
```? If you did, you will not have the "Shut Down" option. To get the Shut Down and Restart option, you need to log in using the graphical login manager, "gdm" (the big "Ubuntu" logo with the text box for you to enter your username and password).

---

### Post by bromix on 2007-11-22
I remember losing my shutdown and restart once in Feisty, here's what fixed it for me.


   1. From the top menu bar choose System
   2. Select the Administration menu option
   3. Then choose the Login Window menu option
   4. Enter your password when prompted
   5. Select the Local tab
   6. Check the box next to Show Actions Menu
   7. Make sure Include Host Names below it is checked as well

That’s it!  The Shutdown and Restart options will magically reappear!  Hope this helps…

---

### Post by jmucha on 2007-11-22
no power button no walking man-nada

---

### Post by gali98 on 2007-11-22
> **jmucha said:**
> no power button no walking man-nada

Do what either I or bromix said (or both) 
and if it doesn't show up then then use the command line line to restart and see if it works then
"sudo shutdown -r now"
Kory

---

### Post by jmucha on 2007-11-22
i did enable power mgr, checckec session mgr.but on reboot still no power options appear-

---

### Post by gali98 on 2007-11-22
> 1. From the top menu bar choose System
2. Select the Administration menu option
3. Then choose the Login Window menu option
4. Enter your password when prompted
5. Select the Local tab
6. Check the box next to Show Actions Menu
7. Make sure Include Host Names below it is checked as well

Did you do this?

---

### Post by jmucha on 2007-11-22
gali 98 did the trick-thanx a miilion tomorrow, i get my wireless working-happy thanxgiving!!

---

