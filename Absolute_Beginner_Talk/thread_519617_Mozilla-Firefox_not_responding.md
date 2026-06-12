---
title: "Mozilla-Firefox not responding"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by orangemoose on 2007-08-07
Every time I start Firefox or Thunderbird I get amessage that says it is already running but not responding.

I'm running Ubuntu 7.04, Gnome Desktop.

Thanks for any assistance.

---

### Post by Cypher on 2007-08-07
Open a terminal by going to Applications->Accessories->Terminal and type the following
```

ps -eaf | grep firefox
ps -eaf | grep thunder

```
This will tell you if either of those apps are indeed running.

---

### Post by FuturePilot on 2007-08-07
For Firefox```
killall firefox-bin
```
I'm not sure for Thunderbird but I'm guessing
```
killall thunderbird-bin
```

---

