---
title: "Powerbook G4 install question"
date: 2010-03-05
forum: Apple Hardware Users
---

### Post by brw314 on 2010-03-05
Hi all,

I would like to install Ubuntu on an old G4 PPC if possible. I downloaded and burned ubuntu 5.1 live iso cd and also ubuntu 8.04 desktop iso  to CD's. When I retart holding the "c" key down steadily , nothing happens it just brings up the Mac OSX. Also, there isn't a sign of the CD in the start-up disk utility

Thanks
Brian

---

### Post by linuxopjemac on 2010-03-06
If booting with the 'c' key does not work, I can advize you to boot from within open firmware. Start the PowerBook and press command+apple+o+f. Then at the prompt you tell your Mac to boot from the CD (be sure to have the CD in the drive by now). Then issue the following command:

```
boot cd:,\\:tbxi
```

if you want to eject the CD in open firmware, just issue an
```
eject cd
```

or shutdown:
```
shut-down
```

---

