---
title: "External hard drive+ubuntu?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by xzin on 2007-12-10
Im going to buy an external hard drive, so I have both internal and external. This is the hard drive I'm going to buy: [http://www.mobileplanet.com/p.aspx?i=147752](http://www.mobileplanet.com/p.aspx?i=147752) (not from that store though). So my question is, can I install ubuntu to that? What about windows? I have heard some people saying that windows can't be installed in external hard drive...
Thanks :)

---

### Post by Jimmey on 2007-12-10
I'm not sure Windows can, because it prefers to be on the first hard drive of the computer (if it's not, it'll throw a hissy fit and refuse to boot).

I believe Ubuntu can, but I'm not sure.

---

### Post by insane_alien on 2007-12-10
i've had ubuntu running on an external drive. its not that difficult at all. windows wouldn't work on it.

just make sure your BIOS can handle booting from USB(most modern ones should be more than capable)

---

### Post by xzin on 2007-12-10
Okay, good. Will it be slower if it's installed on external? Or does it make difference :)

---

### Post by Joeb454 on 2007-12-10
Erm, I'm guessing it'll be a bit slower, beause you'll be limited by the speed of USB, but I don't know if you'd notice it that much

---

### Post by edm1 on 2007-12-10
Buy any ext HD except that one. The clever people at seagate have managed to make it [incompatible with linux]("http://www.theinquirer.net/gb/inquirer/news/2007/12/06/seagate-snubs-linux").

---

### Post by xzin on 2007-12-10
Hmm... about this. When I installed ubuntu to the same hard drive where my windows xp install was, ubuntu automatically found my xp install and configured my settings. Or used the settings from xp to make the install easier, I dont know :) For example I didn't need to install network at all, it worked automatically. But if I have them on different hard drives, will this happen?

---

### Post by edm1 on 2007-12-10
Ubuntu did that all on it's little own, having XP installed won't help with the installation. It detects XP in order to add it to the boot up menu so that you can choose whether to load Ubuntu or XP, and to copy your documents over (if you wanted).

About installing onto an external HD. I dont believe windows can be. Ubuntu can but it's not exactly easy. It would be better to install it to a 2nd internal HD. At the moment they are installed on the same HD but in two completely separate partitions. Is there a reason you want them on separate HDs?

---

### Post by xzin on 2007-12-10
Oh, thats awesome! Thanks a lot :KS

---

### Post by xzin on 2007-12-10
Oh, I just found this article about linux and Seagate external hard drives...:
[http://hardware.slashdot.org/hardware/07/12/09/0651200.shtml](http://hardware.slashdot.org/hardware/07/12/09/0651200.shtml)
Do you think I should buy something else than Seagate?

---

### Post by edm1 on 2007-12-10
> **xzin said:**
> Oh, I just found this article about linux and Seagate external hard drives...:
[http://hardware.slashdot.org/hardware/07/12/09/0651200.shtml](http://hardware.slashdot.org/hardware/07/12/09/0651200.shtml)
Do you think I should buy something else than Seagate?

Thats kinda what i was hinting at in post #6.

EDIT: There is a [workaround]("http://www.cgkreality.com/2007/11/27/seagate-freeagent-idle-under-linux/") but it leaves you with no power saving whatsoever.

---

### Post by xzin on 2007-12-10
Sorry, I didn't notice your post :/

---

### Post by xzin on 2007-12-10
Okay, what about this: [http://www.amazon.co.uk/gp/product/B000GLKK5I/ref=olp_product_details?ie=UTF8&me=&seller=](http://www.amazon.co.uk/gp/product/B000GLKK5I/ref=olp_product_details?ie=UTF8&me=&seller=)
**Maxtor 500GB USB 2.0 Hard Drive **

---

### Post by edm1 on 2007-12-10
I dont see any imediate problems with it except it comes pre-formatted with NTFS (the windows filesystem), ubuntu does have support for this but it's still slightly experimental I would format it to fat32.

---

