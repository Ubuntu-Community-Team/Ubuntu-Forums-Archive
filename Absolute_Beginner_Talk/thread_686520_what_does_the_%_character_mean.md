---
title: "what does the % character mean"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-02-03
I probably should know this by now but can someone tell me what it means when a command is followed by % and a letter?

ex. gksudo clamtk %F           What is the % and the letter for?

Also when I download templates for openoffice the instructions are to put them in %openoffice%/usr/template directory.  What is the % for there?

Thanks

---

### Post by Dr Small on 2008-02-03
I really don't know, but I would say it defines a varaible.

---

### Post by schaumkeks on 2008-02-03
> **iansane said:**
> I probably should know this by now but can someone tell me what it means when a command is followed by % and a letter?

ex. gksudo clamtk %F           What is the % and the letter for?

Also when I download templates for openoffice the instructions are to put them in %openoffice%/usr/template directory.  What is the % for there?

I assume, the first example is from the exec key of a desktop file. % is often used as [escape character]("http://en.wikipedia.org/wiki/Escape_character") to give the following character a special meaning. For example, the desktop entry interpreter should substitute %F with the list of provided file names. See the [desktop entry specification]("http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html") for more possibilities.

The second seems to be a more abstract representation for human beings. The token surrounded by % characters has to be substituted by you to suit the environment of your system.
In this example it is because the path to the OpenOffice installation is potentially different on different systems.

Bye, Sven

---

### Post by iansane on 2008-02-03
Well the first one is the command for the clam av on my accesories menu but clam will launch with or without the %F so I didn't know why it's there or what it means. The links will probably help me understand it. Thanks you guys:-)

---

### Post by iansane on 2008-02-03
Ah yes the second link explains the clamtk %F Thanks

---

