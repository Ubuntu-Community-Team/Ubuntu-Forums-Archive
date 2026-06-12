---
title: "Screen goes blank and won't wake up!"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by chymo on 2006-08-27
I'm not sure what's going on here, probably just a setting that I can't find.  The past few mornings I've came to my ubuntu box and it is just a blank screen.  I am still able to access the files shared on that box through my windows box, so the machine isn't off and the hard discs aren't off.  Is there some kind of sleep setting that I can't find?  Or is there a certain keystroke that will awaken the system?

---

### Post by Skia_42 on 2006-08-27
> **chymo said:**
> I'm not sure what's going on here, probably just a setting that I can't find.  The past few mornings I've came to my ubuntu box and it is just a blank screen.  I am still able to access the files shared on that box through my windows box, so the machine isn't off and the hard discs aren't off.  Is there some kind of sleep setting that I can't find?  Or is there a certain keystroke that will awaken the system?

You can use the command control+alt+F2 to get into the terminal interface, it sounds like you have a problem with your graphics interface. Was it working before and did you run the update manager? I so, look [here]("http://www.ubuntu.com/FixForUpgradeIssue").

---

### Post by chymo on 2006-08-27
I've been down these streets, I have the correct version of that update.  This has just been happening recently (so leads you to think it's that update), but when I run the updates in that fix, say's its OK.  Is there any other reason the monitor sleeps and doesn't awaken?  This is a very vanilla inst. of ubuntu.

---

### Post by jordanmthomas on 2006-08-27
This isn't really a solution per se, but it's what I have to do sometimes.

1.  Press Alt + F2 and run gconf-editor
2.  Navigate to /apps/metacity/global_keybindings
3.  double click on run_command_1 and change this to some key you don't use (I put Menu)
4.  Now go to /apps/metacity/keybinding_commands
5.  double click on command_1 and type this (without quotes) "xset -display :0 dpms force on"

Now, when you press your Menu key on your keyboard, X will force your screen to turn on.  

Oh, and if you have a screensaver run and the screen is locked, you'll have to put in your password blindly first.

Hope I made sense and I hope this helps.

---

### Post by jordanmthomas on 2006-08-27
also, if you run "killall gnome-power-manager" it will stop this so you don't even have to worry about all that xset stuff.  If it does, you can disable it by running gnome-session-properties and disabling gnome-power-manager in the startup tab.

---

### Post by chymo on 2006-08-27
> root@ubuntu:/home/chymo# killall gnome-power-manager
root@ubuntu:/home/chymo# gnome-session-properties

(gnome-session-properties:6306): GnomeUI-WARNING **: While connecting to session manager:

Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gnome-session-properties:6306): CRITICAL **: gsm_protocol_new: assertion `GNOME_CLIENT_CONNECTED (gnome_client)' failed

** (gnome-session-properties:6306): WARNING **: Could not connect to gnome-session.

root@technicity:/home/lucidity#

Looks like the killall command worked, but not the session properties?  I couldn't figure out the other xset post.  Thanks for replying.  Guess I'll have to wait and see if the problem persists...

---

### Post by jordanmthomas on 2006-08-27
you shouldn't run gnome-session-properties as root.  Just run it as you and you shouldn't get the errors (assuming you are running a gnome session at the time)

---

### Post by chymo on 2006-08-27
> **jordanmthomas said:**
> you shouldn't run gnome-session-properties as root.  Just run it as you and you shouldn't get the errors (assuming you are running a gnome session at the time)

Oops.. im new ;)

---

### Post by chymo on 2006-08-28
I waited a day and when I woke up today the Ubuntu box was awake.  I went to work today and when I returned the box was awake, screensaver on.  I then accessed some files from the box via my windows pc and all was good.  I left for 2 hours and now the screen went blank.  I can access the shared files from my windows box, so Ubuntu is still running but just can't get the screen to display... Turned monitor off/on and nothing.  I have to press the reset button on my box to get it back to normal, If I had any unsaved work, all would be lost... what the heck can this be?

---

### Post by chymo on 2006-08-29
Ok, now I really need some help... This is continuing to happen...  Today, after waking up, going to work, and coming home the screensaver is on and ubuntu is fine.  I left the pc for about 2 hours, came back and the system is frozen.  This time I can't even toggle num lock key.  So could this be hardware related?  If so, why does it randomly freeze?  Are there logs to check?  Please help as I do really like ubuntu and don't want to go back to windows...

---

### Post by chymo on 2006-08-30
bump...

---

### Post by jordanmthomas on 2006-08-31
I'm not sure what to do with it freezing up on you.  When it's locked up are you able to access it from your Windows box?  If so, then it's not really frozen.  I don't think this has to do with the screen blanking, although it could.  You can check the acpi logs at:
```
/var/log/acpid
```
You can try looking through the kernel logs as well at:
```
/var/log/kern.log
```

I'm not sure what you need to look for, but if you see something that screams ERROR, maybe you could bring it up elsewhere on the forums.

Sorry I couldn't be of any more help, but I'm pretty new myself.

---

