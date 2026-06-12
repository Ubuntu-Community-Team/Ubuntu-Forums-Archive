---
title: "Looking for a big library"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-11-27
Hey folks. I'm looking to find a rather large collection of scripts that I could take ideas from, and also to pick up on the syntax of the Terminal . . .I'm still not quite used to the err . . ."Grammar" of Ubuntu . . .if you guys know of any sites that house a good sized selection, I'd be really appreciative. Thanks. :)

---

### Post by 23meg on 2006-11-27
Check this out if you haven't: [http://www.shelldorado.com/](http://www.shelldorado.com/)

---

### Post by thomasaaron on 2006-11-27
Two suggestions that I've found helpful.

One: Google: Advanced Bash Scripting Tutorial. There is a tutorial called ABS that starts off very simple and has a ton of great stuff.

Two: I just bought "Teach Yourself Shell Programming in 24 hours." It is for the Bourne shell (but everything in it is completely compatible with BASH (which Ubuntu uses). I recommend this book because it is REALLY geared to beginners. It explains everything in great detail.

Have fun.

Best,
Tom

---

### Post by CheshireMac on 2006-11-27
> **thomasaaron said:**
> Two suggestions that I've found helpful.

One: Google: Advanced Bash Scripting Tutorial. There is a tutorial called ABS that starts off very simple and has a ton of great stuff.

Two: I just bought "Teach Yourself Shell Programming in 24 hours." It is for the Bourne shell (but everything in it is completely compatible with BASH (which Ubuntu uses). I recommend this book because it is REALLY geared to beginners. It explains everything in great detail.

Have fun.

Best,
Tom

Thanks a lot, both of you . . .Teach Yourself Shell Programming in 24 hours . . .who wrote it, and who published it?

---

### Post by thomasaaron on 2006-11-28
Hey, here's a cool script for your library.
It was harder than crap to come by, too.'
I've been trying to come across this for months!

It can detect keystrokes in BASH.

#!/bin/bash
# Capture keystrokes without needing to press ENTER.

old_tty_setting=$(stty -g)        # Save old terminal settings.
stty -icanon -echo                # Disable canonical mode and echo
keys=$(dd bs=1 count=1 2> /dev/null)
echo you pressed $keys
stty "$old_tty_setting"           # Restore old terminal settings.

exit 0

---

