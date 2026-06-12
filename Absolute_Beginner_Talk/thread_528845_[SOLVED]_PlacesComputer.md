---
title: "[SOLVED] Places/Computer"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-08-18
The output of 

mark@Lexington:/media$ ls
cdrom  cdrom0  cdrom1  floppy  floppy0  UDISK 28X
mark@Lexington:/media$ 

seems to indicate that the OS hasn't found the dvd player. Or is that what cdrom1 means?

Also, why is there a cdrom then cdrom0 cdrom1?

---

### Post by Hospadar on 2007-08-18
It'll say cdrom even for a dvd player.  I have a dvd burner that works fine although it is still listed as cdrom0

---

### Post by mali2297 on 2007-08-18
> 
Also, why is there a cdrom then cdrom0 cdrom1?


*cdrom* is a just a link to *cdrom0* I think. You can check by typing *ls -l*.

---

### Post by Mark_in_Hollywood on 2007-08-18
I try very hard to research my problems and then post questions that -- using the process of elimination -- lead to a solution.

This thread isn't helping and I accept that cause and effect as my inability of always convey what is not working.

I'm marking this thread CLOSED and submitting a more complex question, that may prompt an answer.

---

### Post by phenest on 2007-08-18
They are mount points. They are not the actual hardware.

---

