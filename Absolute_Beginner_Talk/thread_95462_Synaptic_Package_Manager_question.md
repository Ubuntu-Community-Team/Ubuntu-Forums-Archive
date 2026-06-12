---
title: "Synaptic Package Manager question"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-26
hi, when i goto the Synaptic Package Manager and, in the left column, click "Installed (Local and Obsolete)" i see these programs in the screenshot below. are they installed correctly? i'm asking because i installed BitDefender and i can't find any sign of it. i have tried afew commands but none work. can you help me? thanks

---

### Post by aysiu on 2005-11-26
Local usually means you installed it with the *sudo dpkg -i packagename.deb* command. It's still installed.

---

### Post by Danielle on 2005-11-26
[QUOTE=aysiu]Local usually means you installed it with the *sudo dpkg -i packagename.deb* command. It's still installed.[/QUOTE]
thanks, aysiu. i just managed to find it :rolleyes: this is the path to it:
/opt/bdc/
this is where the FAQs are:
/opt/bdc/doc/FAQ
this is the help command:
bdc --help

here's a page that has a GUI frontend for it, click on Englsch:Google Translate for the English version.
[http://www.grautier.com/Grautier/modules/news/](http://www.grautier.com/Grautier/modules/news/)

thanks for the help.

---

