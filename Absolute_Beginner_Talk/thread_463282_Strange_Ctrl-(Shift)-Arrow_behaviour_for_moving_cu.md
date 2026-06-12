---
title: "Strange Ctrl-(Shift)-Arrow behaviour for moving cursor."
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Golyadkin on 2007-06-03
Hey everyone, 

I am loving Ubuntu this far (switched all my computers and laptop to Ubuntu after playing with the 7.04 beta until it was final. I only run XP in VMware now, because I need it for Visio.

As a long time Windows user (ever since DOS, Windows 3.11) I use a lot of keyboard shortcuts. Especially for editing text. 

**The problem**:
If I am in a program that has URL's in a textbox, the distance the cursor jumps is different than in Windows. Example: in Firefox addressbar the URL may be: 
[http://books.android42.net/view/book/187](http://books.android42.net/view/book/187)
With the cursor at the end of it, the expected behaviour for me when I press Ctrl-Shift-Left it will select the 
187" part, without the /. And if I were to press those keys again, it would select: "book/187" and then "view/book/187", then "net/view/book/187" well, you get the idea.

In Ubuntu however (in Firefox, but Nautilus does it correctly it seems, at least for the slashes) it jumps directly to the beginning of the line and selects the entire thing.

This is really irritating to me, because I am used to editing text very quickly instead of overwriting it. Is this a known issue? 

I am using a Logitech Internet 350 keyboard, and my settings are US English.

---

### Post by starcraft.man on 2007-06-03
This is very weird. I've never used this. Just spent 10 minutes testing windows/firefox versions and also looking at extensions if this had been addressed in Linux. It certainly isn't a problem with Firefox (in my XP VM it worked fine without any extensions installed). I can only surmise it has to do with how the custom Ubuntu version of Ubuntu or how Linux and Firefox interact (I don't think its a keyboard driver issue, didn't have any installed in my VM).

I'm gonna have to look into this further. For now I guess you'll have to manually select. Maybe if it hasn't already been brought up someone can code a lil extension for this... not certain, will see though.

---

### Post by steeleyuk on 2007-06-03
Same problem here with the official and Ubuntu versions of Firefox on Linux.

---

### Post by Golyadkin on 2007-06-03
Thanks for looking into it starcraft.man. I also tested with Firefox versions 2.0 and 2.0.0.4 in a regular Windows XP and Vista install, in which it works as expected. In both Firefox 32 and 64 bit for Ubuntu this issue occurs.
At first I didn't understand what was wrong, something felt off :) I use computers so much, the keyboard is a part of me, and I don't consciously use it. All shortcuts are automatic for me :)

---

### Post by Golyadkin on 2007-06-03
I did some more research, it also happens in Thunderbird. 
Try this: make a new email address and type this address:  "some.very.long@email.adress.org"
Press Ctrl-Shift-Left and instead of just selecting "org" it selects the entire line.

Maybe it is related to the textbox control of Mozilla software?

---

### Post by Golyadkin on 2007-06-03
I also tried the official ubuntu Firefox and Thunderbird 1.5, same problem. Any one any idea?

---

### Post by Golyadkin on 2007-06-04
And the same holds for Mozilla itself (the browser). So it is probably related to XUL on Linux or something... 

(btw, so many posts in this forum, a thread is only visible on the first page for 10 minutes, and then it is forgotten :))

---

### Post by Golyadkin on 2007-06-10
*bump* noone knows? *bump*

---

### Post by brink on 2007-07-16
Old thread, but since no one has responded to you...

I've experienced this as well. My guess is that it has to do how that particular field is rendered under Linux vs. WIndows. I think that may be some weird javascript overlay in the browser chrome instead of being an actual text box, whereas under Windows it's rendered by the OS instead. 

That's just a wild guess, though.

---

### Post by Golyadkin on 2007-07-16
Thanks for the reply, it could be that it is some XUL component or something,  I don't know. I am surprised there ware sofew people that care about how selection of text works :)

---

### Post by praet on 2007-08-10
Try changing this attribute in about:config or advanced settings in thunderbird.

```
layout.word_select.stop_at_punctuation = True
```

Good luck.

.praet

---

### Post by Golyadkin on 2007-08-10
Thanks a lot praet, I am gonna try it out as soon as I can!

---

### Post by Golyadkin on 2007-08-10
Alright, it works! Great, thanks a lot Praet, and welcome to the community!

---

### Post by praet on 2007-08-10
Glad it worked!

.praet

---

### Post by KhaaL on 2007-10-10
This is something that have bothered me since i started with linux. thanks a heap for coming up with this solution! :KS

---

