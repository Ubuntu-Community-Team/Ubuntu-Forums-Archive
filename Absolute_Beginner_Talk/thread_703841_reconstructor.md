---
title: "reconstructor"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by (((X))) on 2008-02-21
I have some problems with reconstructor. It happens very fast and I see all knds of errors at the terminal window.
I installed all dependencies.
Any suggestions?

---

### Post by Hospadar on 2008-02-21
you might try piping its output to a text file so you can see the errors

if the command to launch it is "reconstructor" try something like "reconstructor > ~/Desktop/errors.txt" which would create a text file on the desktop with the terminal output

---

### Post by PeterJS on 2008-02-21
You could also pipe the out put in to a pager like less.
```

reconstructor | less

```

---

### Post by (((X))) on 2008-02-21
I downloaded tar.gz unzipped, and did sudo python reconstructor.py
Is there any difference between .deb and tar.gz?

---

### Post by PeterJS on 2008-02-21
In general? or in this case?
I don't know enough about reconstructor to give case specifics. There are somethings that can be just unpacked and run in place, and from your comments I'm not sure if reconstuctor is one of those.

But in general, a tar.gz is just an archive, it knows what files are in it and how to extract them with respect to the root of itself, but it has no understanding of what it's contents are, or how they fit in to the overall system. A deb package on the other hand is made of a pair of archives joined together, the first one contains meta data on the package explaining what it is, where it's supposed to be installed, what dependencies it requires and satisfies, and any helper scripts needed to correctly configure it's application once it's unpacked. The second archive is the program itself packed it with relative paths such that the root of the archive and the root of the real file system should match up.

---

