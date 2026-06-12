---
title: "Suspend and other power management broken in Intrepid"
date: 2008-11-19
forum: Apple Hardware Users
---

### Post by spencercarran on 2008-11-19
Macbook 3,1 Santa Rosa, Ubuntu 8.10.

Yes, I know that System>Preferences>Power Management allows options to adjust these settings. However, that's not working for some reason. I have the setting to "Blank Screen" when the laptop lid is closed on AC power, and to "Suspend" when the laptop lid is closed on battery power. Neither of these happens, and when my computer goes to sleep after a period of idleness it does not wake up on opening the lid or pressing a key, and needs to have the power turned off and then restarted. These settings were working properly until recently, and as far as I know I have not done anything which should have affected them. Any ideas on what is wrong or how to fix it?

---

### Post by spencercarran on 2008-11-19
No ideas then? This is basically making Ubuntu unusable unless I turn my computer off any time I'm not using it for some period of time, so unless I find a solution to this it's looking like I'll have to make a clean install.

---

### Post by regebro on 2008-11-20
The suspend worked for me, when I tried it juts now. When on AC Power however, closing the lid will turn off the screen just for half a second, and then it will go on again, so there is clearly something broken there.

---

### Post by spencercarran on 2008-11-20
> **regebro said:**
> The suspend worked for me, when I tried it juts now. When on AC Power however, closing the lid will turn off the screen just for half a second, and then it will go on again, so there is clearly something broken there.

Initially following my install, and for a couple weeks after, suspend, hibernate, and everything else was working perfectly and now none of it is functioning.:confused:

---

### Post by regebro on 2008-11-20
> **regebro said:**
> The suspend worked for me, when I tried it juts now. When on AC Power however, closing the lid will turn off the screen just for half a second, and then it will go on again, so there is clearly something broken there.

And a reboot later, this also works now. Hmm...

Ah! I got it. If you close the lid and then move the external mouse, the screen will turn on again!
That must be a bug.

---

### Post by spencercarran on 2008-11-20
> **regebro said:**
> And a reboot later, this also works now. Hmm...

Ah! I got it. If you close the lid and then move the external mouse, the screen will turn on again!
That must be a bug.

But I don't have an external mouse... and that still doesn't explain inability to suspend and hibernate. Oh well, reinstalling doesn't take long. I know what I'm doing this weekend... let's just hope I don't break my MBR again.

---

### Post by regebro on 2008-11-21
Yeah, your problems is unrelated to mine, mine is this bug:
[http://bugzilla.gnome.org/show_bug.cgi?id=517925](http://bugzilla.gnome.org/show_bug.cgi?id=517925)

---

