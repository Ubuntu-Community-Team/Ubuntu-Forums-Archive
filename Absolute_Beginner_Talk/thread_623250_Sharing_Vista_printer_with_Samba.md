---
title: "Sharing Vista printer with Samba"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-11-25
Has anyone actually gotten this to work?

I'm using the printer utility (System > Administration > Printing > Samba) and I go to browse for the Vista PC I want to print on, it recognizes the name of the computer, but freezes when I press the arrow to show the printer.

How do you get them to work together?

---

### Post by Happy_Man on 2007-11-25
Well, I can get Vista to print through Samba, so I guess it should be the same thing in reverse also. When you say "freeze" though, do you mean the dropdown doesn't close for a bit but you can still keep using other apps, or that the entire comp freezes?

---

### Post by phoenix23 on 2007-11-25
The dropdown with the Vista computer's name won't open to show the printer, and the rest of the application (Printing) freezes.

---

### Post by Happy_Man on 2007-11-26
Oh yeah, mine did that for a bit in the beginning too. You see, it's trying to authenticate to the printer, and it's not getting a reply because Samba won't let the computer respond without a password, so it's just sitting there, waiting for a response and not getting one. Eventually, though, for me it asked if I wanted to just keep going anyway. That was usually after a minute or so. If it doesn't, you may need to access the folder through Nautilus and enter the password. Then it should work.

---

### Post by phoenix23 on 2007-11-26
Hmm, waiting did not work. It eventualy just gave up and the arrow drop down arrow disappeared, leaving just the name of the Vista PC.

How do I access the printer with Nautilus?

---

### Post by Happy_Man on 2007-11-27
I believe you need to go into Nautilus, get to Network:/// and access your Vista share through that. if it asks for a password, enter whatever password you use in Vista.

---

