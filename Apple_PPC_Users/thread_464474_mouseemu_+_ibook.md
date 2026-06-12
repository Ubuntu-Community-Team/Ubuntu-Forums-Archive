---
title: "mouseemu + ibook"
date: 2007-06-04
forum: Apple PPC Users
---

### Post by johne on 2007-06-04
after moving my old ibook over to ubuntu this weekend, im totally sold.

one issue tho, i really hate using f12 as my right-click button. i'd really like to ctrl + click instead, similar to the feature in osx. after doing some reading around on google and forums here, i found the best way to do this is through a package called mouseemu. 

after following numerous guides/steps i still havent been able to get it working properly. could this due to the latest release 'feisty fawn'? most of the posts that said it works were from over a year ago and alot has changed since then.

ive installed mouseemu, uncommented the lines that i want to use for right and middle click, ive also commented the lines out in sysctrl thinking maybe it was conflicting with mouseemu. i even tried using showkey to "update" the right keymap, but still nothing seems to work.

any ideas? or could someone please help me or at least put me in the right direction?

---

### Post by stmiller on 2007-06-04
Mouseemu has been a buggy program in the past few ubuntu releases. It might be having some issues. Ask in the #ubuntu or #debian channel on irc.freenode.net. Some there might have more current info.

---

### Post by johne on 2007-06-05
well its good to know that its not just me, its such a good idea - hopefully someone can revive this app.

i read in a few posts that in earlier versions of ubuntu like 5.x that ctrl+click was standard for a right click in ubuntu...i wonder why the move to f12, doesn't seem very logical to me.

---

### Post by ditsch on 2007-06-07
I am using mouseemu on an iBook G4 in Feisty and it works stable for me. This is my /etc/default/mouseemu:

```
MID_CLICK="-middle 0 87"         # F11 with no modifier
MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
RIGHT_CLICK="-right 0 88"        # F12 with no modifier
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
SCROLL="-scroll 56"              # Alt key
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

```

---

### Post by luckyd on 2007-06-07
Wait... Your saying that mouseemu right click works for you?

---

### Post by ditsch on 2007-06-07
Yes. Ctrl+Click, just as in OS X.

---

### Post by luckyd on 2007-06-07
Ok, I got that much working, but after you set up mouseemu all my ctrl options are lost. Is there a way to map the super apple key to ctrl, so it will be just like os x?

---

