---
title: "Starting apps when logging in"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by rafciu123 on 2007-02-19
Hi,

I want to start a couple of application when I get logged in:
-Skype
-Firewall
-Gmail Notifier
-and couple of others

I followed instructions described here but it didn't work.

[http://ubuntuforums.org/showthread.php?t=97864](http://ubuntuforums.org/showthread.php?t=97864)

I copied shortcut of skype here /usr/share/autostart/ and it doesn't start when log in.
I can start application by doubleclicking it from that location dough so the link is valid.

Please advice.

Just to make myself clear - I want to start those apps automatically.

---

### Post by pgilmon on 2007-02-19
Well, if you are using gnome (if you installed ubuntu and not kubuntu you are using gnome by default), just do this:

System -> Preferences -> Sessions

No go to tab "Startup programs" and add the commands you want to automatically execute when gnome (the desktop environment) starts.

You must enter commands there, that is, to start skype just add "skype" to the list of startup programs. "Skype" won't work (beware of capital letters). If you want to know if a certain command actually starts a program, just open a Terminal (Applications -> Accessories -> Terminal) and type the command there. If it works int he terminal, it will work in the startup program list.

---

### Post by rafciu123 on 2007-02-19
I do as you say and I see skype in startup programs list. Then I close Sessions tool and start it again and skype is not there. I even did sudo gnome-session-properties and tried to add skype but effect was the same.

---

### Post by pgilmon on 2007-02-23
I think sudo won't help in this case. I don't know why that happens. It should stay there...

---

