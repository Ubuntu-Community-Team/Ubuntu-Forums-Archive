---
title: "moving home folder"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-14
Is there a way I can completely move the home folder into another partition? does it matters if it is fat32?

---

### Post by taurus on 2007-05-14
You cannot use fat32 filesystem for your /home.  Doing so will guarantee you won't be able to log in to your $HOME.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by jaded_pl on 2007-05-26
Yea, but can be /home folder moved to existing linux partition?
I mean not specially created for it, with other existing files...

---

### Post by kevinlyfellow on 2007-05-26
> **taurus said:**
> You cannot use fat32 filesystem for your /home.  Doing so will guarantee you won't be able to log in to your $HOME.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Are you certain on that?  I could have sworn I have done that before...

Edit:  I may have done it before, but that doesn't make it a wise decision.  I looked around and Fat32 doesn't support linux file permissions, so there could (will) be issues that pop up. up.  If you like to experiment you can always play around and see if you can get it to work, but don't complain if you loose everything ;-)

---

