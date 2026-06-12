---
title: "How to install Cycas"
date: 2007-01-06
forum: Art &amp; Design
---

### Post by lakelovers on 2007-01-06
I've download the CAD app Cycas, and used "sudo aptitude install cycas." It starts installing but then ends with this: 

Couldn't find any package matching "cycas".  However, the following
packages contain "cycas" in their description:
  libbcprov-java-doc libbcprov-java
The following packages have been kept back:
  totem
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

I don't understand "OB" of archives. What should I do?

---

### Post by tbroderick on 2007-01-06
Did you download a .deb file? If so just type;
```
 sudo dpkg -i /path/to/program.deb
```

---

### Post by lakelovers on 2007-01-07
Thanks much. Got is installed easily. I don't know why I cannot remember that command line. Guess I better write it down.

---

