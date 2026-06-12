---
title: "how do I burn a cd from the terminal"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2007-01-06
Long story short, my computer cannot handle booting up X anymore (due to hardware problems), and so I need to back up my files from recovery mode, without booting up X.  Does anyone know of a CD burning program I could get that would allow me to burn data from the terminal (i.e. without booting up X)?

---

### Post by kinematic on 2007-01-06
for burning files to disk you can use cdrecord...use cdrecord --help for options(k3b,gnomebaker,graveman and others are just a graphical frontends to command line burning apps).
a valid command line would be something like this
> cdrecord dev=/dev/hdc speed=24 driveropts=burnfree -dao -data /path/to/files

---

### Post by Artemis3 on 2007-01-07
To master and burn an ISO9660 volume with Joliet and Rock-Ridge extensions on a DVD:
```
growisofs -Z /dev/dvd -R -J /some/files
```

To use growisofs to write a pre-mastered ISO-image to a DVD:
```
growisofs -dvd-compat -Z /dev/dvd=image.iso
```

---

