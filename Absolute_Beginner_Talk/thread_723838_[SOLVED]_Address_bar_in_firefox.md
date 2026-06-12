---
title: "[SOLVED] Address bar in firefox"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by alphaniner on 2008-03-13
Most of the differences between Win-Firefox and Ubu-Firefox don't bother me much, but there is one thing that really bugs me.  In Windows, when I click on the address bar to type an address, one click automagically selects all the text in the bar so I can overwrite it.  In Ubuntu, it takes three clicks.

Does anyone know how I can change it to work like the Windows version?  Thanks.

a9

PS: Can someone please refresh my memory on how to make a click of the middle mouse button activate mouse-to-scroll mode?  I ustacould do it but I forgot how. #-o

---

### Post by Joeb454 on 2008-03-13
You have to edit the firefox config files to change the middle-click from paste to scroll :) I can't remember how to do it off the top of my head sorry.

And I think if you click once it will select the whole text, or at least it does for me...

---

### Post by drascus on 2008-03-13
Well if you click on the icon on the left corner of the address bar instead of the text it will select all the text in one click. just keep moving the mouse to the left on the adress bar until it turns into a little hand click and bingo! one click no problem.

---

### Post by firefeather on 2008-03-13
> **alphaniner said:**
> PS: Can someone please refresh my memory on how to make a click of the middle mouse button activate mouse-to-scroll mode?  I ustacould do it but I forgot how. #-o

Go to the Menu Edit -> Preferences and then Advanced -> General -> Use autoscrolling .

I'm interested to see the answer of the other question, since clicking the favicon doesn't work on Firefox 3 Beta 3 for me...is there a preference in about:config that will continue to work after an upgrade to 3.0?

---

### Post by alphaniner on 2008-03-13
> **firefeather said:**
> Go to the Menu Edit -> Preferences and then Advanced -> General -> Use autoscrolling.

That's the ticket, thanks!

> **drascus said:**
> Well if you click on the icon on the left corner of the address bar instead of the text it will select all the text in one click. just keep moving the mouse to the left on the adress bar until it turns into a little hand click and bingo! one click no problem.

Not quite what I was hoping or but better than nothing.  Thanks!

---

### Post by noynac on 2008-03-14
> **alphaniner said:**
> In Windows, when I click on the address bar to type an address, one click automagically selects all the text in the bar so I can overwrite it.  In Ubuntu, it takes three clicks.

1) Open Firefox and enter "about:config" (no quotes) in the address bar.

2) In the filter box enter: browser.urlbar.clickSelectsAll

3) Change this setting to true by double-clicking on it.

---

### Post by munkyeetr on 2008-03-14
> **noynac said:**
> 1) Open Firefox and enter "about:config" (no quotes) in the address bar.

2) In the filter box enter: browser.urlbar.clickSelectsAll

3) Change this setting to true by double-clicking on it.

^ +1

---

