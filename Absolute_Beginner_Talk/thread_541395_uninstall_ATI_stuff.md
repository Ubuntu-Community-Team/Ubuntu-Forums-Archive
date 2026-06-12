---
title: "uninstall ATI stuff"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-09-02
Hey community,

I have a dual monitor setuo and I am running the second monitor on an ATI graphics card, I followed Mike's HOWTO...[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

And now ubuntu wont boot to Gnome Desktop.
I tried 
```

sudo apt-get remove xorg-driver-fglrx
```

but I still get the messed up xorg thing when trying to boot up, how do I uninstall everything that I just did from Mike's tutorial?

---

### Post by overdrank on 2007-09-02
> **pgar23 said:**
> Hey community,

I have a dual monitor setuo and I am running the second monitor on an ATI graphics card, I followed Mike's HOWTO...[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

And now ubuntu wont boot to Gnome Desktop.
I tried 
```

sudo apt-get remove xorg-driver-fglrx
```

but I still get the messed up xorg thing when trying to boot up, how do I uninstall everything that I just did from Mike's tutorial?


HI you may need to reconfigure you xorg after removing the fglrx
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by pgar23 on 2007-09-02
hey,
thanks. Even tho I had no idea what I was doing, I got it to work. Appreciate the help.

---

### Post by overdrank on 2007-09-02
> **pgar23 said:**
> hey,
thanks. Even tho I had no idea what I was doing, I got it to work. Appreciate the help.

Hey glad to hear and I could have elaborated a little more. But I fly blind most of the time :lolflag:

---

