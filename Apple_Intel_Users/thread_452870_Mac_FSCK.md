---
title: "Mac FSCK"
date: 2007-05-23
forum: Apple Intel Users
---

### Post by MatthewACT on 2007-05-23
Hi.  My hard drive is failing, and I need to get data off right away.  I was told that mac fsck could work.  How do I use that?  If you think mac fsck isnt a good option, do you have any suggestion?

---

### Post by ronocdh on 2007-05-23
> **MatthewACT said:**
> Hi.  My hard drive is failing, and I need to get data off right away.  I was told that mac fsck could work.  How do I use that?  If you think mac fsck isnt a good option, do you have any suggestion?
Well, you haven't given us very much information about your hardware or situation (tsk, tsk! [-X), but I understand the rush. Have you tried booting from the OS X install disc and running Disk Utility? The repair options it works can be quite helpful. You may be able to clone the drive from in there, too.

---

### Post by Gen2ly on 2007-05-24
I believe fsck has an option the turns off too turn off bad sectors, disk utility too.  I don't have that information on me, I'll see if i can find something MattewACt.

---

### Post by Gen2ly on 2007-05-24
Ok, fsck.ext3 can search for bad blocks and make them inaccessible.  Use the LiveCD and run this command:

```
fsck.ext3 -c /dev/(ubuntu partition)  
```

This will take awhile as it has to discover every block.  If it's showing bad block errors.  Now at least I'd feel at least a little more safe backing up data.

---

