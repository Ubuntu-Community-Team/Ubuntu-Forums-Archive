---
title: "Booting with wifi-radar"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by soulbreak on 2007-08-31
I want to have wifi radar run at startup because I think its better than the default network manager.  However, when I added it to the sessions startup I couldn't even get my panel to load at startup! I ended up having to login under the terminal and remove it manually from "~/.config/" the error that caused it was that when it ran the command at startup it didn't have su access.  Would this be corrected if I just put sudo in front of the command in sessions? Or would that just make me have to enter my password at startup all the time...

Also, how do I get it to auto enter in my keyring password when connecting to my wep network?

---

### Post by diatribe on 2007-08-31
you would need to use gksudo or else it would not prompt for your password, but you could rpobably have it run at startup by adding an entry to your /etc/init.d file

---

### Post by 5-HT on 2007-08-31
> **soulbreak said:**
> I want to have wifi radar run at startup because
You can daemonize it on boot by adding ```
 wifi-radar -d &
``` to your /etc/rc.local
> **soulbreak said:**
> 
Also, how do I get it to auto enter in my keyring password when connecting to my wep network?
Add it into the appropriate entry in your wpa_supplicant.conf. 
cheers,

---

### Post by AlexenderReez on 2007-08-31
actually wifi-radar work automatically by itself in startup...no need to add autostart or whatever.....

---

### Post by 5-HT on 2007-08-31
Are you sure of that? I've always had to configure it to start on boot. Perhaps Ubuntu included a startup script in init.d/? (running a diff distro ATM)

---

### Post by soulbreak on 2007-09-01
where would wpa_supplicant.conf be located?
TY

---

### Post by 5-HT on 2007-09-02
> **soulbreak said:**
> where would wpa_supplicant.conf be located?
TY
Should be in /etc. It's really well documented with options and examples.
Cheers,

---

