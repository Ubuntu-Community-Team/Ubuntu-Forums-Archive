---
title: "Partitions"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by dixxxxer on 2007-01-16
Hey,
Here's the deal.
I've have installed long time ago Fedora and now I got nothing to do with it.
I also got W2k installed and I would like to keep it.
So here's the plan: I want have w2k and Ubuntu on my computer and then my partitions so that I have more than 8gb on Ubuntu, means "home folder", 'cause it's almost full.
After all, I want to merge hda8 and hda5 to hda7, cause thats the partion where I've installed Ubuntu.
Is there any so called noobie, or not so noobie way to do that?

> Levy /dev/hda: 160.0 Gt, 160041885696 tavua
255 päätä, 63 sektoria/ura, 19457 sylinteriä
Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit

    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä
/dev/hda1   *           1        3036    24386638+   7  HPFS/NTFS
/dev/hda2            6197       17032    87040170   83  Linux
/dev/hda3            3037        6196    25382700    f  W95 Laaj (LBA)
/dev/hda4           17033       19457    19478812+  83  Linux
/dev/hda5            4132        6196    16587081   83  Linux
/dev/hda6            4132        4132           0+  83  Linux
/dev/hda7   *        3037        4082     8401932   83  Linux
/dev/hda8            4083        4131      393561   82  Linux / Solaris heittovaihtotiedosto


---

### Post by xyz on 2007-01-16
Several ways to do it; I like:
[Gparted]("http://gparted.sourceforge.net/livecd.php")

---

