---
title: "Coming from a Mac"
date: 2010-10-07
forum: Apple Hardware Users
---

### Post by Xilmwa on 2010-10-07
Every once in a while, I type words in other languages, and I would like to put in accents without having to remember a bunch of different numbers. On my Mac, I could type, say Opt+E then a letter to add an acute. Is there any way to set something like this up in Ubuntu 10.10?

---

### Post by MisterGaribaldi on 2010-10-09
System > Preferences > Keyboard > Layouts

Add the layout "USA International (AltGr dead keys)"

What you then do is use the Right Alt key in much the same way as with Option on the Mac.

In fact, while you're there picking the layout, print out the layout. It'll give you a nice print-out showing what keys will produce what alternate characters. Characters printed on the tops of keys are "shift" and ones printed on the bottoms are "no shift".

Good luck!

---

### Post by MisterGaribaldi on 2010-10-09
Follow-up:

Just grabbed this off my own system to show you.

Holding down the right Alt key (marked in red) and typing the [E] key will give you a é. Likewise, also holding down the shift key (marked in green) and then typing [C] will give you a ¢ sign. It's super easy to make use of.

[IMG]http://img31.imageshack.us/img31/2342/usainternationalaltgrde.png[/IMG]

---

### Post by pindar on 2010-10-09
> **MisterGaribaldi said:**
> System > Preferences > Keyboard > Layouts

Add the layout "USA International (AltGr dead keys)"

What you then do is use the Right Alt key in much the same way as with Option on the Mac.

This is not to disparage your answer, which is very helpful. I just wanted to point out that when you type not just a few words, but larger passages in a foreign language and are used to the Mac layout, this is not a solution. Getting your fingers used to the right Alt key instead of left Option will slow you down considerably; and if you double boot, going back and forth is a pain. I tried several times to understand the way the new Xorg keyboard layout configuration (I forget what it's called) worked, but in the end didn't understand it and resorted to my good old (i.e. deprecated) Xmodmap. I find it easy to configure and have written me a layout which is an exact copy of the Mac. Every now and then, I have to fix a few keyboard shortcuts in Compiz, but that's just minor. Overall, this is the easiest way for me. If anyone is interested, I can post the .Xmodmap file.

---

### Post by kaldor on 2010-10-09
On Linux I've always just used the layout switcher and switched to a different layout when I needed to type certain characters.

The Norwegian keyboard layout is great :)

---

### Post by MisterGaribaldi on 2010-10-09
Yeah, but why keep switching keyboard layouts all the time? I mean, it's one thing if you need to type characters that are nowhere remotely represented in the USA International layouts (Cyrillic, or Chinese, or maybe even Polish) but unless one is faced with such things, I fail to see to how the keyboard layout suggested above would be either inadequate, or fail to provide a relatively intuitive way to on-the-fly type accented characters.

---

### Post by Xilmwa on 2010-10-09
> **MisterGaribaldi said:**
> System > Preferences > Keyboard > Layouts

Add the layout "USA International (AltGr dead keys)"

What you then do is use the Right Alt key in much the same way as with Option on the Mac.

In fact, while you're there picking the layout, print out the layout. It'll give you a nice print-out showing what keys will produce what alternate characters. Characters printed on the tops of keys are "shift" and ones printed on the bottoms are "no shift".

Good luck!
Right alt might take me a little while to get used to, but thank you!

---

### Post by Xilmwa on 2010-10-09
It had started to work, I could hold down opt and it would allow me to add accents to characters, but then I screwed something up and it only does acutes now. Anyone know what's going on?

Edit: nvm, it switched the locations on me.

Also, I found the solution for right alt, in that options dialog, there's an option for left alt under "Key to choose 3rd level"

---

