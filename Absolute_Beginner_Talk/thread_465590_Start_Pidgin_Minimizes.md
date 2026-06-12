---
title: "Start Pidgin Minimizes?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-06-05
Just a quick one, is it possible to have pidgin start up minimized in the system tray?

edit, sorry the title of the post was meant to be "start pidgin minimised?"

---

### Post by wormser on 2007-06-05
I use this set up for glipper.  It should start only in the tray but I am not 100% on this.

System> Preferences> Session - Startup Programs tab - New: give it a name and put the command in,

---

### Post by maxwellcom on 2007-06-08
> **wormser said:**
> I use this set up for glipper.  It should start only in the tray but I am not 100% on this.

System> Preferences> Session - Startup Programs tab - New: give it a name and put the command in,

Still starts maximized for me... I don't know of a  parameter that you can add to the entry in the session/startup area that will make it start minimized.

I do recall having this same problem with Gaim, and somehow got it fixed, but for the life of me I can't remember how.  One would think the same solution would work, whatever it is.

Does anyone have any ideas?

---

### Post by airtonix on 2007-06-08
investigate the use of devilspie....will post link to HOWTO shortly

---

### Post by munckfish on 2007-09-02
For Gaim I've just discovered the gaim-extendedprefs plugin has an option to force the buddy list to start minimized. I've just tested it and finally I'm released from the torture of Gaim grabbing focus as I'm typing into the Gnome Keyring prompt. Wahay!

However, I've not upgraded to Pidgin yet so I'm not sure an equivilient is available. I did however find this bug raised on the Pidgin site about this issue, with specific refs to Ubuntu and mention of a Buddy List Options plugin which may have what you're looking for:

[http://developer.pidgin.im/ticket/1888](http://developer.pidgin.im/ticket/1888)

---

### Post by freddybob on 2007-10-27
I can't see a Buddy List Options plug-in in Gutsy's Pidgin 2.2.1 - has anyone managed to get Pidgin to start minimised?

---

### Post by david.rahrer on 2007-10-27
Install pidgin-extprefs from Synaptic and enable it in the Pidgin plugin section. Minimize on startup is enabled by default.

---

### Post by freddybob on 2007-10-28
Thanks David.

---

### Post by tkrisz on 2007-10-28
I have pidgin-extprefs installed, and the appropriate box is checked. But it starts with the buddy list, any idea why?

---

### Post by AncientPC on 2007-11-26
I was running into this problem as well.

I tried using Pidgin / Extended Preferences -> start minimized.  When launching Pidgin from a terminal, it would start minimized.  However when I added it to Sessions -> Startup Programs, Pidgin would always start with a window.

I then tried delaying it using the command line "sleep 30; /usr/bin/pidgin" but that didn't work either, Pidgin wouldn't even load.

So instead I wrote a simple script with the following:
```
#!/bin/sh
sleep 5;
/usr/bin/pidgin
```

I added the script back into Sessions -> Startup Programs and now it works fine.

---

### Post by samuel.rajesh on 2007-11-26
> **tabithaboof said:**
> Just a quick one, is it possible to have pidgin start up minimized in the system tray?

edit, sorry the title of the post was meant to be "start pidgin minimised?"

Install kdocker

then at the short cut launch thing add this kdocker -m  pidgin

oops sorry pidgin can be minimised there is some option in the chat client itself , use kdocker if u want to minimise evolution or soemthing else

---

