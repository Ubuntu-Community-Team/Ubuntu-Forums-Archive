---
title: "Ambiance terminal theme on other themes?"
date: 2011-01-19
forum: Art &amp; Design
---

### Post by bornagainpenguin on 2011-01-19
I'm currently running with the "New Dejavu" theme and am pretty happy with it, except for the fact I miss the way my terminal looked in the Ambiance theme.  Is there a way to export that look to other themes?

--bornagainpenguin

---

### Post by bornagainpenguin on 2011-01-22
Is this the wrong place for this thread or does no one know how to export the Lucid Lynx Terminal theme?

--bornagainpenguin

---

### Post by Copper Bezel on 2011-01-22
I'm not certain that I understand your question. Do you mean the theme (like the system skin,) or do you mean the terminal profile? I don't know if the profile can be exported, but if you go to Edit -> Profiles, you can change the appearance of the terminal window however you want it. 

If you mean the skin - that is, the title bar and window border, controls, and menus - those are all set system-wide, so there's no way to make one particular window come up with a different theme than others.

---

### Post by bornagainpenguin on 2011-01-24
> **Copper Bezel said:**
> I'm not certain that I understand your question. Do you mean the theme (like the system skin,) or do you mean the terminal profile? I don't know if the profile can be exported, but if you go to Edit -> Profiles, you can change the appearance of the terminal window however you want it.

That allows me to set the translucence but not get that off purple black that can be seen in the original theme.

> **Copper Bezel said:**
> If you mean the skin - that is, the title bar and window border, controls, and menus - those are all set system-wide, so there's no way to make one particular window come up with a different theme than others.

No, I have those variables set via a theme downloaded from gnome-look, I'm trying to *keep* those but get the exact same terminal seen in the default Lucid theme.  Can this be done?

--bornagainpenguin

---

### Post by bornagainpenguin on 2011-01-24
Maybe some pictures would help explain things better?

This is my current desktop:

[IMG]http://img233.imageshack.us/img233/1603/current.png

What I'd like to do is get the terminal from the Ambiance theme to show up in that desktop, displaying the translucent  purple background and white text seen here:

[IMG]http://img815.imageshack.us/img815/6964/terminal.png

I can see how to get the terminal to be transparent but I don't know how to get the correct shades of purple and change the text to be white.  Any ideas?

--bornagainpenguin

---

### Post by ruegore on 2011-01-24
With a terminal open, click on EDIT -> PROFILE PREFERENCES

1) Click the tab named "Colors".
Remove the check from "Use colors from system theme" to enable your own color choices. Click the "Built-in Schemes" dropdown menu and select "Custom".
[[IMG]http://img815.imageshack.us/img815/7208/pic1t.th.png[/IMG]](http://img815.imageshack.us/i/pic1t.png/)


Then click "Text Color" and "Background Color" and make your color choices there. Click the handy eyedropper tool, then use your mouse to click anywhere on your screen on the color you see that you want. Want that cool dark purple color? Just click on it when you use the eyedropper tool!
[[IMG]http://img209.imageshack.us/img209/7828/pic2mq.th.png[/IMG]](http://img209.imageshack.us/i/pic2mq.png/)


2) I guess you already know how to mess with the Background of the Terminal. Just click on the tab "Background" and go to town.
[[IMG]http://img826.imageshack.us/img826/9518/pic3er.th.png[/IMG]](http://img826.imageshack.us/i/pic3er.png/)

---

### Post by Copper Bezel on 2011-01-24
And if you want to go really nuts, setting a .png image as a background respects the alpha channel, so you can do frosted effects in the transparency. = )

---

### Post by bornagainpenguin on 2011-01-25
> **Copper Bezel said:**
> And if you want to go really nuts, setting a .png image as a background respects the alpha channel, so you can do frosted effects in the transparency. = )

Awesome!  That guide was exactly what I was looking for, although I admit I feel a bit silly for having missed the obvious now.  I guess I just assumed it must be more complicated than it was...

Could you suggest some .png backgrounds to me though  I'm not really sure where I can find some that would be right for this type of thing.  (Or is this something that I can find in gnome-look?  Hmm...I'll do some searching.)

Thank you very much for your help!

--borngainpenguin

---

### Post by Copper Bezel on 2011-01-25
For the frosted effects? I think you'd have to make them yourself, and just messing with it, I'm not sure that I'm doing it right, although I could swear I had this working earlier.... Blech. = P

---

