---
title: "How do you UNinstall *.bin file"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-12
I downloaded RealPlayer 10 and cannot get the plug in to work for streaming audio and have not had responses to my posts. I have searched this issue and gone through rather convoluted procedures - so far to no avail - to get this working.
It occurs that maybe I installed it in the wrong directory - although the instructions from the site do not say where it should go (see below) - However I would like to remove and re-install and being a new user i do not have a clue how to do this and cannot seem to find an answer.
Below is how I installed (program seems to work fine - except for the 'streaming audio aspect)

[COLOR="Blue"]Installation Instructions
- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.[/COLOR]

---

### Post by Mustard on 2006-04-12
I'm a not so new user and I'm not even sure how you would go about it. :)

---

### Post by trent dillman on 2006-04-12
What if you run the .bin file again, using the following options:
```
-h
--help
--uninstall
```

?

---

### Post by jethro10 on 2006-04-12
[QUOTE=Mustard]I'm a not so new user and I'm not even sure how you would go about it. :)[/QUOTE]

Me neither, uninstalling software except the ones encapsulated in ununtu seems to have been forgotten about by developers of packages.

The Windows Add/Remove that works for everything ...........
Linux really need that.

It seems you need to find where everything was installed file by file and manually delete them all ?

J

---

### Post by Gustav on 2006-04-12
I hate those bin-installs :(

Mostly they put their stuff in /usr/local/, so look there and remove the appropriete folder (maybe /usr/local/realplayer/?) and probably there is a realplayer file in /usr/local/bin/

There might be an uninstall-script somewhere (probably in /usr/local/realplayer/ or something like that).

You never know with bin-installs :(

---

### Post by Mustard on 2006-04-12
[QUOTE=jethro10]Me neither, uninstalling software except the ones encapsulated in ununtu seems to have been forgotten about by developers of packages.

The Windows Add/Remove that works for everything ...........
Linux really need that.

It seems you need to find where everything was installed file by file and manually delete them all ?

J[/QUOTE]

Oftentimes the .bin files are some sort of closed sources application or driver.  I guess its the hazard of using closed sources on an open source system. :)

---

