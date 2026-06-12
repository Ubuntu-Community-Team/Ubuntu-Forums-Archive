---
title: "Japanese keyboard/keymap problem in Gutsy upgrade"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Angus77 on 2007-10-26
My keyboard worked perfectly under Feisty, but now there's an irritating glitch after I upgraded to Gutsy.

Almost the whole keyboard is fine, except the key with the closing curly brace. Where I should get the closing pair of the   {   character, instead I get   |  . Instead of the closing pair of   [  , I get   \  .

I still get those two mistaken characters where they should be, so it's not that they've been switched. It's just the one key mismapped. And here I am trying to teach myself C without being able to type a closing brace!

I also had this exact problem with [Puppy Linux]("www.puppylinux.org") and [Fluxbuntu]("http://fluxbuntu.org/js.html") before, but never any other distro (Feisty, Debian Etch, Fedora 7, [DSL]("http://damnsmalllinux.org"), Knoppix).

Here's the layout of a typical Japanese keyboard (not mine, but the layout's more or less the same. My kbd's a Dell SK-8115):

[IMG]http://www.win.tue.nl/~aeb/linux/kbd/jp106.jpg[/IMG]
[IMG]http://www.win.tue.nl/~aeb/linux/kbd/jp106-with-scancodes.jpg[/IMG]

The problem key is three keys right of the   L   key, right beside the ENTER key, scancode 2B.

---

### Post by Angus77 on 2007-10-26
Please help! I seriously have to go back to Feisty if I can't fix this!

---

### Post by Angus77 on 2007-10-27
Found the solution [here]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/53206").

---

