---
title: "help! need to repair yaboot.conf"
date: 2007-08-03
forum: Apple PPC Users
---

### Post by jaskah on 2007-08-03
hello
i changed my yaboot.conf filt to boot from another kernel but now i can't boot at all.
my computer can't start from a cd, but i can get into a shell booting from linux net install components on my os x partition.
once i get into a shell how can i get to etc/yaboot.conf on my root partition and change yaboot.conf back to its original configuration?
thanks for any help!

---

### Post by pxwpxw on 2007-08-03
If you can boot the netinstall menu, there should be a <TAB> boot: rescue option, that will let you fixup yaboot.conf. But you then have to run ybin to use it.

---

### Post by jaskah on 2007-08-03
hi 
thanks for your reply.
i managed to get up and running again...learned a lot on the way.

---

