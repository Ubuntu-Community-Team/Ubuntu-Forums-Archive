---
title: "Can't get dual booting to work, please help!"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by intrepidus on 2006-12-14
I've been trying with no luck to dual boot Windows XP and Ubuntu, and no one can seem to help so far. Here's my setup:

Ubuntu is installed on hd(0).
Windows XP is installed on hd(1).

I tried to add the following lines to /boot/grub/menu.lst:

```

title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```

However, when I select XP Pro from grub's list, it just sits there at "Staring up..." and blinks a single _ over and over.

hd(1,0) is where the Windows partition is, so shouldn't this work without a problem? Why can't I make it work? Is there a solution?

---

### Post by Duck2006 on 2006-12-14
> title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1

Try this

title           Microsoft Windows XP Professional
root            (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
savedefault
chainloader     +1

---

### Post by intrepidus on 2006-12-18
> **Duck2006 said:**
> Try this

title           Microsoft Windows XP Professional
root            (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
savedefault
chainloader     +1

Now I get:

"NTLDR is missing.."

Press ctrl-alt-delete to reboot.

---

