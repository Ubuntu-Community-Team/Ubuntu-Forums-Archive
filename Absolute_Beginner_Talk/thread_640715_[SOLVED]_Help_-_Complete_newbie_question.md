---
title: "[SOLVED] Help - Complete newbie question"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Frogster on 2007-12-14
I have installed Ubuntu and played around! I then got my network working and downloaded some applications. Ubuntu, after a restart has decided to totally change its desktop. Its now blue and has lost all it menu bars and can I figure out how to restore the original. No!

Can some kind soul help this confused man?

Regards

Frog

---

### Post by Lord_Dicranius on 2007-12-14
Does this occur everytime you reboot?  I think I know what you're describing here and it's happened to me before and a reboot has fixed it for me in the past.

---

### Post by evil316 on 2007-12-14
control - alt -backspace will restart your X server.  That might work instead of a reboot.

---

### Post by Frogster on 2007-12-14
Thank you for the reply. It happens every time. 

Swith on enter username
              enter Password
Then the default colours dissapear along with all the desktop.  What I do get instead is a button with a star like thing on it, a floppy drive, file system, Home and delete it.

---

### Post by Frogster on 2007-12-14
> **evil316 said:**
> control - alt -backspace will restart your X server.  That might work instead of a reboot.
Tried this and I like it but it didnt solve the problem. Thank you for the suggestion

---

### Post by Lord_Dicranius on 2007-12-14
Do you have any desktop effects enabled (compiz fusion)?

Are you able to open any applications?  If so, try and open gnome-system-monitor (by either typing that into a terminal, or into a run dialog box (ALT + F2)) to check on the daemons (processes), see if any of them are eating up a lot of CPU usage.  If any are, which ones are they?

And I'm assuming your using the Gnome desktop (default install of Ubuntu)?

---

### Post by Frogster on 2007-12-14
At present I am unable to do anything at all. All that is now on the screen is "program manager." Currently thinking that a clean install is the easiest option :-) I couldnt even (ALT + F2) as you suggested.  I think I may have partly installed and then uninstalled something called xfce, so I may not be in the Gnome desktop.  

*Shakes head* and wonders at the learning curve

---

### Post by Law506 on 2007-12-14
sound like you might of added some xfce or kde things into your desktop causing some conflict.

if you can, go into synaptec and search for kde and xfce and gnome and see what you have installed and if you do have more than one, uncheck them till gnome is left.  

i dont know to much about this, so anyone else feel free to chime in and correct me if need be or add to this suggestions.

---

### Post by llamakc on 2007-12-14
Or just change the session from the login manager.

---

### Post by siciliancasanova on 2007-12-14
Yeah the way you describe it, it sounds like you have installed something that is conflicting with the gnome environment.

---

### Post by Frogster on 2007-12-14
I think you all  maybe correct. Unfortunately, I cant seem to launch anything.

---

### Post by Law506 on 2007-12-14
> **Frogster said:**
> At present** I am unable to do anything at all**. All that is now on the screen is "program manager." Currently thinking that a clean install is the easiest option :-) I couldnt even (ALT + F2) as you suggested.  I think I may have partly installed and then uninstalled something called xfce, so I may not be in the Gnome desktop.  

*Shakes head* and wonders at the learning curve

After reading that, and you dont have any important info on the HDD, reinstalling might be the best bet.

---

### Post by llamakc on 2007-12-14
Can you get to the login manager?

---

### Post by Frogster on 2007-12-14
> **Law506 said:**
> After reading that, and you dont have any important info on the HDD, reinstalling might be the best bet.

No, nothing Important on the drive as the whole machine was built from spares to get used to Ubuntu

---

### Post by Frogster on 2007-12-14
> **llamakc said:**
> Can you get to the login manager?

Showing my complete and utter newness to the distro, where would I find that?

---

### Post by llamakc on 2007-12-14
When you turn the computer off, and it restarts. Is there a screen where you type your name and password in?

If there is, there will be a button/choice for "session" or 'session type'. 

What are the options?

---

### Post by Frogster on 2007-12-14
> **llamakc said:**
> When you turn the computer off, and it restarts. Is there a screen where you type your name and password in?

If there is, there will be a button/choice for "session" or 'session type'. 

What are the options?

You are a star.

Found the options button that I had not noticed and have made Gnome the default option. Hey presto I got that desktop back. 

Now I just have to work out how to not do the same thing again! Its a problem of small brain and to much computer power :-)

One thing has been proved and that is the helpfulness of the community, thank you all for your help and patience

---

### Post by Lord_Dicranius on 2007-12-14
Good call, llamakc.  Glad to hear you got it working, Frogster :)

Remember to mark the thread as solved from the "thread toosl" menu near the top.

---

### Post by Frogster on 2007-12-14
> **Lord_Dicranius said:**
> Good call, llamakc.  Glad to hear you got it working, Frogster :)

Remember to mark the thread as solved from the "thread toosl" menu near the top.

Thank you

---

