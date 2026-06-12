---
title: "please help me install 3d cad"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by cmittle on 2007-10-23
I am liking the looks of the following two cad programs but I can't seem to find them in a .deb file and I've never had to install anything manually.  Could someone please walk me through how to install one or both of these programs?

[Graphite One]("http://www.graphiteone-cad.com/en/freedl.htm?agree=1&imageField.x=16&imageField.y=16") 
[LignumCAD]("http://lignumcad.sourceforge.net/doc/en/HTML/index.html")

Thanks,
Cory

---

### Post by chuckyp on 2007-10-23
You can try installing the rpm packages with alien.   If you have to compile them from source I recomend doing a checkinstall when you get to the make install step.  This will create a deb for you for easy removal.

---

### Post by Daveth on 2007-10-23
bit old Cory but should still work. Looks like it comes as a .rpm, so you need alien to convert to a .deb - alien is in Synaptic

[http://ubuntuforums.org/showthread.php?p=3588422](http://ubuntuforums.org/showthread.php?p=3588422)

---

### Post by cmittle on 2007-10-23
I found that but it seems that the three people that tried it didn't have much luck.  Maybe tomorow I'll give it a shot anyhow.  Any tips on the Lignum program?

Thanks,
Cory

---

### Post by Daveth on 2007-10-23
Probably worth staying with graphiteone as the other package was last released back in 2003, so I guess development has stopped. Compare that with May 2007 for the other. Should be pretty straightforward to alien the rpm, and then install the resulting .deb file. Remember to right click it and alter its properties to allow it to run as a program, then open with  GDebi from the same context menu. Give it a go.

---

