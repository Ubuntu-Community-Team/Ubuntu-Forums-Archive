---
title: "Locate &quot;Device&quot; -- How do I do this in xorg.conf?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Hymie on 2007-05-14
I am trying to fix a problem with my Nividia graphics card.

I have logged in as root and am in the xorg.conf

I was told to: Locate "Device"
How do I do this, I don't see it anywhere. I tried typing it in, that doesn't work.

Thanks

---

### Post by bobplano on 2007-05-14
that probably just means find the device section. you could also just post your xorg.conf and you  could still get helped

---

### Post by taurus on 2007-05-14
```
nano -Bw /etc/X11/xorg.conf
```
Scroll down with the arrows until you get to the 

```
**Driver**      "vesa"
```
Make your changes and save it with <Ctrl>o and exit with <Ctrl>x.

---

### Post by Hymie on 2007-05-14
okay, how do i locate the device section?

---

### Post by taurus on 2007-05-14
Just scroll down with the arrow keys until you get to the Device section.

---

### Post by Hymie on 2007-05-14
I can't really scroll down. At the lower portion of my screen, there is some type of menu that says:

^ G Get Help ^O WriteOut ^Read File ^Y Prev Page.....


none of these inculde a device section.

thanks

---

### Post by taurus on 2007-05-14
> **Hymie said:**
> I can't really scroll down. At the lower portion of my screen, there is some type of menu that says:

^ G Get Help ^O WriteOut ^Read File ^Y Prev Page.....


Those are your commands.  Can you press the down arrow key on your keyboard to move to next page?  Or better yet, press <Ctrl>y.

---

