---
title: "What Is ???"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by eKlipSe on 2006-08-10
[COLOR="Blue"]**Hi all, what are the equivalents to the windows tools 'Disk Cleanup' and 'Disk Defrag' in Ubu Linux, and if there are these tools how do i access and use them. Yes i'm a rOOk ... ThanX, rik :)**[/COLOR]

---

### Post by kaffelars on 2006-08-10
I don't think there are any Linux alternatives to Disk Cleanup or Disk Defragmentation.

But I'm pretty sure you wouldn't need them on Linux anyway :)

---

### Post by Tomosaur on 2006-08-10
Cleaning up your disk is, 'unfortunately' a manual job. You can probably find a script somewhere which will do it for you, but there's nothing within the OS itself which will do it.

You do not need to defrag Ubuntu.

---

### Post by jrjr on 2006-08-10
.

---

### Post by 23meg on 2006-08-10
[QUOTE=jrjr]Not sure what the command is to invoke it [/QUOTE]It's* fsck*.

---

### Post by jrjr on 2006-08-10
.

---

### Post by 23meg on 2006-08-10
You can also fine tune and disable automatic checks with *tune2fs*.

---

### Post by jrjr on 2006-08-10
.

---

### Post by ckempo on 2006-08-10
> **eKlipSe said:**
> [COLOR="Blue"]**what are the equivalents to the windows tools 'Disk Cleanup' and 'Disk Defrag' in Ubu Linux, **[/COLOR]

There's something in the pipeline to make this a less manual process, take a look at this spec:

[https://wiki.ubuntu.com/SystemCleanUpTool]("https://wiki.ubuntu.com/SystemCleanUpTool")

It will eventually be built into the user backup tool though, which will make its debut in the next version of Ubuntu, Edgy Eft.

---

### Post by 23meg on 2006-08-10
> **jrjr said:**
> Is that a program or a command?
It's a command that has to be run with command line parameters, but like every command, it's a program by definition.

---

