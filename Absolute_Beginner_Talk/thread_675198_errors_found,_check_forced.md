---
title: "errors found, check forced"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by thepopasmurf on 2008-01-22
I have a dual-boot computer (Ubuntu/XP) and I have had the usual forced check when booting (every so often).

However, now the check is being forced every time I start Ubuntu.

I'm not sure exactly what's causing this but I recently installed a program on Windows which allows me to access the Ubunntu partition.

Does anyone have any ideas? How can I stop this?

---

### Post by candtalan on 2008-01-22
It sounds like a good guess that something is causing some corruption of the ubuntu file system (ext3?). If so, then fixing the result - the 'checks forced' may keep the boat afloat and the specific errors may put some light on the detailed problem. However, it might be worth considering at this stage to un install the windows program you mentioned, and take things from there, hoping the problem can be contained.

good luck

---

### Post by philinux on 2008-01-22
If you use this you can see how many boots are needed on your system before a check takes place. sudo tune2fs -l /dev/sdax

It does sound like the ext3 file system has errors which need fixing. Does find and fix any errors?

---

### Post by thepopasmurf on 2008-01-22
How do I check the results of the check?

---

### Post by Herman on 2008-01-22
```
cat /var/log/fsck/checkfs
```
Regards, Herman :)

---

### Post by rafaelcapanema on 2008-02-11
I've been having the same issue!

Text above from [http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

> **If I use hibernate (suspend to disk) on Windows or Linux, I experience that on the next boot of Linux, the e2fsck utility runs and reports file system errors. Is there a bug fix or a workaround for it?**

When you hibernate (suspend to disk) an operating system, the whole memory of running programs is stored on disk including opened file handles. It is restored on resuming the computer from hibernation. Thus the *Windows boot manager* usually does not offer the boot menu if you have hibernated Windows before, because you are not allowed to boot another OS.

One way of looking at this is that file systems remain mounted and files remain opened when the computer is switched off following a hibernate command.

It is not possible to implement a file system driver which can deal with a file system that is being changed by other operating systems at the same time that it is mounted by the file system driver itself.

It means that you should shutdown Windows before booting Linux and vice-versa. You can use hibernate (suspend to disk) in Windows only if you resume Windows subsequently. Furthermore, you can use hibernate (suspend to disk) in Linux only if you attempt to resume Linux subsequently. But you cannot mix the two operating systems. 

---

