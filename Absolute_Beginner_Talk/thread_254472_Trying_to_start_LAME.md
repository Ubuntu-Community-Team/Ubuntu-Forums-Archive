---
title: "Trying to start LAME"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-09-10
I want to convert a WAV file to mp3. I have Audacity bt it seems the bit rate is fixed, and I need more compression. I searched with synaptic for a suitable program and it looked like LAME was the one, but I apparently already have it installed. but I cannot work out how to start it!
Through synaptic I found the installed files:
/.
/usr
/usr/share
/usr/share/bug
/usr/share/bug/lame
/usr/share/bug/lame/control
/usr/share/doc
/usr/share/doc/lame
/usr/share/doc/lame/html
/usr/share/doc/lame/html/basic.html
/usr/share/doc/lame/html/contributors.html
/usr/share/doc/lame/html/examples.html
/usr/share/doc/lame/html/history.html
/usr/share/doc/lame/html/id3.html
/usr/share/doc/lame/html/index.html
/usr/share/doc/lame/html/lame.css
/usr/share/doc/lame/html/modes.html
/usr/share/doc/lame/html/node6.html
/usr/share/doc/lame/html/presets.html
/usr/share/doc/lame/html/switchs.html
/usr/share/doc/lame/README
/usr/share/doc/lame/copyright
/usr/share/doc/lame/TODO.gz
/usr/share/doc/lame/USAGE.gz
/usr/share/doc/lame/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/lame.1.gz
/usr/share/doc-base
/usr/share/doc-base/lame
/usr/bin
/usr/bin/lame


I don't really know what that means, but anyway I tried navigating to /usr/bin/lame and clicking on it, but nothing happened. I also tried typing lame into the terminal, but that just gave more information (which didn't make much sense to me). I also tried typing lame into the alt + F2 thing, and asking it to run it, but also nothing happened.

How to do it? (Or if I am mistaken by trying to use lame, then what is the right program for being able chose compression rate for creating mp3 files?
Thanks!
Justin

---

### Post by jordanmthomas on 2006-09-10
On a command line, run
```
lame --help
```
for example, you could do
```
lame poo.wav poo.mp3
```
to convert poo.wav to poo.mp3

---

### Post by enopepsoo on 2006-09-10
I've never used lame (I don't have an mp3 player, so I use OGG.  If lame is installed, you can try 
```
man lame
```
to read the lame how - tos.

Sorry I am not more helpful. :(

---

### Post by woodlandjustin on 2006-09-10
> **jordanmthomas said:**
> On a command line, run
```
lame --help
```
for example, you could do
```
lame poo.wav poo.mp3
```
to convert poo.wav to poo.mp3

Do you mean LAME works by typing code into the terminal? Isn't there any pretty box with menus and clickable things like any usual program I would use? I am not one at all familiar with typing stuff into a terminal.
Thanks
Justin

---

### Post by redDEADresolve on 2006-09-10
yeah man you just pull up a terminal and type lame and it will run. freaked me out too when i started using ubuntu.

if you wanna make a shortcut for it you can go into alacarte menu editor and hit edit and make your own. find a .png and creat an icon for it.

good luck!

---

### Post by jordanmthomas on 2006-09-10
I don't have audacity installed, so I can't verify this, but I believe you can use Lame within audacity.  I do know you can in Windows, but I haven't used it in Windows.  

Try looking around in audacity to see if you can find anything about lame.

As for not wanting to use the terminal, you should get familiar with it.  Often, you can do things much more efficiently and quickly.

---

### Post by woodlandjustin on 2006-09-10
> **redDEADresolve said:**
> yeah man you just pull up a terminal and type lame and it will run. freaked me out too when i started using ubuntu.

if you wanna make a shortcut for it you can go into alacarte menu editor and hit edit and make your own. find a .png and creat an icon for it.

good luck!

No, that just gives this:

justin@justin-laptop:~$ lame
LAME version 3.96.1 ([http://lame.sourceforge.net/](http://lame.sourceforge.net/))

usage: lame [options] <infile> [outfile]

    <infile> and/or <outfile> can be "-", which means stdin/stdout.

Try:
     "lame --help"           for general usage information
 or:
     "lame --preset help"    for information on suggested predefined settings
 or:
     "lame --longhelp"
  or "lame -?"              for a complete options list

---

### Post by woodlandjustin on 2006-09-10
> **jordanmthomas said:**
> I don't have audacity installed, so I can't verify this, but I believe you can use Lame within audacity.  I do know you can in Windows, but I haven't used it in Windows.  

Try looking around in audacity to see if you can find anything about lame.

As for not wanting to use the terminal, you should get familiar with it.  Often, you can do things much more efficiently and quickly.

Audacity uses some part of lame to encode mp3s, but I cannot see any choice of compression rate (I did search).

Is there no way to make lame run in a (to me) "ordinary" way, ie not in the terminal? (Do you call that "graphic"?)
Thanks

---

### Post by orb9220 on 2006-09-10
In audacity prefs>file formats at bottom mp3 export setup find library.

You must install libmp3.so seperately then point audacity to it.

---

### Post by Drakkor on 2006-09-10
My problem exactly in trying to export an edited mp3 file,but where to find
libmp3lame.so file ?  I tried to find it in synaptic,but couldn't. Thanks :)

---

### Post by orb9220 on 2006-09-10
[http://www.ubuntuforums.org/showthread.php?t=254550](http://www.ubuntuforums.org/showthread.php?t=254550)

---

### Post by latecomer on 2006-09-10
.

---

### Post by woodlandjustin on 2006-09-10
> **orb9220 said:**
> In audacity prefs>file formats at bottom mp3 export setup find library.

You must install libmp3.so seperately then point audacity to it.

Ah thanks for that! I had the lame thing installed already, but thanks for pointing out about prefs. That's where you can choose the bit rate - great!
Justin

---

