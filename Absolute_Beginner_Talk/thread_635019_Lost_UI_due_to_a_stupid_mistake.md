---
title: "Lost UI due to a stupid mistake"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by shashank_hi on 2007-12-08
I installed Ubuntu 6 some time ago. As I started to run out of space on my partition, I fired up the add/remove utility and uninstalled some programs that I thought weren't useful. But unfortunately, I think I deleted some files that were important for the UI, and now basically I'm stuck without a UI. I'm asked for a username and password on a console screen with just text (just like DOS used to look). I searched around and ran 'sudo startx' which got me a mouse, and I was able to load Firefox from the console. 

I suspect I must have uninstalled something that let gnome work properly, and I think I need to reinstall the stuff that I uninstalled. Luckily, I'm able to connect to the internet, so all I need are the commands to reinstall lost stuff.

Any hope???

---

### Post by PmDematagoda on 2007-12-08
Do:-

```
sudo aptitude install ubuntu-desktop
```

To try and fix the GUI.

---

### Post by shashank_hi on 2007-12-08
That worked. Thanks a lot. :)

---

### Post by PmDematagoda on 2007-12-08
No problem, glad it worked:).

---

