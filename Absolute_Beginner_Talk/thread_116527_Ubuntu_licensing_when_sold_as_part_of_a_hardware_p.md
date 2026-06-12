---
title: "Ubuntu licensing when sold as part of a hardware package"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by dave@zecki on 2006-01-12
Apologies for logging this question here but I could find no other forum where it seemed to fit.

Basically, what I'd like to know is in terms of the GPL under which Ubuntu (and other Linux distros) is licensed, what are the legalities of distributing the product embedded in hardware. If someone was to sell a server preloaded with Ubuntu and a LAMP stack, and an application they'd written on the server would they be under any obligation to open source the code? Assuming of course that the components of the LAMP stack itself were all under Berkely / BSD style licenses.

---

### Post by poofyhairguy on 2006-01-13
[QUOTE=dave@zecki]Apologies for logging this question here but I could find no other forum where it seemed to fit.

Basically, what I'd like to know is in terms of the GPL under which Ubuntu (and other Linux distros) is licensed, what are the legalities of distributing the product embedded in hardware. If someone was to sell a server preloaded with Ubuntu and a LAMP stack, and an application they'd written on the server would they be under any obligation to open source the code? Assuming of course that the components of the LAMP stack itself were all under Berkely / BSD style licenses.[/QUOTE]

My kind of question. First a link to the GPL:

[http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html)

And now me trying to answer your questions (yet this is not official legal advice as I am not a lawyer yet).

If you distribute Ubuntu in anyway, you have to tell people where to get the code. 

As far the as Lamp program goes, if you link to GPL software in Ubuntu in anyway you have to release that code to.

Linking and distribution is what does it. So just programing the code in Ubuntu is not enough. But as soon as you make it so it DEPENDS on Ubuntu (or a part of it), the GPL legally forces you to open your code.

If you do not wish to open your code, your best option is to use a BSD instead of Ubuntu.

---

### Post by Viro on 2006-01-13
Hmm... I was under the impression that there are a few packages in Ubuntu that are under the LGPL (like GTK+ for example). As such, if you were to dynamically link with them you needn't release the source code for your program. However, if you do statically link with LGPL libraries, you will have to reveal your source code. Am I mistaken?

---

### Post by poofyhairguy on 2006-01-13
[QUOTE=Viro]Hmm... I was under the impression that there are a few packages in Ubuntu that are under the LGPL (like GTK+ for example). As such, if you were to dynamically link with them you needn't release the source code for your program. However, if you do statically link with LGPL libraries, you will have to reveal your source code. Am I mistaken?[/QUOTE]

No. You are very correct. Thats why Gnome and GTK use the Lessor GPL.

[http://www.gnu.org/copyleft/lesser.html](http://www.gnu.org/copyleft/lesser.html)

Great thread.

---

### Post by dave@zecki on 2006-01-13
I'll check out the threads suggested, thanks a lot.

---

