---
title: "Moving a Single File"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-02-06
I have just installed the *epsxe* PlayStation emulator using this guide [here]("http://ubuntuforums.org/showthread.php?t=612021") without any problems. I own a PSX and have obtained a BIOS file legally.

I want to move the BIOS file to this folder */usr/local/games/epsxe/bios*

When I try to delete the file called *erase.me* or move to correct BIOS file *SCPH1001.BIN* I get an error message stating that I do not have the correct permission.

[IMG]http://img131.imageshack.us/img131/9499/errorhn3.png[/IMG]

How can I gain the necessary permissions? Thanks.

---

### Post by emarkd on 2008-02-06
You'd need to do that from the command line using sudo:

```
sudo mv mybios /usr/local/games/epsxe/bios
```

---

### Post by kbless7 on 2008-02-06
You can also press alt-f2 and type

```
gksudo nautilus
```

this opens the folders as root so you can then copy the file in there. don't forget to exit the file browser though

---

### Post by emarkd on 2008-02-06
> **kbless7 said:**
> You can also press alt-f2 and type

```
gksudo nautilus
```

this opens the folders as root so you can then copy the file in there. don't forget to exit the file browser though

This is true but be extra careful with a root nautilus.  One mis-click-n-drag or hitting <del> while you've got the wrong directory highlighted could be disastrous.  Be very careful.

---

