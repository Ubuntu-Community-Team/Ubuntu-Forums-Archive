---
title: "[SOLVED] Cannot use CD/DVD drives in Gutsy"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Goodson1974 on 2007-10-21
Hi all

I've just installed Gutsy on my laptop (Dell Latitude D600) and my desktop.
All had been going well, but when i insert a cd or dvd in the drives on either  machine, i cannot access the drives.

I get an error message about permissions (see attached) but i haven't got a clue what to do to sort this out!!

The drives were accessible in Feisty with no tinkering required.

Has anyone else come across this?

I'm sure that i must have missed something simple or obvious!

Any help will be greatly appreciated :)

---

### Post by dward526 on 2007-10-21
Have you tried the chmod command on the disk drive?

i.e.: sudo chmod 555 /media/cdrom0

It is worth a shot.

---

### Post by Goodson1974 on 2007-10-28
Thanks Dward526

It worked a treat!

---

