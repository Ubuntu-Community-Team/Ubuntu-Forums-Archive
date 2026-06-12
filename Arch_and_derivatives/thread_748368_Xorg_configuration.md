---
title: "Xorg configuration"
date: 2008-04-07
forum: Arch and derivatives
---

### Post by Gauvenator on 2008-04-07
When I start X it automatically goes to 1920x1080 (not my native res).  In order for it to go to my desired settings I have to enter nvidia-settings, which puts it to my desired resolution automatically.  I don't have to mess with any settings, it just automatically goes to the res I configured when I open it.

How can I make it so that it goes to that resolution by default without entering nvidia-settings every time I go into X?

---

### Post by Rumor on 2008-04-08
Have you tried editing your xorg.conf file to set the resolution you desire?

Which method did you use to generate the file?

---

### Post by kpkeerthi on 2008-04-08
Open nvidia-settings in super-user mode, change your desired resolution and click on "**Save to Xorg**" button. This will write the resolution changes to xorg.conf and should stick after reboot.

In a terminal, type
```

gksu nvidia-settings <press-enter>

```
**or**
```

su <press-enter>
nvidia-settings <press-enter>

```

---

### Post by Gauvenator on 2008-04-08
> **Rumor said:**
> Have you tried editing your xorg.conf file to set the resolution you desire?

Which method did you use to generate the file?

I used nvidia-xconfig as root, then edited our my undesired resolution.

> **kpkeerthi said:**
> Open nvidia-settings in super-user mode, change your desired resolution and click on "**Save to Xorg**" button. This will write the resolution changes to xorg.conf and should stick after reboot.

In a terminal, type
```

gksu nvidia-settings <press-enter>

```
**or**
```

su <press-enter>
nvidia-settings <press-enter>

```

I'll try that again.

---

### Post by Gauvenator on 2008-04-08
OK didn't work.  It still defaults to a different res upon entering the X server.  But once I enter nvidia-settings it automatically goes to my desired res.

:-k

---

### Post by kpkeerthi on 2008-04-08
In super-user mode change the resolution in nvidia-setting and save to xorg.conf. Then add
```
nvidia-settings -l
``` to the list of auto started applications.

* 
EDIT: Not sure if this would work. But worth a try since you mention resolution fixes by itself when opening nvidia settings. That command has the letter 'L' and not 1 (one)

---

