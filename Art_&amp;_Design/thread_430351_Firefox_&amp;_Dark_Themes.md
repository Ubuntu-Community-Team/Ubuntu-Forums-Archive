---
title: "Firefox &amp; Dark Themes"
date: 2007-05-02
forum: Art &amp; Design
---

### Post by ~LoKe on 2007-05-02
One of the main deterrants of using a dark theme for me is the effect they have in Firefox.  What I dislike is how the tab button all have these...ugly bevels and whatnot.  Screenshot [here](http://img127.imageshack.us/img127/2430/firefoxde2.jpg).

Is there any css I can add to userChrome or the like that will make them flat again?

---

### Post by ComplexNumber on 2007-05-02
> **~LoKe said:**
> One of the main deterrants of using a dark theme for me is the effect they have in Firefox.  What I dislike is how the tab button all have these...ugly bevels and whatnot.  Screenshot [here]("http://img127.imageshack.us/img127/2430/firefoxde2.jpg").

Is there any css I can add to userChrome or the like that will make them flat again?
download [this]("http://gnome-look.org/content/show.php/Kore-GTK?content=55744") theme. the instructions for firefox are inside.

---

### Post by mojoman on 2007-05-04
Sorry to invade your  thread on firefox and dark theme but it was such a perfect title for my problem too, which is that the text in the firefox menu is black on a dark background. As far as I have seen firefox is the only application with this problem, and I got it regardless if "use system colour" is checked or not. Any ideas on this, anyone?

Oh, and btw, I too find the effect on the tabs annoying so I'm interested in that as well.

/mojoman

---

### Post by ComplexNumber on 2007-05-04
> **mojoman said:**
> Sorry to invade your  thread on firefox and dark theme but it was such a perfect title for my problem too, which is that the text in the firefox menu is black on a dark background. As far as I have seen firefox is the only application with this problem, and I got it regardless if "use system colour" is checked or not. Any ideas on this, anyone?

Oh, and btw, I too find the effect on the tabs annoying so I'm interested in that as well.

/mojoman
download [this]("http://gnome-look.org/content/show.php/Neutronium?content=46153") theme. instructions are inside.

---

### Post by kpolice on 2007-05-04
That doesn't fix his issue.

---

### Post by mojoman on 2007-05-04
> **kpolice said:**
> That doesn't fix his issue.

No, I don't think it does. That fix is, I think, for how the web-pages are displaed and they look fine the way it it. 

/mojoman

---

### Post by kpolice on 2007-05-04
If you use the default theme, this should fix the tabs:
```
.tab-image-middle,
.tab-image-left,
.tab-image-right, .tab-close-button {
	background-color: #d9d9d9 !important; 
}

.tabbrowser-tabs {
	background-color: #c9c9c9 !important; 
}

.tab-text{
	color: #101010 !important;
}
```

At least a little bit :P

---

### Post by ComplexNumber on 2007-05-04
> **kpolice said:**
> That doesn't fix his issue.
it does. the 1st screenshot is the (corrected) issue that the above solves. before the fix the background to the text entry areas were black. the 2nd screenshot showed what it was like before (i renamed the  file that fixes the issue so that it isn't recognised and restarted firefox).
is that not what mojoman is referring to?

the instructions for firefox in [this]("http://gnome-look.org/content/show.php/Kore-GTK?content=55744") theme cause the changes to be systemwide. it also appears to be the more effective version.

---

### Post by kpolice on 2007-05-04
Loke was talking about the tabs and mojoman about menu, and in the screenshot you are showing the text boxes ?

---

### Post by ComplexNumber on 2007-05-04
> **kpolice said:**
> Loke was talking about the tabs and mojoman about menu, and in the screenshot you are showing the text boxes ?
it fixes the issues associated with dark themes. the screenshots are merely an example.

[B]

mojoman[/B]
can you give a an example of the theme that the issue occurs with?

---

### Post by kpolice on 2007-05-04
Still that doesn't fix the tabs neither the menu, it is to fix the forms inside web pages and I don't think that modifying system files is the way to go. You can fix the forms by changing your userContent.css and this way the changes are applied even if the user upgrades firefox.

---

### Post by ComplexNumber on 2007-05-04
> **kpolice said:**
> Still that doesn't fix the tabs neither the menu, it is to fix the forms inside web pages and I don't think that modifying system files is the way to go. You can fix the forms by changing your userContent.css and this way the changes are applied even if the user upgrades firefox.
the original fix doesn't modify any system files. it merely adds the userContent.css file to the mozilla directory in ones own home directory.

---

### Post by mojoman on 2007-05-05
I've tried several dark themes, among them the both GTK-Kore and Neutronium which CompleNumber referred too. Everything looks good exept that the menu text (i.e. file, edit, view etc) in firefox (might be in other apps too but I've only seen it in firefox so far) is black on a black or very dark background, which renders the application unusable. I've tried the fix on both neutronium and GTK-Kore but that doesn't help at all, and as far as I've understood the fix is not for the problem that I have (and I don't even have the usual problems that many other seem to  have with dark themes). Anyway, I still appreciate the effort you're putting into it.

