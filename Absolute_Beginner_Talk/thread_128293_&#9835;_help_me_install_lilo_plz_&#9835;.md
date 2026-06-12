---
title: "&#9835; help me install lilo plz &#9835;"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by namith on 2006-02-11
i tried installing lilo through synaptic package manager.
i sed run "liloconfig 8 & /sbin/lilo" for lilo to work properly
but the second command didnt work:confused: 
so lilo also wasnt fount at bootup

[FONT="Comic Sans MS"][COLOR="Red"]HELP ME PLZ........
[/COLOR][/FONT]
:-k

---

### Post by bscbrit on 2006-02-11
You will probably not find many people rushing to answer this one because Ubuntu uses GRUB as default rather than lilo - so that aren't that many lilo users around.

What commands did you type _exactly_?

I'm not sure what 'liloconfig 8' means as a command, it looks more like a man(ual) page but, as I haven't got it installed I don't know.

Secondly,  to run /sbin/lilo you will have to prefix the command with 'sudo' i.e.

sudo /sbin/lilo

which will prompt you for your normal user password.  You could always check that /sbin/lilo exists :

ls -l /sbin/lilo

just to make sure that your installation went as you imagined.

But, finally, is there a particular reason why you want to use lilo rather than grub?  There is nothing wrong in that, but unless there is something that lilo will do that grub won't, then I'm not sure what you hope to achieve.  Just my personal opinion.  :-D

---

### Post by bscbrit on 2006-02-11
Yep! Liloconfig(8) is the manpage:

[http://www.wlug.org.nz/lilo(8](http://www.wlug.org.nz/lilo(8))
[http://www.planetpenguin.de/manpage-8-liloconfig.8.html](http://www.planetpenguin.de/manpage-8-liloconfig.8.html)

To view the manual page, assuming that you have installed it, type the following on a command line:

man liloconfig

---

