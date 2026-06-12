---
title: "[SOLVED] Having to restart cupsys every boot"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2008-01-05
Every time I reboot, I have to restart the cupsys service to get my printer and cups showing
 in the printing section (system > administration >printing). Once I restart cupsys, 
everything is fine and I'd like to find the root of the problem instead of just restarting the 
service on boot. 

Thanks for your help!

---

### Post by shanepardue on 2008-01-08
Everything is grayed out before I restart cups thus the reason I 
must restart Cups to get normal functionality. Here's a screenshot 
of what it looks like before I restart Cups.

[IMG]http://img.photobucket.com/albums/v330/shanepardue/screenshot1-1.png[/IMG]

Going to the cups server brings up the following error message

```
There was an error during the CUPS operation: 'httpConnectionEncrypt failed'.
```

---

### Post by shanepardue on 2008-01-10
If you have any tips or suggestions, feel free to share. hehe

---

### Post by bapoumba on 2008-01-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/135054](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/135054) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Looks like there is a bug.

---

### Post by shanepardue on 2008-01-10
> **bapoumba said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/135054](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/135054) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Looks like there is a bug.
It's definitely the same error message, but what's weird is when I restart the cupsys 
service, I get my printer back like nothing had happened.

So I can get Cups working right on restart, but after each boot, I lose it again.

---

### Post by bapoumba on 2008-01-10
May be you could comment your experience in the bug report, or link to this thread ?
I googled for it, and that was the closest I could find ;)

---

### Post by McDuff on 2008-01-11
i'm having the same problem since about a week ago. since then there have been various updates which haven't changed anything.
this is quite annoying on a stable system.

---

### Post by shanepardue on 2008-01-11
> **bapoumba said:**
> May be you could comment your experience in the bug report, or link to this thread ?
I googled for it, and that was the closest I could find ;)
I left a comment on the bug and referenced this thread. Thanks for the tip bapoumba.

---

### Post by Showan2 on 2008-01-12
Same problem here! ussing Gutsy 64 bit

---

### Post by tico on 2008-01-13
Same problem here, using Xubuntu Gutsy.

---

### Post by shanepardue on 2008-01-20
The problem disappeared for me..Hadn't checked in awhile, but I noticed it's working 
properly now. Must've been a recent update.

---

### Post by GGLucas on 2008-01-20
I had the same problem, but I fixed it by adding "/etc/init.d/cupsys start" to my /etc/rc.local, I'll remove it and see if it's been fixed.

---

### Post by shanepardue on 2008-01-24
It appears the problem has been fixed by updates. I haven't had the problem anymore.

---

### Post by KillerKiwi on 2008-03-16
wierd i have no /etc/init.d/cupsys... cupsys is installed...

---

### Post by Henrik on 2008-04-04
> **shanepardue said:**
> It appears the problem has been fixed by updates. I haven't had the problem anymore.

Do you mean it is fixed in Gutsy now? Has anyone reproduced this in Hardy? Could you add a comment about it working on the bug itself. Thanks!

---

