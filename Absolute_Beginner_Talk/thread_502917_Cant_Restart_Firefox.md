---
title: "Cant Restart Firefox"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-07-17
In one of the recent updates (past few weeks), firefox was updated. That update wiped out all of my themes and extensions. I thought I would just install them again, but no such luck. After downloading them and hitting install, it says that they will be installed when firefox is restarted. I've tried everything to restart firefox. I hit the restart firefox button in the plugin window, I closed all firefox windows and launched it again, I killed the firefox process and started it again, I restarted my computer, I even reinstalled the newest version of firefox.

Could someone please give me a hand. I can't live without my extensions.

---

### Post by Kaobear on 2007-07-17
Maybe you could list some of the extensions you are using?  Version of Ubuntu and Firefox as well?  The more information the better we can help you with your question.

---

### Post by nhandler on 2007-07-17
I've tried various extensions. Some of them are Stealther, ubufox, United STates English Dictionary, User Agent Switcher, Google Desktop for Firefox, and Download Statusbar. I have Firefox 2.0.0.4 and Ubuntu Gutsy.

---

### Post by kc0eks on 2007-07-17
> **Cheater said:**
> I've tried various extensions. Some of them are Stealther, ubufox, United STates English Dictionary, User Agent Switcher, Google Desktop for Firefox, and Download Statusbar. I have Firefox 2.0.0.4 and Ubuntu Gutsy.

perhaps one of the extensions is making firefox fail to load...maybe try safe mode for firefox?
[http://kb.mozillazine.org/Safe_mode](http://kb.mozillazine.org/Safe_mode)

then try the extensions one by one til you find the one that it doesnt like. :)

---

### Post by nhandler on 2007-07-17
Firefox loads fine. I just can't get any of the extensions to install. They just show the message that says they will be installed when firefox is restarted.

---

### Post by nhandler on 2007-07-18
Bump

---

### Post by the.phantom on 2007-07-18
you didn't say how you updated ff???

i am not a expert !!!
but what about trying

gksudo firefox?

it might at least give you a error in the term if it doesn't work?

---

### Post by nhandler on 2007-07-18
I installed/updated firefox from the terminal using 'sudo apt-get install firefox'. Running it with any form of sudo defeats the purpose. It loads the profile for root instead of my profile. As a result, no extensions will be installed.

---

### Post by nhandler on 2007-07-19
Well, I just tried doing 'sudo apt-get autoremove firefox' and then 'sudo apt-get install firefox'. This caused two of my extensions to be installed. I have compatibility errors for the other ones, and it says they will be uninstalled when firefox is restarted. They never get uninstalled. Anything I can do?

---

