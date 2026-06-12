---
title: "burning or converting .dmg files"
date: 2007-09-11
forum: Apple PPC Users
---

### Post by darkenedday on 2007-09-11
Alright, well I've looked through multiple threads on here on how to convert my mac os x 10.4 .dmg file to an iso file, so I can burn it to disc, does anyone know how to do this? I have tried dmg2iso, I changed the first line in the script to match my path to perl (/usr/bin/perl) and yes I am positive this is where it is, yet still I get this error

mike@Mercury:/usr/bin$ dmg2iso.pl /home/mike/mac/mac1 /home/mike/mac/maciso1
bash: /usr/bin/dmg2iso.pl: /usr/bin/perl^M: bad interpreter: No such file or directory

this does not make any sense because when I do this:
mike@Mercury:/usr/bin$ which perl
/usr/bin/perl

it gives me the same directory?

if anyone else knows anyway to convert this file let me know, or even how to get dmg2iso to work

(by the way I am running a ppc with ubuntu right now, so running the windows version through wine isn't possible)

---

### Post by stmiller on 2007-09-11
Check out[ this thread]("http://ubuntuforums.org/showthread.php?t=135913") or[ this thread]("http://ubuntuforums.org/showthread.php?t=128833") perhaps? Seems like someone had success there before. Could be a perl issue with the perl version in Feisty... :(

---

### Post by darkenedday on 2007-09-11
alright I followed the second thread there and am past the first obstacle, however now I get this error which I've never seen

mike@Mercury:~/mac$ perl dmg2iso.pl mac1.dmg mac1.iso
dmg2iso v0.2a by vu1tur (vu1tur@gmx.de)

ERROR: Can't open input file
mike@Mercury:~/mac$

---

### Post by Micthetrick on 2008-07-17
@darkenedday: your first post, i had the same one. Solved it with converting the perl-script to unix Line endings. (because it is Win)

now i get: 
Conversion failed.File may be corrupted.

dow !

---

