---
title: "Help WIth exe files"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Tootles on 2007-09-09
how do i open exe files?

---

### Post by Linux_Man on 2007-09-09
Simple. You can't. .exe s are Windows binary files. However WINE can help you use some of them, however its not perfect and many applications don't work. If you don't like WINE you can run Windows in a virtual machine such as Qemu or VMware.

---

### Post by Acglaphotis on 2007-09-09
Try opening a terminal,downloading wine, and then do a:

```

wine /path/to/exe/goes/here

```

Download wine with the following command:

```

sudo aptitude install wine

```

---

### Post by Tootles on 2007-09-09
how do u get wine?

---

### Post by Linux_Man on 2007-09-09
Download it from the package manager just like you would any other software.

---

### Post by Tootles on 2007-09-09
k installed wine

---

### Post by philinux on 2007-09-09
You get it from the synaptic package manager

---

### Post by Tootles on 2007-09-09
error i get sergey@sergey-desktop:~$ wine vpsupd.exe
bash: wine: command not found
sergey@sergey-desktop:~$

---

### Post by Maestro23 on 2007-09-09
> **Tootles said:**
> how do u get wine?

Their Website: [http://www.winehq.org/](http://www.winehq.org/)

From the Repositories:

> sudo aptiude update

sudo aptitude install wine


*Read the help docs at the site so you will know what you're doing.

---

### Post by Bothered on 2007-09-09
> **Tootles said:**
> how do u get wine?

Follow the instructions in the post above yours.

Be warned that wine does not always run exe files without problems. Which particular exe files are you trying to run? If it's an software installer, then you can install ubuntu specific software.

---

### Post by Linux_Man on 2007-09-09
Did you really install wine? Because try 


```
wine --version
```


If nothing shows up then you don't have Wine installed.

---

### Post by philinux on 2007-09-09
If it installed ok it will be in your menus. Look for Wine File

---

