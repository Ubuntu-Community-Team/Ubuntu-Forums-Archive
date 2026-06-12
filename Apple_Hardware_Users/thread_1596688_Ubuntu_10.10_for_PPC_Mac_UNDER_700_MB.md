---
title: "Ubuntu 10.10 for PPC Mac **UNDER 700 MB**??"
date: 2010-10-14
forum: Apple Hardware Users
---

### Post by 828688 Ben on 2010-10-14
Does anybody when the non-beta version of Ubuntu 10.10 (under 700 MB) for PPC will be released? The only one I can find is located here: [http://cdimage.ubuntu.com/ports/daily-live/current/](http://cdimage.ubuntu.com/ports/daily-live/current/) and it's not the final version and it's over 700 MB.


Thanks For The Help,
Ben

---

### Post by kerry_s on 2010-10-14
[http://cdimage.ubuntu.com/ports/releases/10.10/release/](http://cdimage.ubuntu.com/ports/releases/10.10/release/)

---

### Post by zeroti on 2010-10-14
if it's over 702 MB, you'll have to "overburn" it.

I did it using the "wodim" command, and added "overburn" and "sao" options to make it overburn. check out the manpage, if you want to do it with that.

You can also try "k3b", a graphical utility, but for some reason it didn't work on my computer.

---

### Post by 828688 Ben on 2010-10-14
> kerry_s:
[http://cdimage.ubuntu.com/ports/releases/10.10/release/](http://cdimage.ubuntu.com/ports/releases/10.10/release/)Thanks, but if you look at the bottom of the page, the iso for ppc mac is 710MB and it was created on October 8th 2010, which is two days before the final version of ubuntu 10.10 was released.

> if it's over 702 MB, you'll have to "overburn" it.

I did it using the "wodim" command, and added "overburn" and "sao"  options to make it overburn. check out the manpage, if you want to do it  with that.

You can also try "k3b", a graphical utility, but for some reason it didn't work on my computer.     I already do know how to overburn a cd. My main problem is finding the final version of ubuntu 10.10 for ppc mac.


Thanks,
Ben

---

### Post by zeroti on 2010-10-14
> **828688 Ben said:**
> Thanks, but if you look at the bottom of the page, the iso for ppc mac is 710MB and it was created on October 8th 2010, which is two days before the final version of ubuntu 10.10 was released.

Interesting... well, I used that iso and it was fine for me. It shouldn't be any different than installing and then upgrading with apt-get. Not every package is working for me right now, such as evince, and maybe a couple others, but the fixes for those are in the pipelines.

---

