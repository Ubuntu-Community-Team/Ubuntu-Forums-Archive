---
title: "[SOLVED] Won't autologin after upgrade from 7.04 -&amp;gt; 7.10"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by amigaone_xe on 2007-11-22
After upgradeing to 7.10 it won't autologin anymore.

I enable "System>Administration>Login Window, Security Tab, Enable Automatic Login" and specify my user and close the window. 
Then i open the same window again to see that " Enable Automatic Login" is not enabled anymore.

It seems I can't enable automatic login anymore. Is it possible to edit som configfiles manually to enable it? It worked fine when I was running 7.04.

Thanks in advance!

---

### Post by aysiu on 2007-11-22
Try /etc/gdm/gdm.conf-custom

Make sure it has this in it: ```
AutomaticLoginEnable=true

AutomaticLogin=amigaone_xe
```

---

### Post by amigaone_xe on 2007-11-22
/etc/gdm/gdm.conf-custom was an empty file and adding those lines didn't do the trick.

But i found out that editing /etc/gdm/gdm.conf with the suggest lines did the trick!

Thanks!!! :)

---

