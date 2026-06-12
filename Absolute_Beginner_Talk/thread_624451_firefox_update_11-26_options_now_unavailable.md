---
title: "firefox update 11-26 options now unavailable"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by keenjoe on 2007-11-27
Hello Everyone,

I'm new to Ubuntu (and Linux...3 days now), so patience is appreciated.

I elected to update when prompted today. I now notice that firefox is missing 'options' under 'tools', and 'help contents' under 'help' now displays the following error message:

         XML Parsing error: not well-formed
         Location: chrome://help/content/help.xul
         Line number 1, Column 2

Thanks in advance for any assistance.

keenjoe

---

### Post by FuturePilot on 2007-11-27
Try this
```
mv .mozilla .mozilla_old
```
This will basically rename your Firefox profile to .mozilla_old. When you restart Firefox it will create a new profile. Sometimes they get corrupted.
If that didn't work and you want your old profile back just do this
```
mv .mozilla_old .mozilla
```

---

