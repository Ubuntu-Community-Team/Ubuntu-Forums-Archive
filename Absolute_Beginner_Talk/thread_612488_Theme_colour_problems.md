---
title: "Theme colour problems"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-13
For some reason i can't change the colour of my selected window.
The border around any window i have selected is a deep red colour, no matter what changes i make in 
system>preferences>appearance
i can't get my current window to change from this deep red.
i'm clicking my theme and then selected customize and going over to the colours tab, but after doing that, i have nothing set as this deep red colour.  How can i get rid of this.
also, i find my minimize/maximize/X buttons in the top right of my windows to be boxy. how can i change these?

i made my own theme based on clearlooks, then just modified colours, etc.

Any ideas?

---

### Post by jordank on 2007-11-14
urgg this is actually getting really frustrating. i've tried changing everything, nothing seems to change my dark red borders for current windows.  anyone?

---

### Post by jordanmthomas on 2007-11-14
Is there any way you could post a screenshot of what's wrong.
I'm a little confused.

---

### Post by jordank on 2007-11-14
hrmm. k i got the screenshot l need to figure out how to post it somewhere to link. any suggestions? one sec.

---

### Post by jordanmthomas on 2007-11-14
When you are replying, hit the "Go Advanced" button at the bottom and you can upload it straight to the forum.

---

### Post by jordank on 2007-11-14
alright. test.

---

### Post by jordank on 2007-11-14
notice the red border. i cant get rid of it.

---

### Post by jordanmthomas on 2007-11-14
Ah, I see what's up.
You are using emerald as your window decorator.

You can either switch back to gtk-window-decorator (which I'm not sure how to do in a default gutsy install...in Arch I use fusion-icon)

OR

You can change this theme by running
```
emerald-theme-manager
```
(you should also have an icon under system --> preferences I think)

---

### Post by jordank on 2007-11-14
alright, that fixed things. but now i've got a new problem.
accidentally deleted my X buttons in the top right.
how do i get these back?
ahah. crap.

---

### Post by jordanmthomas on 2007-11-14
Did you lose the whole title bar or just the buttons?
If you lost the whole bar, press alt + f2 and type:
```
 emerald --replace
```

If it's just the button, just select a new theme and then the theme you want, or you can edit the theme, and go to the titlebar tab.  Then, there's a section that lets you set up the order of the buttons.

---

### Post by jordank on 2007-11-14
hrmm i keep screwing up the buttons in the top right. how do i restore defaults?

---

### Post by jordank on 2007-11-14
it's just the buttons. i can move from theme to theme, but the buttons are still screwed up. if you look under the button tabs i completely removed the X ones.

---

### Post by jordanmthomas on 2007-11-14
To restore the default buttons, select the default theme.
Each theme has different buttons.  There are several color variations of the default theme that have the same buttons.

These themes are called slatehorn.

Hmm, maybe another screenshot is in order?  I am confused again.  :)

---

### Post by jordank on 2007-11-14
notice the first button row, and also the maximize one. they arent what they should be. how do i change them back to normal?

---

### Post by jordanmthomas on 2007-11-14
I'm not sure why that's happening unless you changed the buttons yourself.  It would likely be a pain to go and find the proper buttons, so I would take the lazy way out.

Try this:
```
 rm -r ~/.emerald
```
This will clear your options you've set for emerald (and revert you back to the default red theme)
Log out and back in or restart compiz, and it should be fixed.

---

### Post by jordank on 2007-11-14
alright, thank you that fixed things up.  Now where can i find preset themes? i want some better looking buttons for up top. it would almost be better to get rid of the grey squares around them. Is this possible?

---

### Post by jordanmthomas on 2007-11-14
Well, it appears to be down, but [http://gnome-look.org](http://gnome-look.org) has emerald themes.
Just download one, and click import in emerald-theme-manager.

It is possible to change the buttons without changing themes, but the main difference between themes is the buttons anyway.  You've already found the place to do it.

---

### Post by jordank on 2007-11-14
Hrmm, lets say i wanted to get rid of the boxes around the minimize, maximize, and close button at the top right, and instead just have the pictures.
For example. in the top right, instead of the x that was there in the previous pictures, i just want a red X, without the box around it.
is this possible?

---

### Post by jordanmthomas on 2007-11-14
Yes, but you'd have to edit the picture for the button yourself.  The buttons are just png images that you can edit in the gimp.
Basically, the "boxes" you speak of ARE the pictures.

I'd suggest just getting a premade theme, though, unless you have a feel for how the themes work.

---

### Post by jordank on 2007-11-14
ahh i see. well thank you anyways

---

### Post by Eion on 2007-11-20
What if there aren't any themes to choose from?  I did this same thing, tried to make my window border not red, then I screwed up my buttons.  Is there anyway to install a new theme?  Sorry for the noobtasticism.

---

### Post by jordank on 2007-11-20
yeah, i'm using the same old plain buttons, it'd be nice to have some variation.  lemme know if you find some button themes to choose from.

---

### Post by Eion on 2007-11-20
Where would I find the said plain buttons?  Right now I have nothing, no buttons at all.  Is there a place to download Emerald themes?  Then, how do I install them?  I'm kinda new to this.

---

### Post by Eion on 2007-11-20
Ok, I downloaded a theme, but I can't get it into emerald.  How am I supposed to do this?

---

