---
title: "download complete website for offline viewing"
date: 2013-07-03
forum: Any Other OS
---

### Post by Si1414 on 2013-07-03
Hi all,

I am going to download a complete website for offline viewing. I am wondering what is your suggestion? What command is suitable for this?

Thank you for your help.

*I am using Cygwin.*

---

### Post by lisati on 2013-07-03
*Thread moved to **Other OS/Distro Support**.*
[Cygwin]("http://www.cygwin.com/") is Windows software.

---

### Post by varunendra on 2013-07-03
I prefer HTTrack, even on Windows. It's available in the repositories and the Linux version even has web interface (webhttrack), which I like more than the standalone gui on windows version.

---

### Post by tgalati4 on 2013-07-04
*curl* for a script-based webpage grabber.  Otherwise there are several firefox plug-ins for offline browsing.  Zotero for cut-and-paste of webpages into notes.

---

### Post by mastablasta on 2013-07-04
as for command - the ***wget*** should get you what you need. you can *man* it for parameters you wish to have.

wgetgui to provide a gui.

---

### Post by MG&amp;TL on 2013-07-04
```
wget --mirror <domain name>
```

Works pretty nicely for me. Make sure to replace <domain name> with your domain.

---

