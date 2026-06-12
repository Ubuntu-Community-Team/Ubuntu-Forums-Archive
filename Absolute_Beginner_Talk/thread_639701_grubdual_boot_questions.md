---
title: "grub/dual boot questions"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by DestroyMicroshaft on 2007-12-13
Ok heres the deal, I have ubuntu and vista on my laptop via a partion, what I want to do is replace vista with linux mint, but still keep ubuntus grub intact, any ideas how I might do that?

---

### Post by logos34 on 2007-12-13
make sure to install grub to the bootsector (not mbr) of the Mint root partition.  Then manually add Mint to ubuntu menu.lst

---

### Post by Achetar on 2007-12-13
> **logos34 said:**
> make sure to install grub to the bootsector (not mbr) of the Mint root partition.  Then manually add Mint to ubuntu menu.lst Actually, instead of manually updating the menu.lst in ubuntu, run: ```
update-grub
```

That will scan your HD for any and all kernels (it will pick up Mint) and edit your menu.lst accordingly, much easier than editing manually.

---

### Post by DestroyMicroshaft on 2007-12-13
you guys are great, the linux community is outstanding, switching to linux was one of the best decisions Ive made in computers. Next Im off to try ubuntu server.:)

---

### Post by DestroyMicroshaft on 2007-12-13
my bad on the double post but I had another question, what if I had ubuntu installed, and wanted to install xp or vista on a partion, or if I installed xp or vista, or any os really, and it stopped  booting to the grub, what would I do then?

---

### Post by Duck2006 on 2007-12-13
Just reinstall grub

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by annda on 2007-12-13
> **Achetar said:**
> Actually, instead of manually updating the menu.lst in ubuntu, run: ```
update-grub
```

That will scan your HD for any and all kernels (it will pick up Mint) and edit your menu.lst accordingly, much easier than editing manually.

are you sure? i believe it only updates kernels present on the partition it is being run from. at least that's my experience. other distros still need to be updated manually.

---

### Post by DestroyMicroshaft on 2007-12-13
> **Duck2006 said:**
> Just reinstall grub

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

how would i do that if I couldnt get into linux?

---

### Post by Duck2006 on 2007-12-13
> **DestroyMicroshaft said:**
> how would i do that if I couldnt get into linux?

You can do it from the linux live CD.

---

