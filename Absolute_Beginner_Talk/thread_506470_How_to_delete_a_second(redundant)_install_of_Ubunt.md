---
title: "How to delete a second(redundant) install of Ubuntu?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by bokorpop on 2007-07-21
I have been dual booting for a few month or so now. On the GRUB screen, for totally unexplained reasons, instead of giving me the option of "Ubuntu" "Ubuntu safe mode" and Windows, it now gives me two options of Ubuntu and Ubuntu safe mode, plus windows. In otherwords, it is more like I am triple booting instead of dual booting. I have no idea how this second install of Uubuntu got on my computer and I want it off- it is just wasting space. How do I delete this second useless, install of Ubuntu.

---

### Post by scxtt on 2007-07-21
if you updated your kernel, that's just an entry to boot the "new" and "old" kernel - not another ubuntu on the whole ... you can just edit /boot/grub/menu.conf and remove the entry you don't want ...

---

### Post by steve.horsley on 2007-07-21
If you are happy that the updated kernel iw trustworthy for you, you can use Synaptic, and search for and remove the outdated **linux-image** package.

---

### Post by alienexplorers on 2007-07-21
You can also comment out the un-needed kernels by proceeding there lines with the pound (#) symbol.  This way if you do have a problem with the new kernel you can always uncomment the old one and use it.

---

### Post by bokorpop on 2007-07-22
Am I correct in saying that 2.6.20-15 is the old one I want to delete and 2.6.20-16 is the newer one?

---

### Post by Outrunner on 2007-07-22
> **bokorpop said:**
> Am I correct in saying that 2.6.20-15 is the old one I want to delete and 2.6.20-16 is the newer one?

Yes.

---

