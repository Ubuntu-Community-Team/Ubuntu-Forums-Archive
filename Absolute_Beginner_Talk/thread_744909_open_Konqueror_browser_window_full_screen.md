---
title: "open Konqueror browser window full screen"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2008-04-04
Anybody know how to make Konqueror open browser windows full screen. Using Kubuntu 7.10. Firefox does it by default, but sometimes I prefer Konqueror. A minor irritation, I know, but it would be nice not to have to click every window to maximize after it opens. So far I haven't found anything in settings to handle this.

---

### Post by amingv on 2008-04-04
Here's a dirty solution: K Menu > Internet > (right click on) Konqueror > Edit Item

Make note of the line that says "command", just in case, then replace it forthis:
```
konqueror --geometry 1024x728
```

where 1024x728 is your actual resolution. Close it and save changes, give the same treatment to any Konqueror shortcut.

Of course, this is not effective if you use Katapult. Also I did not bother looking at the Konqueror options since I understand you looked there first (if you didn't, do check them. I don't use Konqueror as a web browser)

Anyhow, hope it helps.

---

### Post by paydaydaddy on 2008-04-04
Thanks, I will keep you suggestion as an option, but will give a chance for others to chime in with suggestions before giving it a try.

---

### Post by paydaydaddy on 2008-04-04
bump

---

