---
title: "evolution error"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by mikawber on 2007-10-27
I make a backup of my Feisty install every Friday. I started messing with some stuff last night and it screwed up my computer. I just restored the installation from the image. Everything is fine but when I try to open Evolution it doesn't open. I tried running it from terminal and this is what I get.

```
CalDAV Eplugin starting up ...

(evolution-2.10:8460): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:8460): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:8460): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:8460): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:8460): e-data-server-CRITICAL **: e_source_group_peek_base_uri: assertion `E_IS_SOURCE_GROUP (group)' failed
Segmentation fault (core dumped)
```

Any ideas why this is happening? Thanks

---

### Post by t.septekin on 2007-10-28
Same problem here. In Gutsy I was having problems with OpenOffice.org so decided to revert back to Feisty, did a complete installation. OOo is now behaving but Evolution is lost. Attempted an apt-get install which reported that my installation was up to date. Running evolution in Terminal gave the results listed by "mikawber".
??

---

### Post by mikawber on 2007-10-28
I didn't state in the first post but after I screwed stuff up I tried Gutsy. I was having video issues in Gutsy and didn't have time to mess with it so I reverted back using my image. This is when evolution started messing up.

---

### Post by t.septekin on 2007-10-29
Our common denominator seems to be Gutsy/Feisty switch. My system is working fine now. This is what I've done:

Did a clean installation, formatting my /home partition as well. I then copied the contents of my home folder from yesterday morning's backup and the problem re-appeared! I Repeated the clean installation but this time copied the last week's home folder and Evolution is working fine. I then copied just the .evolution folder from yesterday's backup to bring my Mail, Contacts and Calendars up to date and after a few error messages in Mail everything is working properly now. I installed the Feisty updates only after confirming that Evolution was working but the precaution was not necessary as the updates are blameless. I shall be keeping well away from Gutsy for a month or so.

Good luck with your system.

---

### Post by mikawber on 2007-10-29
I just managed to get this to work about 5 minutes ago. First I removed evolution, then all I had to do is run the following commands:
```
rm -r ~/.gconf/apps/evolution/
gconftool-2 --recursive-unset /apps/evolution
```

After that I reinstalled evolution and it started working perfectly. Sorry I found this so late and you had to do a complete reinstall.

---

### Post by t.septekin on 2007-10-29
Glad to learn that you are ok! No problem with the full installation, it helps to clear accumuleted rubbish.

All the best.

---

