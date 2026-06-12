---
title: "thunderbird 2"
date: 2007-07-17
forum: Apple PPC Users
---

### Post by ajmctaggart on 2007-07-17
Anyone using Thunderbird 2 on PPC?  Just curious since I have compiled and used an installer script, neither of which is working...anyone got any ideas?

Command line is giving me a syntax error

/opt/thunderbird/thunderbird-bin: 1: Syntax error: "(" unexpected

Just wanted to see if you guys could help...I'd really like to use Thunderbird across the board, I like it for OS X, and it'd be easier to transfer info between the two computers (Ubuntu and OS X) if I could actually get it to run on my PPC ubuntu box...

Thanks, 
ajm

---

### Post by stmiller on 2007-07-17
Hm, that error means there is a bad character "(" in the executable/launcher script. Try search mozilla forums for that. I think you may have a version that is compiled fine, but it's just that launcher script.

Or you could install the gutsy debs:

[http://packages.ubuntu.com/gutsy/web/thunderbird](http://packages.ubuntu.com/gutsy/web/thunderbird)

Though a lot of gnome stuff is built against the current Firefox/Thunderbird included with Feisty. So this deb could potentially not work. A sneaky method that I sometimes use is that you can extract the contents of this gutsy deb, run the executable from the extracted contents. This way it's not 'installed' on your machine, but you have a PPC compiled version.

---

