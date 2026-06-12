---
title: "MacBookPro2,1 Almost Perfect"
date: 2011-04-25
forum: Apple Hardware Users
---

### Post by Benjamindaines on 2011-04-25
Spent a few hours today getting everything set up properly on my MacBook Pro; so far the only issues are that when I start up the digital audio jack is always on (therefore, headphones don't work).  That is fixable by installing ALSA Mixer and muting the corresponding function, but each time the system reboots the setting is lost.  Is there anyway to disable the digital audio port at start up?

Also, I am having an issue where if I place 2 fingers on the track pad to right click, it inevitably ends up scrolling away from where I want to click.  Anything I can do about this?  Some drivers out there I haven't found yet?  

--Thanks.

---

### Post by handy on 2011-04-25
I think if you start alsamixer from the Terminal with sudo, your settings will be remembered on reboot.

---

### Post by Benjamindaines on 2011-04-25
> **handy said:**
> I think if you start alsamixer from the Terminal with sudo, your settings will be remembered on reboot.

Same result as running as myself.

---

### Post by handy on 2011-04-25
What if you use the two keys ctrl , alt & F2, login & do a sudo alsamixer from out there, then come back to the GUI using ctrl , alt & F4 or whichever F# works on Ubuntu?

---

### Post by Benjamindaines on 2011-04-25
> **handy said:**
> What if you use the two keys ctrl , alt & F2, login & do a sudo alsamixer from out there, then come back to the GUI using ctrl , alt & F4 or whichever F# works on Ubuntu?

Just tried that.  The connector just unmutes itself when I log in (got to the command prompt from the login screen).

---

### Post by handy on 2011-04-25
Here are a few ways that I've found out there in the web:

**First way:**

Adjust alsamixer settings to suit you, then enter the following in the Terminal:

**sudo alsactl store**

Then edit /etc/rc.local as root adding the following line

**alsactl restore before exit 0**

Reboot.


**Second way:**

If that doesn't work, use the following in rc.local instead: 

**sleep 10 &&  alsactl restore**

Reboot.


**Third way:**

Set your settings in the Terminal & then exit.

Open terminal again & enter:

**sudo alsactl store 0**

Go to System, Preferences, Startup Applications & add a startup program as follows:

**sudo alsactl restore**

Reboot.

---

### Post by Benjamindaines on 2011-04-26
> **handy said:**
> Here are a few ways that I've found out there in the web:

**First way:**

Adjust alsamixer settings to suit you, then enter the following in the Terminal:

**sudo alsactl store**

Then edit /etc/rc.local as root adding the following line

**alsactl restore before exit 0**

Reboot.


**Second way:**

If that doesn't work, use the following in rc.local instead: 

**sleep 10 &&  alsactl restore**

Reboot.


**Third way:**

Set your settings in the Terminal & then exit.

Open terminal again & enter:

**sudo alsactl store 0**

Go to System, Preferences, Startup Applications & add a startup program as follows:

**sudo alsactl restore**

Reboot.

Third way (which I tried first) worked.

---

### Post by handy on 2011-04-26
Your welcome. ;)

Marking any of your solved threads as [SOLVED] is appreciated by the many.

---

