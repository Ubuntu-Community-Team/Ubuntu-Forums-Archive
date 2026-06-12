---
title: "screwed up system permissions in Users and Groups"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by alvin727 on 2007-10-01
I am newbie and probably ruined my new installation.

I went into the Users and Groups area and started changing my own permissions.  Now SUDO nolonger works for me.  I can nolonger get administrative permissions.  I can't get back into the Users and Groups to correct the problem.  Here is the message I am getting . . .

[B][I]Failed to run users-admin
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/I][/B]

Can anything be done short of a total reinstall?

    All help is appreciated,
         Alvin

---

### Post by Dr Small on 2007-10-01
Try booting up in recovery mode and then run:
```
addgroup *username* admin
```

---

### Post by alvin727 on 2007-10-01
At what point do I add the instruction?

   Alvin

---

### Post by Dr Small on 2007-10-01
1.) Select the recovery option fromt eh GNU Grub Menu, and boot in that.
2.) When the computer completes it's booting, type in the following command.

Dr Small

---

### Post by alvin727 on 2007-10-01
Dr Small,

            WOW!   That is a neat trick!   

              THANK YOU!

---

