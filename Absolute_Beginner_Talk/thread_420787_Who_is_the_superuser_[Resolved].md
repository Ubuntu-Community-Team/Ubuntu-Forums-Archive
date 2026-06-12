---
title: "Who is the superuser? [Resolved]"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-04-23
I ran this and got this back> pk@pk-desktop:~$ sudo rdate clock-1.cs.cmu.edu && hwclock --systohc
Mon 23 Apr 2007 08:27:07 PM PDT
Sorry, only the superuser can change the Hardware Clock.
This command sets the hardware clock to the atomic clock at cmu.edu. Is there a superuser I don't know about?

---

### Post by scxtt on 2007-04-23
shouldn't you sudo the hwclock command too?

---

### Post by thelinuxguy on 2007-04-23
Should it be 
```

sudo rdate clock-1.cs.cmu.edu && **sudo** hwclock --systohc

```

---

### Post by Patrick K on 2007-04-23
I didn't think of that. I've never had any occassion to put sudo in the middle of a line. That appears to have work, thanks.

---

### Post by jfinkels on 2007-04-23
> **Patrick K said:**
> I ran this and got this backThis command sets the hardware clock to the atomic clock at cmu.edu. Is there a superuser I don't know about?

There is a "root" user or "superuser" on every Linux system...using the "sudo" command allows you to run the commands after it as the "superuser" (the superuser is the only user who can edit important system files).

You need to put "sudo" before the second command, just as you did before the first command.

---

### Post by scxtt on 2007-04-23
[quote=Patrick K]I didn't think of that. I've never had any occassion to put sudo in the middle of a line. That appears to have work, thanks.[/quote]

it's not "the middle of a line", you're running two separate commands and you apparently need "superuser" privs for both ...

---

### Post by Patrick K on 2007-04-23
Learn something everyday. Thanks all.

---

### Post by Tsen on 2007-04-24
Yeah, the && in the middle of the line denotes a separate command.  In this case, you need sudo rights to do both commands.

---

