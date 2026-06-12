---
title: "Where is it written? Installing kde uninstalls xfce!"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2006-09-17
I was just wondering why and how.

I my main is ubuntu Gnome.

I had installed xfce desktop earlier and had it setup the way I like it.
Then decided to also install KDE to just to have all flavors.

Well Lo and Behold when I installed kde desktop did it install.
Well yes and uninstalled xfce. Why? 

Where in the docs does it mention that installing a third desktop uninstall the second one?

Not that big a deal but would have like to know.

---

### Post by xyz on 2006-09-17
Good question!
Perhaps if you installed a 4th desktop, you'd get number 2 back!! LOL

Edit:
Hopefully **aysiu** will drop by. Lots of writing about various desktop on psychocats but nothing there answers your question.

---

### Post by orb9220 on 2006-09-17
Is there a way to have all three?

---

### Post by Jucato on 2006-09-17
Installing another desktop doesn't uninstall a previous desktop, at least under normal circumstances. Can you describe why you think Xfce was uninstalled when you installed KDE?

---

### Post by orb9220 on 2006-09-17
Because when I sudo aptitude install kubuntu-desktop
in the term window it said it was uninstalling xfce-xxxxx and a long list of all the xfce stuff.

When I went to logon change sessions there was no longer an xfce choice. But was a gnome and kde choice.

---

### Post by Jucato on 2006-09-17
That is strange. normally it shouldn't do that. The only possible reason I could think of is that aptitude thought that a certain package on which xubuntu-desktop was dependent was going to conflict with kubuntu-desktop. Aptitude sometimes tries to be too smart for it's own good. :(

---

### Post by orb9220 on 2006-09-17
Ok thanks I'll look into that.

---

