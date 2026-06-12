---
title: "[SOLVED] Upgraded Wine from WineHQ repo now menu shortcuts vanished"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-07
Any ideas why? also how do I role back to the official Ubuntu version if I get any other problems.

---

### Post by doomster on 2007-08-07
to return to the official Ubuntu wine version, do a 
```
sudo apt-get remove wine
``` 
then go to  /etc/apt/sources.list file and comment out the winehq repos with a "#" in front of the lines,

do a
```
 sudo apt-get update
```
and install wine from the main repos using 
```
sudo apt-get install wine
```

ps : never tried the method above, but i dont find a reason why it shouldnt work :)
have fun

---

