---
title: "Help Installing Wine"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by Demagogue51 on 2005-07-11
Hey, I just installed ubuntu on my computer.  I had heard good things about wine in the past so I decided I would try to install it.  Ive been trying a lot of things and finally I just came back to these forums.  I searched and found the <i>HOWTO: Compiling and Installing WineCVS with WineTools</i> thread and followed those but this is what I get.
```

root@tyler:/home/tyler/cvs/wine # ./tools/wineinstall
WINE Installer v0.75

You are running wineinstall as root, this is not advisable. Please rerun as a user.
Aborting.

```

I'm stuck and Ive tried going to the actual file (not in the root) and double clicking on it and running it but nothing happens.  I'm new to linux and so far I've learned a lot. Help would be greatly appreciated.

---

### Post by Williams477 on 2005-07-11
Try going to a normal terminal instead of the root. You'll install it onto your username and not system wide.

---

### Post by Kvark on 2005-07-11
1. Open the synaptic package manager. (it is under administration in the menu)
2. Search for "wine".
3. Add a checkbox in front of wine.
4. Click apply.

---

### Post by Demagogue51 on 2005-07-11
well, I wasnt able to find it in the synaptic package manager.  I tried it in the terminal, and this is what I got.

```

tyler@tyler:~/cvs/wine$ ./tools/wineinstall
WINE Installer v0.75

The source directory is not writable. You probably extracted the sources as root .
You should remove the source tree and extract it again as a normal user.
tyler@tyler:~/cvs/wine$

```

---

### Post by Kvark on 2005-07-11
[QUOTE=Demagogue51]well, I wasnt able to find it in the synaptic package manager.  I tried it in the terminal, and this is what I got.

```

tyler@tyler:~/cvs/wine$ ./tools/wineinstall
WINE Installer v0.75

The source directory is not writable. You probably extracted the sources as root .
You should remove the source tree and extract it again as a normal user.
tyler@tyler:~/cvs/wine$

```[/QUOTE]

In the menues on top: System -> Administration -> Synaptic Package Manager

Always use the package manager or it's command line version apt-get if possible. To download and install programs in other ways may lead to dependancy issues or other problems.

BTW, you should configure synaptic's sources in order to get access to more programs through it:
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

---

### Post by Demagogue51 on 2005-07-11
Thanks.

---

