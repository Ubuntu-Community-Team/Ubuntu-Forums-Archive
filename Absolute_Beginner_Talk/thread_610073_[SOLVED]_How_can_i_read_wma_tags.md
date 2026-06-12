---
title: "[SOLVED] How can i read wma tags"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by ralphz on 2007-11-11
Hi

I need a command line program to read wma tags. Does anyone know one?

Thank you.

PS: I don't need to write wma tags just read.

---

### Post by erginemr on 2007-11-11
Hello,

The console program that supposedly reads WMA tags (along with MP3, OGG. etc.) is "python-mutagen".

It may be already installed in your system, which you can check with the following command in a console:
aptitude search python-mutagen

The output should be something like this:
i A python-mutagen   - audio metadata editing library 

The letter "i" at the beginning indicates that it is installed in my system. If not, you can install it with:
sudo aptitude install python-mutagen

But the actual console program to use is "mutagen-inspect" (part of python-mutagen package).

For instance the following command:
mutagen-inspect 'Abba - The Winner Takes It All.ogg'

on an OGG music file on my desktop yields the following output:
-- Abba - The Winner Takes It All.ogg
- Ogg Vorbis, 205.14 seconds, 96000 bps (audio/vorbis)
genre=
album=Pop
artist=Abba
title=The Winner Takes It All

I hope it is close to what you are looking for.

---

### Post by ralphz on 2007-11-11
THANKS

Works perfectly

---

### Post by erginemr on 2007-11-12
You are welcome. I was not sure about the WMA part, glad that it works.

Could you please also mark your thread as solved from the thread tools drop-down menu above?

Happy Ubunt'ing!

---

