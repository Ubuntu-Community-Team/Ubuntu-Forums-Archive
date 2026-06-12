---
title: "Printing to standalone network printer"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2007-02-09
People,

There are two standalone (not behind a printer server) network printers in my LAN:
1) A Kyocera FS-9000 @ 10.5.1.210
2) A Kyocera FS-1800 @ 10.5.1.160

Login to the Microsoft network domain is not required to access the printers.

I followed some instructions found in [this thread]("http://www.ubuntuforums.org/showthread.php?t=351690") but the printer manager says "printer does not exist.".

What should I do to have them working?

Thanks in advance.

---

### Post by edwardLS on 2007-02-09
See this thread: [http://www.ubuntuforums.org/showthread.php?t=354611](http://www.ubuntuforums.org/showthread.php?t=354611)

I don't know if that will help, but I have a network standalone printer and just last eveing solved my problem.  If it help - great, if not, sorry!

---

### Post by paulozzzz on 2007-02-09
> **edwardLS said:**
> See this thread: [http://www.ubuntuforums.org/showthread.php?t=354611](http://www.ubuntuforums.org/showthread.php?t=354611)

I don't know if that will help, but I have a network standalone printer and just last eveing solved my problem.  If it help - great, if not, sorry!

Thanks, Eduard, but both printers are **Kyoceras**, which means JetDirect doesn't apply.  Even though I gave it a try, for no avail.  Thanks anyway.

Problem remains.

---

### Post by question_chick on 2007-02-09
I don't know how much help this will be but when I had to install a standalone printer I used the UNIX printer option in the add printer dialog box and then just added the ip address, you don't need to point to a spool, it will set up a default one anyway.

After that it's just a matter of choosing your drivers  from the list provided.

---

### Post by paulozzzz on 2007-02-09
> **question_chick said:**
> I don't know how much help this will be but when I had to install a standalone printer I used the UNIX printer option in the add printer dialog box and then just added the ip address, you don't need to point to a spool, it will set up a default one anyway.

After that it's just a matter of choosing your drivers  from the list provided.

That solved my communications problem.  I got some unintelligible output, but at least the connection settings are right.

The problem now is the driver, as my printer doesn't seem to understand PS, the other options seem to be HP oriented.  I will search for the Kyoceras' drivers an see if they work.

---

### Post by paulozzzz on 2007-02-09
The Kyocera FS-9000 understood the lj4 driver, but the FS-1800 didn't respond to any of the available driver.  It would be good if I were able to print on both printers, but one is enough.  I will search for a solution for the 1800 and I will report it back if I succeed.  I will also appreciate any solution for the 1800 someone might have.

:)

---

