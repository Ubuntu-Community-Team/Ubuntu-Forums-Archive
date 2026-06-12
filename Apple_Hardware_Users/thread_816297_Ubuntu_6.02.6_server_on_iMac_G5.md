---
title: "Ubuntu 6.02.6 server on iMac G5"
date: 2008-06-02
forum: Apple Hardware Users
---

### Post by o0' on 2008-06-02
Hi everybody, I'm new from community and from ubuntu. I've an iMac G5 tath I'll would use like a server. But i've not a cd\dvd-rom. I've divided my disk in 2 partitions. the first with leopard and the second with the ubuntu's boot disk. When I press C in the startup of imac, I can select Leopard or Ubuntu. But when I select ubuntu the imac reload the same page with the selections... Sorry for my bad english, I'm italian... :lolflag:

---

### Post by stream303 on 2008-06-02
Welcome aboard oO!

When you split up the disk with Leopard, you don't really need to make a partition for Ubuntu - it can handle it by itself.

Maybe the easiest thing to do is to delete your special partition you tried to make for Ubuntu, and then go through install again, and then let Ubuntu install to "free space".  It will then do all the necessary partitioning for you during install and will configure yaboot.conf as well.

I'm wondering if when you created those two partitions with Leopard, that you don't really have any space left to install Ubuntu onto?

---

