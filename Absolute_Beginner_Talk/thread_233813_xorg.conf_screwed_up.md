---
title: "xorg.conf screwed up"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by khulbert on 2006-08-10
I tried to add a screen resolution by altering my etc/X11/xorg.conf  file, and now x wont start.  I can boot in recovery mode but when I  use startx I get a bunch of errors.  I was wondering if there is a way to reset my xorg.conf file.  Any suggestions?

---

### Post by khulbert on 2006-08-10
Fixed.

---

### Post by thistlebrae on 2006-08-10
How did you fix your file?  I am having a problem in that Ubuntu shows 640X480 as the only resolution available despite the fact that my graphics card (Nvidia) and Monitor will display much greater than that.  I was going to see if I could change that by altering the "Default Depth" setting in the xorg.conf file.

Based on your post I think that might not be wise so I feel lucky that I saw this just before I was going to make the change.

Got any idea on how to increase the resolution options that display?

Regards,
Todd

---

### Post by powder on 2006-08-10
He probably fixed it with dpkg-reconfigure xserver-xorg.  If the resolution/refresh rate that you want is not displayed, but you know your monitor can handle it, you can create a custom modeline to place in your xorg.conf which will effectively force that resolution/refresh rate.

---

### Post by thistlebrae on 2006-08-10
Thanks...how does one do that?

---

### Post by powder on 2006-08-10
Edit:

Here is a better guide... :)

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Anduu on 2006-08-10
Learn how to backup your xorg.conf...it's easy.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.confgoodest
```

If it should get messed up...

```
sudo cp /etc/X11/xorg.confgoodest /etc/X11/xorg.conf

```

---

### Post by djsroknrol on 2006-08-10
> **khulbert said:**
> Fixed.

Instead of that, it would be helpful to all if you explained [B]how
[/B] you fixed it...

---

### Post by Anduu on 2006-08-10
> **djsroknrol said:**
> Instead of that, it would be helpful to all if you explained [B]how
[/B] you fixed it...

Yes that would be nice ;)

---

