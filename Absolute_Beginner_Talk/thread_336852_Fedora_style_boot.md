---
title: "Fedora style boot?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-01-12
I really like the Fedora style boot-up, the Blue background with the black console thing. Can we re-create this for Ubuntu?

---

### Post by Bachstelze on 2007-01-12
When you're in GRUB, instea of just pressing Enter, pess "e" to change the boot options, go to the line that ends with "ro quiet splash", remove the "splash", Enter to confirm, "b" to boot and see if that's what you want.

If it is, you can make te changes permanent by doing the same in */boot/grub/menu.lst*.

---

### Post by Bagboy23 on 2007-01-12
Thanks for that. I've made the changes, however I would really like the Fedora Core boot thing. I suppose it's out of the question and can't be done.

---

### Post by energiya on 2007-01-12
I like the old booting style too, so I removed "quiet splash" from my kernel line. Now I can see the nice text when booting :D . You can chance the colors (I think I saw something like this on the forums, but I like black, so I don't change them)

---

### Post by Bagboy23 on 2007-01-14
I wanted this type of boot:

[IMG]http://transamrit.net/files/temp/fedoraBootsplash.png[/IMG]

Any ideas?

---

### Post by kinematic on 2007-01-14
that's a fedora/redhat specific kernel patch called redhat graphical boot.
if can get the patch you may be able to get it to work since as i recall it functions in kernel space.
you would have to modify the patch to work with ubuntu's kernel and to display the ubuntu name but if you ask me it's a waste of time,
you would have to build each new updated kernel from source to include the patch.
on a side note,how my computer boots isn't important to me.....it's important what it boots into ;)

---

### Post by Bagboy23 on 2007-01-14
Lol, true but the thing with mine is that it's messy and it's nice to have info on what's booting and what's stalled. I often get what I think is a hang, but it's actually doing something.

---

### Post by kinematic on 2007-01-14
well....if you really want it there's only one thing i can say....happy coding ;)

---

### Post by Bagboy23 on 2007-01-16
Lol, you'll be the first person to get it when I've finished Kinematic. ;)

---