Thanks
/mojoman

---

### Post by ~LoKe on 2007-05-05
Karma, does your firefox theme change the default dark theme ugly tabs?  I think you posted a screenshot where it looked great.

How's that comin' along? =D

---

### Post by ComplexNumber on 2007-05-05
> **mojoman said:**
> I've tried several dark themes, among them the both GTK-Kore and Neutronium which CompleNumber referred too. Everything looks good exept that the menu text (i.e. file, edit, view etc) in firefox (might be in other apps too but I've only seen it in firefox so far) is black on a black or very dark background, which renders the application unusable. I've tried the fix on both neutronium and GTK-Kore but that doesn't help at all, and as far as I've understood the fix is not for the problem that I have (and I don't even have the usual problems that many other seem to  have with dark themes). Anyway, I still appreciate the effort you're putting into it.

Thanks
/mojoman
it shouldn't be like that. it not because of the dark themes anyway. i think there must be some other setting thats responsible. this is how i've got the colours on my firefox, and i don't have that problem.

---

### Post by mojoman on 2007-05-05
> **ComplexNumber said:**
> it shouldn't be like that. it not because of the dark themes anyway. i think there must be some other setting thats responsible. this is how i've got the colours on my firefox, and i don't have that problem.

Yep, I've tried changing thosee settings but when I change text and background it doesn't effect the text in the menus (which always stay black) and whether I have the "use system colours" checked or unchecked makes no difference. 

/mojoman

---

### Post by ComplexNumber on 2007-05-05
> **mojoman said:**
> Yep, I've tried changing thosee settings but when I change text and background it doesn't effect the text in the menus (which always stay black) and whether I have the "use system colours" checked or unchecked makes no difference. 

/mojoman
oh, thats seems odd. i wonder if its something to do with the firefox theme that you're using (assuming that you're not using the default theme). 
the fix that i first mentioned earlier doesn't actually address the particular problem that you're having, but it addresses most dark theme issues, so at least some good would have come from it. in fact, my firefox menus have neevr had dark writing on a dark background whatever gtk or firefox  theme i've been using, nor at any time.
thats a strange problem.

btw note that you have to restart firefox for changes to come into effect. don't know if you already know that.

---

### Post by mojoman on 2007-05-05
> **ComplexNumber said:**
> oh, thats seems odd. i wonder if its something to do with the firefox theme that you're using (assuming that you're not using the default theme). 
the fix that i first mentioned earlier doesn't actually address the particular problem that you're having, but it addresses most dark theme issues, so at least some good would have come from it. in fact, my firefox menus have neevr had dark writing on a dark background whatever gtk or firefox  theme i've been using, nor at any time.
thats a strange problem.

btw note that you have to restart firefox for changes to come into effect. don't know if you already know that.

I use the default firefox theme so it's not that and I've restarted it so it's not that either. Really weird. Oh, well, I'm settling for a lighter theme for now but if anyone comes up with a fix I'm interested.

---

### Post by guillepb on 2007-05-08
I applied the usercontent.css fix and it almost did the trick for me, but it seems to be ignoring the style for checkboxes, anybody has any idea why? There seems to be a handler for them in the css files...

---

### Post by ComplexNumber on 2007-05-08
> **guillepb said:**
> I applied the usercontent.css fix and it almost did the trick for me, but it seems to be ignoring the style for checkboxes, anybody has any idea why? There seems to be a handler for them in the css files...
 see the last sentence in post 7 - that is a link to a theme that contains the instructions for the firefox fix.  its the html.css file fix which does the trick for your particular problem. make a backup copy of your html.css by renaming it to htmlOLD.css.

---

### Post by guillepb on 2007-05-09
That did the trick, thanks a lot (I should read posts more carefully, sorry for that)

Now, if I only I could figure out why sites like [www.tvsquad.com](www.tvsquad.com) look so messy with my dark theme (check out the dark font on dark background and the messy side menu on the left on the screenshot attached...)


[COLOR="Blue"]**Edit: OK, Ignore this post, I'm just dumb (I should _definitely_ read posts more carefully, sorry again)**[/COLOR]

---

