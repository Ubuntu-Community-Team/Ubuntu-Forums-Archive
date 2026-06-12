---
title: "Unable to remove cdemu"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by crackling on 2007-02-13
I just installed cdemu, but it turns out I don't really need it now when I try to get rid of it it gives me this: ```
chris@chris-desktop:~/Desktop/cdemu-0.7$ sudo aptitude remove cdemu
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "cdemu"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```

I tried removing via Synaptic but I can't seem to find cdemu listed anywhere.

---

### Post by jpeddicord on 2007-02-13
Did you compile from source, if so, go to the same directory you installed from and type "sudo make uninstall" to remove it all.

You might be able to find the package in Synaptic's Local or Obsolete section if you installed via package.

Jacob

---

### Post by crackling on 2007-02-13
I compiled by source but sudo make uninstall doesn't seem to be working: ```
chris@chris-desktop:~/Desktop/cdemu-0.7$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.

```

---

