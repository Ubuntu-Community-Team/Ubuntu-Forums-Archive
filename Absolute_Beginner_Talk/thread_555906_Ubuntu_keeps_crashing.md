---
title: "Ubuntu keeps crashing"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by xxhaloownerxx on 2007-09-20
Ive used ubuntu for a little under a month, and no problems so far, untill today, i booted it up, entered my keychain code, and got on gaim, then out of no where everything froze, i had to restart, then the same thing, it froze again, 2 time withen the hour! the only thing ive changed is my wireless adapter, which i got a few days ago, but its only acting up now, any troubleshooting/ help for this?

im using v 7.04 ^_^

---

### Post by jnorthr on 2007-09-20
From a terminal command line you can try dmesg and scroll to the bottom of discover kernel error messages that may help to diagnose this problem. You can also go to System>Administration>System Log. This should open an interactive session that will let you view several of the internal log files that are generated during boot and execution. There may be a few clues there as well. Post any here that appear odd.

---

### Post by xxhaloownerxx on 2007-09-20
ive had gaim off for the last hour or so, and so far i havent had a crash yet, im going to turn it back on and see what happens.

---

### Post by xxhaloownerxx on 2007-09-20
it froze again, i went to system log and found the following error for today, 3 times, and my computer has crashed 3 times, this is what i got,

E [20/Sep/2007:19:57:26 -0400] Creating missing directory "/var/run/cups/certs"

i have no idea what that means, corrupt data? missing files? beats me, anyone know anything?


im going to restore that folder, luckily  i have system backup.

EDIT: ARG i opened up GAIM again, and 30 mins later sure enough FREEZE! same error 
 
E [20/Sep/2007:21:24:53 -0400] Creating missing directory "/var/run/cups/certs"

i restored it and everything HELP!

---

