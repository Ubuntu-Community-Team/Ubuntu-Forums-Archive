---
title: "NTFS partition: one of my directories disappeared"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by tico on 2007-07-06
Well, here's the situation:

I'm having some problems with polytonic greek and palatino Linotype font in Openoffice, so I unistalled Openoffice and reinstalled it. After that I cannot see 2 of my directoriesin two different NTFS partitions:

1. my work directory: /media/sda2/André (d:/André in Windows)
2. my user configuration directory in Windows: /media/sda1/Documents and Settings/André (C:/Documents and Settings/André in Windows).

I can see the other directories in these two NTFS partitions. In Windows XP I can see and access these two directories (yes, thanks God they are still there).

How can I make these 2 directories appear again in Ubuntu?

Thanks fr helping.

---

### Post by Biochem on 2007-07-07
Hi Tico,
When installed, ntst-3g has big problem understanding accentuated characters. and therefore it doesn't display them to avoid braking them. To see your file there are 2 option available.[LIST=1]
[*]In Windows, change the name of all the file containing special character. in your exemple André to Andre.
[*]Follow the instruction in szaka' link.[/LIST]Good luck

---

### Post by szaka on 2007-07-08
Ntfs-3g requires that the distribution setup the national environtment before mounting NTFS volumes. During boot this doesn't happen yet on Ubuntu, so it needs a workaround described here: [http://ntfs-3g.org/support.html#locale3](http://ntfs-3g.org/support.html#locale3)

The iocharset option is ignored by ntfs-3g, the locale is the correct one. Sometimes the below can also help without need to configure /etc/fstab:
```

umount -a
mount -a

```

---

### Post by simosx on 2007-08-08
tico, it's better to use free and open-source fonts for Greek Polytonic.
By default, Ubuntu comes with Greek Polytonic support.
If you want quality fonts, you can also try Gentium.

If you are working professionally on Greek Polytonic, see the GFS fonts, at
[http://www.greekfontsociety.org/pages/en_typefaces1.html](http://www.greekfontsociety.org/pages/en_typefaces1.html)
(again, free and open-source).

All are packaged for Ubuntu.

---

