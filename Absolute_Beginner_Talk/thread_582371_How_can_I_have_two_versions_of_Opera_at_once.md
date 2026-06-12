---
title: "How can I have two versions of Opera at once?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Joe Dinmore on 2007-10-19
My favourite web browser is going through an alpha/beta phase and it would be nice if I could install daily/weekly builds while still retaining my regular "stable" version.
Trouble is, I've done it backwards. I d/led a v9.5 alpha before I grabbed the current v9.24 release
My download/install routine is just to d/l the .deb to my desktop and double-click, and the error message that I "already have a newer version installed" while correct, doesn't give me any clue as to what to do next.
(I'm on my third week as a Ubuntu user, running Feisty)

---

### Post by gwoodard on 2007-10-19
So... Opera is not included in the "Supported Ubuntu Applications" but if you try "Epiphany" Web Browser I think you'll like it and is supported by ubuntu

(I prefer Epiphany with the simplicity but I prefer Mozilla Firefox for "other" areas)

---

### Post by adamorjames on 2007-10-19
Open the v9.5 Alpha deb with gdebi and find the package name (next to the word "Package") and then in the terminal type 'sudo apt-get remove "packagename"'. I think that will uninstall it, not sure though. Try it at least.

EDIT: Yes it works (it removes Opera 9.5 Alpha). I tried it myself :) You can have the stable Opera now. Not sure about having two Operas though.

---

### Post by Joe Dinmore on 2007-10-19
> **adamorjames said:**
> Open the v9.5 Alpha deb with gdebi and find the package name (next to the word "Package") and then in the terminal type 'sudo apt-get remove "packagename"'. I think that will uninstall it, not sure though. Try it at least.

EDIT: Yes it works (it removes Opera 9.5 Alpha). I tried it myself :) You can have the stable Opera now. Not sure about having two Operas though.

Thanks,  but I really want  to run more than one version (for web development purposes). There has to be a way. I was running several version of Opera, IE and Firefox under WinXP.

---

### Post by jordanmthomas on 2007-10-19
Honestly, the easiest way would be to download the standard .tgz (or .tar.gz, whetever it is) from Opera's website and extract it wherever you want.  Then, just run the opera from withing that directory.

---

### Post by corevette on 2007-10-19
> **Joe Dinmore said:**
> Thanks,  but I really want  to run more than one version (for web development purposes). There has to be a way. I was running several version of Opera, IE and Firefox under WinXP.

Last resort you could use WINE to run both Windows versions of Opera :-P

---

### Post by Joe Dinmore on 2007-10-19
> **jordanmthomas said:**
> Honestly, the easiest way would be to download the standard .tgz (or .tar.gz, whetever it is) from Opera's website and extract it wherever you want.  Then, just run the opera from withing that directory.
Do it manually? <gasp!> Never even crossed my mind.
See what using Windows for 14years will do to you?
Thanks Jordan, I'll do that. As soon as I get my head around *nix filesystem. Maybe usr/share/opera924 - seeing as how the current (alpha) is living in usr/share/opera ? 
Then I'll need to figure out how to get icons onto the desktop (and maybe into the menus) and ...
Malcolm Fraser was right!

---

### Post by jordanmthomas on 2007-10-19
I'd put int /opt....just a matter of preference in the end though.  :)

---

