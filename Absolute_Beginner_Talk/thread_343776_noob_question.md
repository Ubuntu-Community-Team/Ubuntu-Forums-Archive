---
title: "noob question"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by atomic drizzle on 2007-01-22
im trying to get more familiar with the command line, i was wondering how i open a rom emulator with zsnes from the commandline. im in the dir that the rom is. thanks for any help.

---

### Post by kidders on 2007-01-22
Hi there,

Just type the name of your executable. Anything beyond that (cmd line arguments, etc.) is up to the application itself.

If the app you want to start isn't in your $PATH, you often need to prefix it with a path ... even if it's just **./**

---

### Post by tonyr1988 on 2007-01-22
If you've already cd'ed into the rom directory (and if you have ZSNES installed), do this:

> zsnes --help

It should tell you about how to use it via commandline.

For most programs (I'm not sure about ZSNES), you'll just do something like this:

> zsnes name_of_rom.ext

and it'll run just fine.

P.S. Do you know about tab-completion? If not, type the first 2 or 3 letters of the rom name and hit Tab. :)

P.P.S. Some programs have manual pages to explain in-depth about using the program from the commandline. To see if ZSNES has one, try:

> man zsnes

---

### Post by atomic drizzle on 2007-01-23
thanks for the help guys. i did not know the tab thing. that will definatly make thing easier. does everything i apt-get come with a man page?

---

### Post by tonyr1988 on 2007-01-23
No, it's completely up to the developer of the program.

However, most (all?) of the built-in commands are going to have a "man page," and many other programs do, too. But some developers, especially for GUI-based applications, leave them out. :(

If a program doesn't have a man page, it will simply tell you it doesn't have one - no harm done to check.

---

### Post by atomic drizzle on 2007-01-23
thank you! :)

---

