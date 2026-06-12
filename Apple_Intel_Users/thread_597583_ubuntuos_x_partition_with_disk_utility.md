---
title: "ubuntu/os x partition with disk utility?"
date: 2007-10-30
forum: Apple Intel Users
---

### Post by nebhead on 2007-10-30
Hello there.
i would like a pretty straight forward way of dual booting ubuntu and all the guides i have seen using bootcamp look slightly hard.
So i was wondering.. is it possible to partition the HD within disk utilty, then boot into ubuntu cd and install onto that partition? is it possible and fairly straight forward? also if i need to manually edit the partition table in the ubuntu installer please give me a little help, never done that, always have done a single boot on an entire HD without any partition changing, it just confuses me a bit.
Thanks very much, looking forward to hearing from someone.

---

### Post by cyberdork33 on 2007-10-30
> **nebhead said:**
> Hello there.
i would like a pretty straight forward way of dual booting ubuntu and all the guides i have seen using bootcamp look slightly hard.
So i was wondering.. is it possible to partition the HD within disk utilty, then boot into ubuntu cd and install onto that partition? is it possible and fairly straight forward? also if i need to manually edit the partition table in the ubuntu installer please give me a little help, never done that, always have done a single boot on an entire HD without any partition changing, it just confuses me a bit.
Thanks very much, looking forward to hearing from someone.

If you can use bootcamp, it is probably the easiest method. If you have Leopard, then you can use disk utility and the '+' button to add a partition. This essentially does the same thing as the bootcamp assistant, except that you can format it to a different filesystem (not that it matters, because none of them are linux filesystems). In tiger, this function is not included in Disk Utility., and your best bet is to use gparted or parted magic.

Whichever way you choose to make a partition, when you boot the Ubuntu install disc, you will want to delete the new partition, then choose to install in the free space! that's it!

---

### Post by nebhead on 2007-10-30
Thankyou so much, yes i have leopard, i will try it tomorrow, and possibly post results depending on if i have enough time, for people who want to know exactly how to do it, thanks!

---

### Post by nebhead on 2007-10-31
Just incase someone stumbles across this thread while searching for answers on creating a partition with disk utility i am going to say this:
Its easy, it works.

all u do is create a partition in disk utillity, reboot into the ubuntu cd
delete the partition you just created and install with free space.
the only problem i came across was wireless which i solved by reading the ubuntu for macbook documentation. so just do it!

I did this with a macbook 2nd gen core 2 duo, with leopard and ubuntu gutsy.

---

