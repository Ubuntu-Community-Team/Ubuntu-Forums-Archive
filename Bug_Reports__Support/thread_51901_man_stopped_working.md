---
title: "man stopped working"
date: 2005-07-25
forum: Bug Reports / Support
---

### Post by makhand on 2005-07-25
I really dont know how to even begin troubleshooting this, but my man files stopped working. I can find them, they're all still there, but when i type "man command-of-interest", i get 

No manual entry for command-of-interest
See 'man 7 undocumented' for help when manual pages are not available.

I figured i'd check here because maybe one of the recent updates somehow effected this. Any ideas?

---

### Post by sjmorgan on 2005-07-26
[QUOTE=makhand]Any ideas?[/QUOTE]```
man -d command-of-interest
```might be a good start.

---

### Post by makhand on 2005-07-26
Thanks for that., 
using 
[HTML]man -d command-of-interest[/HTML]
showed the debug info. From this i was able to deduce that my MANPATH variable had been tampered with by the program 'alltray'. Basically, it redirected my MANPATH to 

/home/user/.local/share/man

because it didnt recognize my system password and installed itself in my home directory. 

Anyway, if anyone ever finds this, I was able to fix it by simply doing this: 
[HTML]export MANPATH=""[/HTML] 

This made my $MANPATH variable blank, forcing the shell to go to the /etc/manpath.config for the manpath (as i understand).

sjmorgan, thanks for the help

---

### Post by jebe on 2005-07-28
hi,

seems to be a autopackage bug. if  you can reproduce it please report it to


[http://www.autopackage.org/](http://www.autopackage.org/)



jebe

---

### Post by mhearn on 2005-07-28
[QUOTE=jebe]hi,

seems to be a autopackage bug. if  you can reproduce it please report it to


[http://www.autopackage.org/](http://www.autopackage.org/)



jebe[/QUOTE]
 Yes, it's an autopackage bug, is fixed in the upcoming 1.0.5 release (will be released in a few days).

---

### Post by makhand on 2005-07-28
[QUOTE=mhearn]Yes, it's an autopackage bug, is fixed in the upcoming 1.0.5 release (will be released in a few days).[/QUOTE]

Which part is the bug? The fact that it wrecks the manpath or the fact that it doesn't recognize/accept my root password?

---

### Post by mhearn on 2005-07-28
[QUOTE=makhand]Which part is the bug? The fact that it wrecks the manpath or the fact that it doesn't recognize/accept my root password?[/QUOTE]

Both.

The MANPATH problem is actually that this variable has weird semantics: if set it completely overrides the config file instead of augmenting it like most other FOO_PATH vars do. The fix is to never set MANPATH, as modern man implementations can locate man pages for any program in the regular PATH that follow the FHS anyway.

I am not sure which root bug you are referring to there, but 1.0.4 was missing a helper binary that was needed for the autopackage sudo support to work correctly. That's fixed in 1.0.5 as well.

---

### Post by mhearn on 2005-07-29
OK, we release 1.0.5, which fixes both of these bugs (though you need to remove the export MANPATH line yourself).

To upgrade, run

"package remove autopackage-gtk autopackage"

then install something like you did the first time (by running it). It'll re-download the latest support code.

---

