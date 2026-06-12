---
title: "Skype Voicemail - where is this directory?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by danmpem on 2007-07-20
I've been having Skype Voicemail problems, so I emailed Skype tech support and they sent me this:

> We suggest you delete ~/.Skype/shared.xml and ~/.Skype/skypename/config.xml
directories.

I'm a newbie at Linux, where are these directories?  I've been searching my computer, but I can't find them.  I searched in the terminal by typing in "whereis Skype" and went through the search results, but I can't find those directories.  Can anyone help me?

Thank you

---

### Post by sancho panza on 2007-07-20
They are hidden directories in your home (~) folder. To view them, enablet hidden directories in your nautilus folder browser.
All folders starting with a dot(.) are hidden by default.

---

### Post by danmpem on 2007-07-20
Okay, I'm a REALLY big newb.  How ought I do this?  I have my KDE desktop configured so that it will show my hidden files, but I still can't find the one listed above.  Skype was installed via Synaptic Package manager, so should they be?

When I search for Skype in the terminal, I get this:

user@Ubuntu-Linux:~$ whereis skype
skype: /usr/bin/skype /usr/X11R6/bin/skype /usr/bin/X11/skype /usr/share/skype


What should I do?

Thanks

---

### Post by arashiko28 on 2007-07-20
Go to you Home folder, press ctrl+H you will see all of the hidden folders and there you will find the .skype, look in there for what they asked you.

---

