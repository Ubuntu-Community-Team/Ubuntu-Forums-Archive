---
title: "[SOLVED] how do i run program?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by vvvladut on 2008-02-02
I just installed the PSPP package but it did not appear in the applications menu. I looked for it in /usr/bin and found it, but it doesn't run! I double click on it but nothing happens. Then I tried creating a launcher for it, but again, nothing happens when I double click the launcher. What should I do?

---

### Post by chrono310 on 2008-02-02
I believe that is a command line program, so you must run it using the terminal. If it is in /usr/bin, then you should be able to just type the name of the program and hit enter to run it.

---

### Post by Mark_in_Hollywood on 2008-02-02
How did you install the program?

Have you checked the file permissions?

Will it run as:

sudo pspp            ?

Let us know.

---

### Post by Nythain on 2008-02-02
about a 95% chance just typing pspp in a terminal will run it... if not, then pspp --help should give you enough info about the correct syntax to get it running

---

### Post by vvvladut on 2008-02-02
> **chrono310 said:**
> I believe that is a command line program, so you must run it using the terminal. If it is in /usr/bin, then you should be able to just type the name of the program and hit enter to run it.

Thank you, you are right, it does run from terminal and it is command line based. So, if I install some application and I cannot find it in the menu, does this mean that it does not have a GUI and I have to run it from the terminal?

Have any got idea why it doesn't work when double clicking on it? 

Mark: I installed through Synaptic.

---

