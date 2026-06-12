---
title: "Kubuntu X Server Died"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by kenflipkick on 2006-09-08
I think I messed something up with my X, I turned on transparency or something, but when I boot my computer, at the end of the splash when the login screen should come on, instead it goes back to the splash screen and stops.

Is there any way I can fix this without a re-install?

Thanks for any help.

---

### Post by kenflipkick on 2006-09-08
Any ideas?  I can post anything I need to if it helps.

---

### Post by Kobalt on 2006-09-08
Hello,

If you messed up your Xorg, you can run this command to re-establish apropriate settings : 
```
sudo dpkg-reconfigure xsrever-xorg
```

Cheerios !

---

