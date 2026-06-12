---
title: "shift+backspace annoying the crap out of me"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by avg on 2006-08-22
When I first installed xgl I had is disabled with > xmodmap -e "keycode 22 = BackSpace", but now that for some reason doesn't work anymore. I'm not able to find the tutorial that I used but I know it wasn't from the forums.

---

### Post by bulldog on 2006-08-22
Don't know about any of you lot, but i've been constantly annoyed by my lazy little finger on the shift button causing x to reset when i press shift+backspace.

Thanks to sudomania4 on the IRC channel, he's informed me that adding

Code:

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

to some sort of script at each startup e.g. "thefuture" will stop the key combo from working!

Works fine for me thought you all may want to now.

=====================

I did read that tutorial to and copied it.:p 
Put the code in your compiz startup script and it should be fine.

---

### Post by avg on 2006-08-22
In my case it isn't because I'm lazy to let go of the shift key when I make a mistake, I just forget that it is there and press the backspace key.

edit: that didn't work also

---

