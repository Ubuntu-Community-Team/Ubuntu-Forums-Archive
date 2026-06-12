---
title: "wine question"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-02-09
I have a Windows animation program in wine that needs a browser to run with.
Is there a way  to somehow integrate the windows program with the firefox browser in feisty or
will I have to install a windows broswer into wine in order to run my windows animation program?

---

### Post by bwhite82 on 2008-02-09
I would install the windows version of FF or mozilla into Wine and all should be well.

---

### Post by GSF1200S on 2008-02-09
> **garyed said:**
> I have a Windows animation program in wine that needs a browser to run with.
Is there a way  to somehow integrate the windows program with the firefox browser in feisty or
will I have to install a windows broswer into wine in order to run my windows animation program?

Im not sure if this will help, but please research the wine gecko engine- its used to render html pages in Wine games, and I believe apps. Try:

```
wine iexplore http://winehq.org
```

I dont know if that will help, but maybe.. According to Wines APPdb, Firefox is Platinum, which means it runs great in Wine:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5819&iTestingId=9211](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5819&iTestingId=9211)

You could also try IE4Linux, which may help you:

[http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)

Good Luck :)

---

### Post by garyed on 2008-02-09
Thanks,
I installed Firefox into wine & all is well.
I also had to install the flash plugin & the animation program now runs fine.

A friend of mine is a software developer (Windows only) & he was telling me that I should be able to tell the windows animation program in wine to use firefox in linux for its browser to integrate with.  I couldn't figure out how to do it. He couldn't do it either but he's never used linux or wine before.

---

