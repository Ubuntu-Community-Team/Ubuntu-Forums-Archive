---
title: "Change titlebar color in gnome?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by muguwmp67 on 2007-06-11
In edgy I used to be able to change titlebar colors with the theme application.  Now that I'm on feisty, all of the fonts feature an orange titlebar and I can't figure out how to change them.  I'm tired of orange, can someone help me?

---

### Post by jba6511 on 2007-06-11
you can do that by changing the themes. System -> Preferences -> Themes

---

### Post by diatribe on 2007-06-11
you have to open theme manager and then select customize, select different window borders for the title bar

---

### Post by aktiwers on 2007-06-11
I hope I understand you correct.
Go to:
System => Preferences => Themes
And pick Customize and then Color.

---

### Post by muguwmp67 on 2007-06-11
By theme application, I meant theme manager from user>preferences>settings.

The 'problem' I'm experiencing is that all of the themes have an orange titlebar.  This wasn't the case in edgy.

If I select the customization option, I can change everything except for the color of the titlebar.

---

### Post by fr3ddey on 2007-08-04
I have the same problem.. cant change the color under System > preferences > Theme
Nothing happens when i change the color. Still the orange one. Have tried to install other themes and everything but the titlebar changes then... Anyone know how i can change it?


My first post btw, great forum! :)

---

### Post by Sbarton on 2007-08-04
Strange that? I have just gone to System-Preferences-Theme and the only orange title bar is Human Theme. I have Clearlooks selected and the title bar is Blue! If I change to Human I get Orange. Unless I have misundertood the problem! Not so difficult at my age.:)
regards

---

### Post by bballer320xu on 2008-04-07
Want to bring this thread back up.  Any easy solutions here?

---

### Post by phonicboom on 2008-04-18
strange, i reinstalled compiz after messing up something else and it's all fine but my title bar is red (which isn't so bad as it sounds) -but i can't change it.

Appearance settings alter all but the color of the title bar :/

---

### Post by Tom--d on 2008-04-18
Try emerald. (you have you download themes from [www.gnome-look.org](www.gnome-look.org). Its under beryl)
Try gtk window manager

See if that changes.

---

### Post by northern lights on 2008-04-18
emerald is indeed a solution.

Simply adding metacity themes would work as well. Those also can be found at [gnome-look]("http://www.gnome-look.org"), for instance.

---

### Post by phonicboom on 2008-04-18
ok, i now know i can get cool themes

i got one, downloaded it saved it, went to appearance > install

still wont change :/

maybe a setting in compiz is preventing the change or i have a package missing???

---

### Post by bballer320xu on 2008-04-18
I dont think this is an emerald issue.  In gutsy, the background color option  handled the title bar as well.   I think this might be a bug with Hardy.  I'll revisit it in a few days when the final release comes out.

---

### Post by northern lights on 2008-04-18
mkey.

Now I'm confused. What "titlebar" are we talking about - window decorations or the top panel?

---

### Post by phonicboom on 2008-04-18
i think there is a slight cross in this thread..

I am talking about the title bar of my windows, they are red and won't alter :)

---

### Post by Triggerhapp on 2008-04-18
OK!
try these, tell me what works, and what does nothing :)
```
metacity --replace &
emerald --replace &
gtk-window-decorator --replace &
```

---

### Post by phonicboom on 2008-04-18
```
metacity --replace &
```

works!! :D

BUT! it or one of the other 2; stopped avant and compiz, wouldn't let avant reload, and when i relaunched compiz from terminal, the fix unfixed :(

---

### Post by northern lights on 2008-04-19
Yup. That was metacity's doing.

metacity is just another window manager and ("--replace") replaced compiz (the "fix").

At least we now know it's a compiz issue.

If you're happy with it otherwise, you could try [cairo-dock]("https://developer.berlios.de/projects/cairo-dock/") instead of AWN.

Else, set you're compiz settings to default, then **** around again - what happens now?

Can you give some hardware specs also?
Was this ever working or did the problem occur from the very first install?

---

### Post by sayakb on 2008-04-19
Okay, OP might try downloading some GTK themes and use them in unison with Emerald. For example, I use GTK Moomex theme + UbuntuStudio emerald theme. This gives me the beautiful window borders + the green 3D file menu bar. You might give it a try as well. Plus, to use GTK theme with Compiz, create a startup entry as:
```
gtk-window-decorator --replace &
```

This would still keep Compiz as the WM and GTK as Window Decorator.

---

### Post by phonicboom on 2008-04-19
i found my fix :)

i was playing with "Appearance" and "Compiz" but i didn't know about "**Emerald**" - and that is what i needed to be tweaking :D

---

### Post by sayakb on 2008-04-19
Emerald is a replacement to GTK, not a fix, unfortunately. Emerald might look great but what OP mentioned should be also taken into consideration, since Hardy should be able to change the titlebar color. And if that is not happening, there might be a new bug out there.

---

### Post by bballer320xu on 2008-04-20
I agree with the previous post.  There are a number of replacements (Emerald being the most popular apparently) but this does not change the fact that OOB, one cannot change the color of a window title bar as it can be done in Gutsy.

---

