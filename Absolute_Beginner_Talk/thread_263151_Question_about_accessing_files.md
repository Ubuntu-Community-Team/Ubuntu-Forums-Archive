---
title: "Question about accessing files"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-09-22
I just got Ubuntu loaded yesterday and now I need to know where do I find the equivelant of Windows Explorer and My computer?
I have a lot to learn about this OS:confused:

---

### Post by mikl2 on 2006-09-22
I'm very much a noob myself, but what I've learned so far is:
Windows Explorer =Nautilus     
Places (top panel) >Home Folder will get you there
My Computer=Computer
Places (top panel)> Computer will get you there

---

### Post by Arevos on 2006-09-22
mikl2 is quite correct. The home folder is much like "My Documents" under Windows, in that this is where you would put personal files, and where the OS puts your configurations and preferences.

However, Linux tends to enforce this rule more stringently than Windows. In Windows, it's not uncommon to have configurations elsewhere in the filesystem, or hidden in the registry, and it's also not that uncommon to have directories such as C:\Photos. Linux tends to discourage this behaviour, preferring that the user keep all their files in one place.

Another thing that may throw you is that Linux does not have drives (C:, D: E: etc), as Windows does. Instead, it maps drives and partitions straight to folders in the filesystem. For example, whilst in Windows one may have, say, a C: drive and a D: drive, in Linux you might map the first drive to the root of your filesystem (/), and have the second hard drive to keep your home folders in (/home). And whilst on Windows you may have your DVD drive at E:, on Linux you'd find it in /media/cdrom.

---

