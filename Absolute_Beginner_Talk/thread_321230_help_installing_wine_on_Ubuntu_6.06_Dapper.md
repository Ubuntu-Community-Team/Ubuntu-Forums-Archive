---
title: "help installing wine on Ubuntu 6.06 Dapper"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Entase on 2006-12-18
Hi, I actually have botha question and a request, okay

1) is Wine used to accomplish the same thing that Transgaming Cedega would do, i.e. run windows games on Linux, and if so does anyone know what fps i can expect with WoW on wine, because ive thought I could use cedega, but its very, very slow, so I gave up trying.

and I was reading here ([http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)) anbout getting wine on my computer, can someone either please simplify this for me or give different instructions, because I get this error message  (E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?)

  when I put this 

(apt-get build-dep wine)

in the console, 

any suggestions or help would be greatly appreciated.

---

### Post by Erunno on 2006-12-18
Since wine is under constant heavy development I'd suggest that you add the winehq repository for dapper to your sources.list:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Install wine with "sudo aptitude install wine" and configure it with "winecfg" (type both into the terminal). In order to be able to use the command line tools you should close all other software management tools (the add/remove thing and synaptic) as some of them might be using the database and therefore you don't get the lock.

I've no experience with games under wine. Cadega is a fork from wine and they promised to send some code regarding directx implementation back to the original wine project. Well, they didn't so wine is now working on directx themselves. You'll have to give it a try and see how good the game works I guess.

---

