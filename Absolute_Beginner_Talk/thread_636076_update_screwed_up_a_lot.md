---
title: "update screwed up a lot"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by TheTeZ on 2007-12-09
ARG!!!! so i typed in sudo apt-get ubuntu-desktop and it started installing ubuntu i ran out of space on the partition, so i made the partition bigger, what do i type to start up the installation from where it stopped, also when i now start up firefox or any web browser it says welcome to 7.04 i should have ... or did have 7.10 installed (kubuntu) that and my wireless isnt working again, but after i can get my adapt manager to work again i will get that working. Any help?

---

### Post by CRCarl on 2007-12-09
What were you upgrading from? 7.04 server? Desktop? Something else?

---

### Post by TheTeZ on 2007-12-09
well i was actually installing ubuntu from my already installed 7.10 kubuntu desktop.   and it seems like kubuntu may have been downgraded, or some files were replaced with older ubuntu files like ndiswrapper for one. ... is their a way to even remove the partially installed ubuntu desktop?  when i go to adpet manager it wont let me it says that some other adept program is being used and can not continue because of it.

---

### Post by CRCarl on 2007-12-09
sounds like adept is running in KDE somewhere. Can you get into KDE and quit Adept? If not try "killall adept"

After you have stopped adept you can roll the install forward ```
sudo apt-get ubuntu-desktop
``` or you can rollback ```
sudo apt-get remove ubuntu-desktop
```

C

---

### Post by TheTeZ on 2007-12-10
thanks, i tried that, but with no luck.... oh well, it was a recent installation of kubuntu anyway, im gonna just reformat and fresh reinstall.

---

