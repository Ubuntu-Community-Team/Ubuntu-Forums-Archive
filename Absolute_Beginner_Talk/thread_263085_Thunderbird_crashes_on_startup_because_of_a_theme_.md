---
title: "Thunderbird crashes on startup because of a theme and I can't uninstall it too"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by brnn on 2006-09-22
I use Kubuntu 6.06. I installed Thunderbird. It worked fine, unless I installed a theme (Mostly Crystal) on it (it's a theme which works fine on Firefox). However, after I applied the theme as soon as I start Thunderbird it crashes. Because of this I can't change the theme. In Windows there was Safe Mode for Mozilla apps, but I don't know where to search for it here... 

Please help - I don't wish to reinstall Kubuntu every time I encounter a buggy theme...

---

### Post by mitch.c on 2006-09-22
> **brnn said:**
> In Windows there was Safe Mode for Mozilla apps, but I don't know where to search for it here... 

Please help - I don't wish to reinstall Kubuntu every time I encounter a buggy theme...
Never tried safe mode, but if it's available for Thunderbird, open a terminal and type:
```
mozilla-thunderbird -safe-mode &
```
Let me know if it works!

---

### Post by brnn on 2006-09-25
No - ```
mozilla-thunderbird -safe-mode &
brnn@brnn-desktop:~$ mozilla-thunderbird -safe-mode &
[1] 5142
brnn@brnn-desktop:~$ bash: mozilla-thunderbird: command not found

```

:-? :confused:

---

### Post by mitch.c on 2006-09-25
> **brnn said:**
> No - ```
mozilla-thunderbird -safe-mode &
brnn@brnn-desktop:~$ mozilla-thunderbird -safe-mode &
[1] 5142
brnn@brnn-desktop:~$ bash: mozilla-thunderbird: command not found

```
Then try:
```
thunderbird -safe-mode &
```

---

