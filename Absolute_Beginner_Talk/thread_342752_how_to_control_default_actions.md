---
title: "how to control default actions"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by thom314 on 2007-01-20
Even though using gnome, I prefer some of the kde tools. How or where do you control the default actions that occur when ubuntu detects something? For instance, when I connect up my digital camera, I want digikam to start up and do the import instead of the ubuntu default photo import program. And when I put a blank CD in, I want k3b to start up.

---

### Post by mcduck on 2007-01-20
System/Preferences/Removable Drives and Media

---

### Post by ComplexNumber on 2007-01-20
> **thom314 said:**
> Even though using gnome, I prefer some of the kde tools. How or where do you control the default actions that occur when ubuntu detects something? For instance, when I connect up my digital camera, I want digikam to start up and do the import instead of the ubuntu default photo import program. And when I put a blank CD in, I want k3b to start up.
to start a player when you slip a cd in, go into your menu -> system ->  preferences -> removable drives and media. click the 2nd tab and insert your choice.


to open up a particular player when you double click on the cd/dvd icon on your dekstop, fire up gconf-editor, go to /desktop/gnome/url-handlers/cdda/command, then write in your choice of media editor.

---

### Post by mikewhatever on 2007-01-20
Under system->preferences check out Removable Media and also Preferred Applications.

---

### Post by thom314 on 2007-01-20
Ah! Thank you very much.

---

