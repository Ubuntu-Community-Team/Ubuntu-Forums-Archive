---
title: "Ubuntu Themes questions"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by bobbo85 on 2008-04-07
I need a quick explanation of the different applications and how they produce the "look" of my desktop.

I have installed compiz-fusion, and I love its effects.  But sometimes it messes up, and apparently another program called "metacity" takes over.  I have to run some command to replace metacity with compiz to get my effects back.  On top of this, I keep seeing names like GTK, GTK2, GTK+ mentioned everywhere, but I don't know what they are.  Today, I am thinking of installing emerald theme manager, and I'm a little worried what that will do to everything.

So how do all of these things work together?

---

### Post by snobby500 on 2008-04-07
a quick explanation:

Metacity is the thing that makes you window borders and bars, so where the minimise/maximise buttons are and the the border around the rest of the window, when you install emerald, you replace this with a different one that some people think looks better (some people like metacity), emerald has some themes with glossier and transparent window bars which look nice.

GTK is the buttons, the menu bar, and other bacjkground parts like the aplication drop down, and just under the wondow border, here is a link to a slightly unrelated topic but has a good explanation of GTK and the difference it has to metacity. However i am not sure what the difference is between al the different GTK's, sorry.

[http://ubuntuforums.org/showthread.php?t=748010]("http://ubuntuforums.org/showthread.php?t=748010")

Metacity and GTK come default in ubuntu but what you want to do is replace metacity with emerald.

hope this helps

p.s. take a look at gnome-look.org if you want to see some other themes for GTK and metacity, as 
i think they might be less likely to give you trouble (but hold me to that)

---

### Post by Therion on 2008-04-07
**snobby500** pretty well summed it up.  Metacity and GTK handle formatting your windows and your window decorations (borders, buttons, etc).

Compiz handles compositing your windows.

Emerald, should you install it, will work in conjunction with Compiz.  This means that Compiz will, automatically when it starts, look to see if Emerald is installed.  If Emerald IS installed, Emerald will be come the new default Window decorator.  This used to drive me nuts as I didn't WANT Emerald decorating my Windows, I wanted Metacity and Compiz; but I digress.  I just wanted to point out that if you install Emerald it will sort of "take control" of your window decorations whether you want it to or not.

---

### Post by Faud on 2008-04-07
what version of Ubuntu are you running ?

---

### Post by bobbo85 on 2008-04-08
I've got the lastest Hardy Beta.  I know there's a seperate forum for that, but this issue I felt was more general and applied to Gutsy as well.

---

