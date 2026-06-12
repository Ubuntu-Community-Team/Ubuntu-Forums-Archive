---
title: "How do I cut and paste a complex string into terminal?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by pcrussell50 on 2007-07-26
From time to time, as I learn this stuff, a help suggestion comes up in which someone posts a terminal command to try out.  Frequently, they are kind of long and copying them, charactger-by-character into the terminal is tedious and fraught with the possibility of keystroke errors, so being able to copy and past the command into the terminal would be useful.

Now, coming from the DOS world, that's not possible, but most DOS commands are pretty short.  I wonder if it's possible in ubuntu?  sure would be useful.

Also, whenever I bring up a terminal under "places", it never asks me for my password or anything, which I think is odd, since with it, I can make system changes.  Maybe the "terminal" I get under the "places" menu isn't a full authority terminal, and I should be looking elsewhere for a "real" terminal?

best,
peter

---

### Post by skymera on 2007-07-26
Shift+Alt+C    copies from terminal
Shift+Alt+V    pastes into the terminall

and add to laucner.:

application > accessories > right click terminal and click add to panel

---

### Post by sumguy231 on 2007-07-26
After selecting text, you can middle-click in the terminal to paste text.

> Also, whenever I bring up a terminal under "places", it never asks me for my password or anything, which I think is odd, since with it, I can make system changes. Maybe the "terminal" I get under the "places" menu isn't a full authority terminal, and I should be looking elsewhere for a "real" terminal?
The terminal starts with only your permissions; if you want root permissions to run stuff in the terminal, use 'sudo'. (Type 'man sudo' for more info)

---

### Post by pcrussell50 on 2007-07-26
> **sumguy231 said:**
> After selecting text, you can middle-click in the terminal to paste text.


Now I feel extra dumb...how do I middle-click with a two-button mouse?

regards,
peter

---

### Post by rich.bradshaw on 2007-07-26
press both buttons at once.

---

### Post by mattze on 2007-07-26
press both buttons at once

edit:
haha funny ...

---

### Post by aysiu on 2007-07-26
I haven't seen a terminal command that's too long to paste into the terminal. Just highlight it and Control-C (or right-click and select *Copy*); then press Shift-Insert while in the terminal, and the command will paste into the terminal.

---

### Post by mikewhatever on 2007-07-26
> **pcrussell50 said:**
> Now I feel extra dumb...how do I middle-click with a two-button mouse?

regards,
peter

Shift+Alt+M was tempting, but no, that is only a joke. :) What does mid clicking do anyway?

---

### Post by eternalsword on 2007-07-26
> **mikewhatever said:**
> Shift+Alt+M was tempting, but no, that is only a joke. :) What does mid clicking do anyway?

Middle clicking pastes the primary buffer.

---

### Post by Bablefish on 2007-07-26
The simplest way to do this is move your cursor to the beginning of the text then press and hold left mouse button then at the same time drag cursor across the text. You will notice the text will now be highlighted. Now with cursor over highlighted text click on the right mouse button then use the copy command. Then open Terminal and click on right mouse button and use the paste command. It's the same as if your going to move text from one file to the next.

---

### Post by Skidpad on 2007-07-26
> **mikewhatever said:**
> What does mid clicking do anyway?
Middle-clicking allows you to paste without having to right-click and paste.  It does this automatically.

For example:
To copy a long terminal command from the forum, I simply highlight the text as normal (without right-clicking and copying...) and then go to the terminal and push down on my mouse wheel (middle click).  When I push down on the wheel, the command is pasted into the terminal.

This saves you a few clicks, as no copying/pasting/right-clicking is required.  :)

---

### Post by pcrussell50 on 2007-07-26
> **Bablefish said:**
> The simplest way to do this is move your cursor to the beginning of the text then press and hold left mouse button then at the same time drag cursor across the text. You will notice the text will now be highlighted. Now with cursor over highlighted text click on the right mouse button then use the copy command. Then open Terminal and click on right mouse button and use the paste command. It's the same as if your going to move text from one file to the next.

What you're describing sounds just like the way anyobody would cut and paste text in the windoze world.  i swear, the last time i was logged into ubuntu, [i dual boot with xp], i could highlight text with the normal ctr-c, but could not paste it into the termanal with a simple ctrl-v....but several of you have offered alternatives that I will try.  Thanks.

regards,
peter

---

### Post by aysiu on 2007-07-26
Yeah, Control-V won't work for pasting into the terminal, but just about anything else will:

Right-click and paste
Edit > Paste
Middle-click
Shift-Insert
Control-Shift-V

---

### Post by mikewhatever on 2007-07-26
> **Skidpad said:**
> Middle-clicking allows you to paste without having to right-click and paste.  It does this automatically.

For example:
To copy a long terminal command from the forum, I simply highlight the text as normal (without right-clicking and copying...) and then go to the terminal and push down on my mouse wheel (middle click).  When I push down on the wheel, the command is pasted into the terminal.

This saves you a few clicks, as no copying/pasting/right-clicking is required.  :)

Thanks, it really does that.

---

