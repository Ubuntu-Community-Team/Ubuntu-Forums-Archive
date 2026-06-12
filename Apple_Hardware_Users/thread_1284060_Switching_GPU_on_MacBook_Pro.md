---
title: "Switching GPU on MacBook Pro"
date: 2009-10-06
forum: Apple Hardware Users
---

### Post by andeol on 2009-10-06
The new MacBook Pros have dual GPUs, I haven't managed to find info on using them in Ubuntu though. What is the current state of support for this feature? 

I'm pretty sure Ubuntu doesn't support switching seamlessly between them and that it uses the more powerful GPU per default, but is it possible to switch to using the less power hungry one?

Maybe a section should be added to 
[https://help.ubuntu.com/community/MacBookPro5-5/Jaunty](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty)

There is a brainstorm idea on the topic:
[http://brainstorm.ubuntu.com/idea/19540/](http://brainstorm.ubuntu.com/idea/19540/)

---

### Post by alexmurray on 2009-10-06
This has been asked a number of times in this forum - basically when booting Ubuntu or Windows for that matter, the MacBook does a legacy bios boot which disables the lower powered 9400M gpu and only enables the 9600M GT - so there is no way to switch between the two, as the 9400M is disabled. However, if you can boot using EFI (ie. without having to do a legacy bios boot) then you can use either the 9400M or 9600M GT - see here for some more info [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#EFI](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#EFI)

---

### Post by andeol on 2009-10-07
I see, thanks!

---

