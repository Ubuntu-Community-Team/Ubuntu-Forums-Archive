---
title: "Where do I find the language files for pidgin?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Dj_eLmO on 2008-03-23
I am currently using Xubuntu with norwegian language. But there is a little "problem". Pidgin is currently not completly translated to norwegian. I know I can help translating at lunchpad, but that doesn't help me rigth now. 
So my question is; Where do I find the files that contain the language, and how can I translate these aplications for my self? whitout waiting for "a green ligth" at lunchpad?.

---

### Post by Dj_eLmO on 2008-03-26
Anyone?

---

### Post by twisted_steel on 2008-03-26
I've never done this before, but I did manage to dig up a few pages online.  The language files themselves start out as plaintext .po files and are then translated into a binary form (.mo).  On my computer, which is en_US, I found a .mo under GB: /usr/share/locale-langpack/en_GB/LC_MESSAGES/pidgin.mo.  I think you first want to get the original .po file from pidgin's site.  The original files might get distributed with the source code of a specific version, but I'm not sure about that.  The latest files are on pidgin's site: [http://developer.pidgin.im/l10n/](http://developer.pidgin.im/l10n/).

According to [this thread]("http://www.nabble.com/Is-anyone-working-on-Khmer-translation--td12918563.html"), you will need to install the gettext package and use the msgfmt command to convert the .po to a .mo.  You would then do ```
msgfmt -cv nn.po -o pidgin.mo
``` (or nb.po, I'm not sure which Norwegian you would need ;))  Then, copy the new file over the original and try it out.  I imagine you would want to back up the original pidgin.mo file before you do this.

There is also a [Tips for Translators]("http://developer.pidgin.im/wiki/TipsForTranslators") page.  Good luck :)

---

