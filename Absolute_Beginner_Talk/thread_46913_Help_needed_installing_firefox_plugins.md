---
title: "Help needed installing firefox plugins"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by AsburyPark on 2005-07-06
:? 
I have picked up a few trick thanks to everyones input.... :) 

I still can't figure out how to get downloads installed (like firefox plugins)

Help!! And thanks in advance!!!!!

---

### Post by Teo on 2005-07-06
To install plugins for FF and Tb u'll need a root's privileges, so:
1. Close FF and/or Tb.

2. **Backup** your Firefox/Thunderbird profile (coz, when we run FF/Tb as root it will mess our profiles):
- for Firefox: /home/user/.mozilla
- for Thunderbird: /home/user/.mozilla-thunderbird
(u can rename them for a second)

3. Applications -> Run Application... -> gksudo firefox
3a. Applications -> Run Application... -> gksudo mozilla-thunderbird

4. Install your plugins and/or extensions and close FF/Tb.

5. Delete root's profile folders for Tb and FF:
- for Firefox: /home/user/.mozilla
- for Thunderbird: /home/user/.mozilla-thunderbird

6. Restore your profile folders.

This is my way - it's a bit dirty, but works :)

---

### Post by neylitalo on 2005-07-29
I found that adding my user to the group 'root' fixed that quite quickly :)

---

