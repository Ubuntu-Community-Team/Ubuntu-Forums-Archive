---
title: "Firefox"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by RobotAlligator on 2007-11-30
I'm coming off a fresh install of ubuntu with firefox version 2.0, and I can't click on any button.  Preferences dont work, I can't download anything, etc.  Heres the GENERAL error, but it changes with each button

XML Parsing Error: syntax error
Location: chrome://mozapps/content/extensions/extensions.xul
Line Number 1, Column 1:

How am I supposed to do anything without being able to download things?:confused:

---

### Post by Nano Geek on 2007-12-01
Unless you have something you want to save in Firefox, run this to clear anything that might have gone wrong.```
rm -r ~/.mozilla/firefox/
```

---

### Post by alienexplorers on 2007-12-01
Create a new profile using > firefox -profilemanager.  Then migrate over your extensions, ect. to the new profile.
> [http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

---

