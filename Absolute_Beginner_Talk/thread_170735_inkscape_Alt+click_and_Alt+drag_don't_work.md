---
title: "inkscape: Alt+click and Alt+drag don't work"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-05-05
I'm going through the basic tutorial (Help/Tutorials/Inkscape:Basic) in inkscape. At the end of this tutorial page, we are taught how to "select under."
Here's a snip.
> What to do if the object you need is hidden behind another object? You may still see the bottom object if the top one is (partially) transparent, but clicking on it will select the top object, not the one you need. 

This is what Alt+click is for. First Alt+click selects the top object just like the regular click. However, the next Alt+click at the same point will select the object below the top one; the next one, the object still lower, etc. Thus, several Alt+clicks in a row will cycle, top-to-bottom, through the entire z-order stack of objects at the click point. When the bottom object is reached, next Alt+click will, naturally, again select the topmost object

I tried Alt+Click in inkscape but it doesnt' do anything. I tried both Left Alt and Right Alt. Neither works. 

Alt+Drag does a strange thing. It moves the whole program window. So my Inkscape window is maximized. When I do Ctrl+drag, it moves the window.

What can I do to fix this?

---

### Post by hanzj on 2006-05-05
I found a workaround on inkscape's page: 
> Note that on Linux, some window managers steal Alt+click, but Ctrl+Alt+click ("select under in groups") and Shift+Alt+click ("select under, add to selection") will still work.
(from [http://www.inkscape.org/archive.php?year=2004&month=09](http://www.inkscape.org/archive.php?year=2004&month=09))

But I'm wondering though if this workaround means that the main usage of these key-combos will then be lost. I've just started using inkscape, so i don't know yet.

---

### Post by testube_babies on 2006-05-05
You can change the "move window" key combo in System -> Preferences -> Windows.

---

### Post by hito1 on 2006-05-05
I'm having a very similar problem, but with the "All-in-one gestures" extension for Firefox. I need Alt+Left Click to perform the regular Left click action. 

It won't work even after changing the options at System -> Preferences -> Windows. It doesn't move the window, but it doesn't do the regular Left Click action also. :(

---

### Post by hanzj on 2007-06-15
I changed "Move Window Key" from the Alt key  to the Super/Windows Logo key. Now, Super/Windows plus mouse click and drag works. But, Alt+Click in Inkscape still does not select under.

Please  help.

---

### Post by naught101 on 2007-08-29
I'd also like to know the answer to this. I'm using Kubuntu.

---

### Post by fktt on 2007-09-24
i allso changed the alt keys window drag/move to the super key so i could use it, but now it seems as if alt doesnt work at all.. :(

**(edit: i fixed it by going to 'System > Preferences > Keyboard' then in the keyboard preferences window i went to the 'Layout Options' tab and from there in the 'alt/win key behavior' options changed it back to the default, i had changed it hoping that would fix the window movement, before i found out what i was looking for was the 'System > Preferences > Windows' instead!)**

---

