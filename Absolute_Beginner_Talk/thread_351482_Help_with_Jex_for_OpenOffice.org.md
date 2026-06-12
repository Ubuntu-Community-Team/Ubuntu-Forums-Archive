---
title: "Help with Jex for OpenOffice.org"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by slumcat05 on 2007-02-02
OK, I've looked everywhere for help on this and can't find what I'm looking for, so I figure it's time to post my very first help thread.

I'm trying to install Jex, a MathType-like equation editor Java script for OpenOffice (version 2.0.4 on Edgy). I've gotten through most of the installation (at least I think, the scripts don't have any verification like "Success" or something, so who knows), but I'm stuck on the final step:

> if you are using Linux open a console as root. Type locale charmap<enter>. If the result is ISO-8859-1 stop. If it is not, for example it is UTF-8, type which openoffice.org-2.0<enter>. Then cd directory-in-which-openoffice.org-2.0-is-located<enter>. Then gedit openoffice.org-2.0<enter>. Before the line exec /etc/openoffice.org-2.0/program/soffice "$@" insert the line LANG=en_US. Save the file.

The "locale charmap" statement is returning UTF-8, so I tried the next instruction "which openoffice.org-2.0"... nothing. I did a search for anything called "openoffice.org-2.0", I even did a search for "openoffice*" and got many results but nothing resembling this file. It seems to me like the Ubuntu installation of OOo names the file differently or something.

Does anybody know what file I should be looking for, or where I can find it? Or is there another way to make this program work? Has anybody installed Jex and gotten it to work properly? Is there perhaps another equation editor for OpenOffice that anybody knows of? Any help would be greatly appreciated, as just about every paper or lab report I write is littered with equations and the built-in equation tool in OOo seems rather useless. Thanks in advance.

---

### Post by slumcat05 on 2007-02-02
UPDATE:

It looks like OOo's "Math" is actually a little more useful than I thought. While still not as functional and user friendly (in my opinion of course) as MathType, I'm beginning to get the hang of it.

Still if anyone figures out my problem, I would still appreciate the help, as Jex appears to be more MathType-like in implementation.

---

