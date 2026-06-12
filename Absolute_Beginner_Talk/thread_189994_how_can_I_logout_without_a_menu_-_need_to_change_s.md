---
title: "how can I logout without a menu - need to change sessions"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by mike_m on 2006-06-05
I just got xubuntu installed & had the idea to try fluxbox desktop, but when it loaded I had no menu or icons to log back out.:roll: 

Unfortunately I'm set to auto login & I had clicked to make fluxbox my default session, I would like some help to logout to change my sessions back.:???: 

I can ctrl+alt+F2 to get to the terminal but don't know what to type,
logout gives an error & says to type exit, then exit sends me back to fluxbox](*,) 

Thanks in advance for your help, Mike

---

### Post by psquared89 on 2006-06-05
To kill an X session (note the word kill, this is not a nice way of doing it and under normal usage, X wouldn't appreciate this...) you have a few options:

From the frozen / screenless shell: Press Ctrl-Alt-Backspace
From the command line: killall -HUP (g,k,x)dm  <-- "-HUP" will restart gdm, kdm, or xdm as appropriate ("gnome/kde/xfce display manager")

---

### Post by shamrock_uk on 2006-06-05
Heh, yeah, fluxbox can appear quite minimal at first!

There's no 'start menu' as such; instead you bring up the menu by right-clicking on the desktop. 

If nothing happens, then you haven't got a fluxbox menu installed. It's just a text file, so you can either copy the example from /usr/share/docs/fluxbox to your home directory (there should be instructions there) or this link will help:

[http://wiki.linuxquestions.org/wiki/Fluxbox_Menu](http://wiki.linuxquestions.org/wiki/Fluxbox_Menu)

To be honest, it's going to be easier to get a basic fluxbox menu and run **sudo gdmsetup** from there than it will be to sort this out from the command line. 

You could maybe try Alt+F2 to see if it gets you a run dialog, I can't remember whether that's a gnome-only thing though. 

Once you're at gdmsetup, disable auto-login, reset your default session and then enable it again. 

By the way, if you want to have a good go at fluxbox for your desktop, then you need to pull in all the associated packages to give you some bells and whistles. I have a feeling **fluxconf** may even give you a menu editor now, but it's been a while since I've used it. It's probably too minimalistic for someone not comfortable with the command line and editing text configs.

---

### Post by mike_m on 2006-06-05
Thanks psquared89 & shamrock_uk !!
Ctrl-Alt-Backspace put me back at login & I was able to login to Xubuntu & fix the fluxbox menu.

shamrock_uk was right as to it being too minimalistic for a beginer like me, But I'm learning :)

Thanks again, Mike

---

### Post by shamrock_uk on 2006-06-07
[QUOTE=mike_m]Thanks psquared89 & shamrock_uk !!
Ctrl-Alt-Backspace put me back at login & I was able to login to Xubuntu & fix the fluxbox menu.

shamrock_uk was right as to it being too minimalistic for a beginer like me, But I'm learning :)

Thanks again, Mike[/QUOTE]

That's interesting, so when you kill the XServer manually, it doesn't log you in automatically? I just assumed it would!

That's a nice feature I guess...

---

### Post by Psquared on 2007-01-22
I installed Fluxbuntu using the 6.06 kernel instead Feisty Fawn - no logout there either. It does not use GDM when installed this way. It has its own login manager which does not provide for "restart" "reboot" or other "sessions." Its in development so I suppose this will be added. I just logout, and then cntl-alt-f2 and then login as user and then "shutdown -r now" to reboot my machine to the Grub menu.

---

