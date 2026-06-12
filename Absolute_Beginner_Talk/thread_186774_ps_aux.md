---
title: "ps aux"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-06-02
IF i run ps aux what are all these processes running on tty1 to tty6?


root      4033  0.0  0.0   1560   488 tty1     Ss+  14:18   0:00 /sbin/getty 384
root      4034  0.0  0.0   1560   492 tty2     Ss+  14:18   0:00 /sbin/getty 384
root      4035  0.0  0.0   1560   492 tty3     Ss+  14:18   0:00 /sbin/getty 384
root      4036  0.0  0.0   1560   492 tty4     Ss+  14:18   0:00 /sbin/getty 384
root      4037  0.0  0.0   1564   496 tty5     Ss+  14:18   0:00 /sbin/getty 384
root      4038  0.0  0.0   1564   496 tty6     Ss+  14:18   0:00 /sbin/getty 384


lex1

---

### Post by Arndt on 2006-06-02
[QUOTE=lex1]IF i run ps aux what are all these processes running on tty1 to tty6?


root      4033  0.0  0.0   1560   488 tty1     Ss+  14:18   0:00 /sbin/getty 384
root      4034  0.0  0.0   1560   492 tty2     Ss+  14:18   0:00 /sbin/getty 384
root      4035  0.0  0.0   1560   492 tty3     Ss+  14:18   0:00 /sbin/getty 384
root      4036  0.0  0.0   1560   492 tty4     Ss+  14:18   0:00 /sbin/getty 384
root      4037  0.0  0.0   1564   496 tty5     Ss+  14:18   0:00 /sbin/getty 384
root      4038  0.0  0.0   1564   496 tty6     Ss+  14:18   0:00 /sbin/getty 384

lex1[/QUOTE]

They are waiting for someone to connect to the serial port they are watching and then offer a login prompt. "384" is probably really "38400 [baud]".

---

### Post by astoltz on 2006-06-02
Those are just the normal virtual terminals set-up by init. (getty is the command that actually opens a terminal and asks for a login).  You can access the terminals by ctrl-alt-F1, F2...  By default, the X-server (gnome) runs on F7.

---

### Post by Arndt on 2006-06-02
[QUOTE=astoltz]Those are just the normal virtual terminals set-up by init. (getty is the command that actually opens a terminal and asks for a login).  You can access the terminals by ctrl-alt-F1, F2...  By default, the X-server (gnome) runs on F7.[/QUOTE]

I thought I knew enough to answer the question - sorry about that.

---

### Post by robins_web on 2006-06-02
[QUOTE=Arndt]I thought I knew enough to answer the question - sorry about that.[/QUOTE]
Never mind--at least you gave it your best shot, right? That's what helping each other is all about.

---

