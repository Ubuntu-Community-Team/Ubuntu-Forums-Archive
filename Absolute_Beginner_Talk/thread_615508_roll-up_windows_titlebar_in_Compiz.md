---
title: "roll-up windows titlebar in Compiz"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by skiwithpete on 2007-11-17
I want to roll up my window title-bar on right-click.

I had previously asked how to do this in metacity, but am using compiz in 7.10 now and it doesn't work.

I want double click to be maximize and right click to roll up.  How do I do it?

Please help.

---

### Post by lpb331 on 2007-11-17
If you go into the configuration editor and go Apps - Compiz - General - Allscreens - Options, you will find an option near the bottom called toggle_window_shaded_button. It should say disabled; if you change it to "Button3" (without the quotes), it should make it happen.

---

### Post by skiwithpete on 2007-11-17
Nope, now when I right-click anywhere in a window (like Firefox) it rolls it up.

That's no good.  I only want it to do it when I right-click on the top window bar

---

### Post by lpb331 on 2007-11-17
Yeah, that could be a bit of a problem! I found that if you change toggle_window_shaded_edge (the very next option after the one I told you) to [Top] and  toggle_window_shaded_edgebutton to 3, rightclicking the very top edge while you have something open will shade it. Of course, if your window isn't fullscreen this won't get the desired effect. I'm going to keep looking for a little bit.

---

### Post by lpb331 on 2007-11-17
After searching "compiz right_click_action" in Google, it appears there is a patch that will add the option you seek into the gconf editor. However, I think you'll have to compile compiz to make that happen.

---

### Post by skiwithpete on 2007-11-17
I wouldn't know where to start to compile anything.

Can you send me a link to the page that you found?

---

### Post by runemaste644 on 2007-11-17
Well, mine does whenever I do my mouse wheel on the titlebar.

---

### Post by lpb331 on 2007-11-17
If you search google with the phrase "compiz right_click_action", either of the first two links will show you the code. One of them is 

[http://cgit.compiz-fusion.org/compiz/blob/?id=c81adad2c9a58ffa931b199d694ba860b984fa61](http://cgit.compiz-fusion.org/compiz/blob/?id=c81adad2c9a58ffa931b199d694ba860b984fa61)

I only get 3 links when I did the search. Given compiz is integrated into Gutsy, it's probably going to be a real pain in the you know what to do this. I would suggest going to the compiz forums for help with something like this, since I know I can't help you with that.

---

