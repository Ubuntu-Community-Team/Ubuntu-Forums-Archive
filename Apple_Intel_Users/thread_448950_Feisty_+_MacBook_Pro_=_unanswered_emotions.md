---
title: "Feisty + MacBook Pro = unanswered emotions"
date: 2007-05-19
forum: Apple Intel Users
---

### Post by Halsnalle on 2007-05-19
Okay, I really, really want to be friends with Ubuntu, but it keeps rejecting me. Perhaps I'm trying too hard. Here's my problem:

I've got a MacBook Pro C2D. [After failing to upgrade from Edgy to Feisty in my Parallells install]("http://ubuntuforums.org/showpost.php?p=2580828&postcount=41"), I decided to try use a Boot Camp partition (on which I previously had failed to install Windows XP, but that's another story) to install Feisty for real instead.

So I installed Refit, got the Feisty Live CD, eventually managed to get past the [X problem by installing the ATI drivers]("http://ubuntuforums.org/showthread.php?t=414194"), and then started the install process.

Now I just can't get past the partitioning step: "No root file system defined", it says, and [editing the /usr/lib/ubiquity/ubiquity/validation.py did not let me bypass that step.]("http://ubuntuforums.org/archive/index.php/t-282898.html")

Does anyone know what I could do to get Ubuntu like me?

---

### Post by ronocdh on 2007-05-20
No root partition defined just means you haven't set your "Ubuntu partition" (whatever space you've decided to let Ubuntu use) as /. Do this by selecting "/" from the drop-down menu in the installer. You can ignore defining swap space; create a swap file later at your leisure. Hope this helped.

---

### Post by Halsnalle on 2007-05-22
Ah, thanks, that did it. It wasn't obvious how to do the manual partition, but now I got it working.

---

### Post by ronocdh on 2007-05-22
> **Halsnalle said:**
> Ah, thanks, that did it. It wasn't obvious how to do the manual partition, but now I got it working.
Congratulations! If you have any other issues, we're here to help.

---

