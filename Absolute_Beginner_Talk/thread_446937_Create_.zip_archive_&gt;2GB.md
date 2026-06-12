---
title: "Create .zip archive &gt;2GB ?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by pkh106 on 2007-05-17
Does anyone else have this problem?  Trying to archive some of my pictures and music in a folder (~8 gigs) which can be done in windows without a problem.

Trying the right-click, create archive option in Ubuntu 7.04, seems like it works (when choosing the .zip option) until it gets to 2 gigs, and stops because it can't create it any larger.

So, tried 7zip, works without a hitch in the command line, however, Ubuntu doesn't recognize the .zip file once it's created (made one 4 gigs) can't open the file when it's double-clicked?  what gives?

any thoughts, working on a NTFS formatted drive.

thanks in advance

---

### Post by Bachstelze on 2007-05-17
You're not being fair here. You make Windows work on it's own filesystem but not Linux, no wonder it can't do as well ;)

---

### Post by pkh106 on 2007-05-17
so you think i should try it on the root drive?

---

### Post by Bachstelze on 2007-05-17
I don't think it would help much if the files you want to compress are on your NTFS drive. Where are they located, exactly ?

---

### Post by pkh106 on 2007-05-17
/media/sta5/

weird problem, was able to compress it there w/ 7zip

---

### Post by Bachstelze on 2007-05-17
Does it really have to be .zip ? You'd be bettar with a b/gzipped tarball, I guess.

---

### Post by heimo on 2007-05-17
This is interesting problem. Did you try creating .tar.gz archive using right-click create archive in Ubuntu? (eg. Winzip does understand .tar.gz files too)

---

### Post by pkh106 on 2007-05-17
hmm, ok, didn't know that winzip recognizes .tar.gz files, i'll give this a run when i get back to my Ubuntu machine

hate using winblows.

---

