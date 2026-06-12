---
title: "No permission over drive?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Iamshiznaki on 2007-12-06
I have a portable hard drive that connects through a USB port. When I plug it in, it mounts, but I cannot write to it. Ubuntu says I don't have permission. I know the "chown" command, but the disk is called "My Book" and because of the space I can't tell the terminal to allow me to own the disk.

Help?

---

### Post by hackle577 on 2007-12-06
Use quotes around the name  when you type it in terminal.

ie, "/mnt/My Book" or whatever

---

### Post by mahiyar on 2007-12-06
To be able to get around typing spaces in linux or for that matter any special characters that character e.g space has to be prceded by a \ (backslash) like My\ Book (My,backslash,space,Book). This is true for all commands in CMD.

---

### Post by iris-n on 2007-12-06
**mahiyar**, isn't it actually the inverted slash \?
I tried your command here, no good.

---

### Post by mahiyar on 2007-12-06
Sorry, thats persistence of windows effect, it should be \, I will correct my post.

---

### Post by banewman on 2007-12-06
You could rename it my_book from windows. :)

---

### Post by ThrashJazzAssassin on 2007-12-06
What file system is the drive formatted? NTFS? FAT32? EXT3?

---

