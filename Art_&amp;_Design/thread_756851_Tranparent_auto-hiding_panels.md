---
title: "Tranparent auto-hiding panels"
date: 2008-04-16
forum: Art &amp; Design
---

### Post by bryanchicken on 2008-04-16
Be grateful if someone could point me in the right direction here as i'm having difficulties.

Basically i want a panel in gnome (currently running Gutsy btw) that is truly transparent. I can get the panel to be tranparent in that i can see the background image, but if the panel hides and an application goes fullscreen the panel still shows the background colour when it appears over the top of the application

I've tried setting the panel as solid colour  with transparency and also using a transparent image with no luck.

Hopefully that makes sense and hopefully someone can help.

Cheers!

---

### Post by LeoSolaris on 2008-04-16
I looked it up in the forums and appearently if you use a .png of a totally transparent square (which you can make in GIMP) you can make the panel actually transparent. You may have to add a slight opacity from compiz to make it work properly, but it also means your panel can be slightly non-transparent at the bottom, or what ever effect you can GIMP up.

Just make a transparent .png square with GIMP that is about the thickness of your panel, and save it someplace where it can stay out of your way (like a subfolder in Pictures) After that's done, open up the menu for your panel and select the square as the background image.

Leo

EDIT: Hmm...  I am sorry, apparently it doesn't work. I just tried and it made the exact same pseudo-transparent panel that a it was before. I suppose with a little tweaking from the opacity in compiz it would start to actually look transparent regardless of whither or not you make a small transparent .png square. Sorry bout that!

---

### Post by smartboyathome on 2008-04-16
> **LeoSolaris said:**
> I looked it up in the forums and appearently if you use a .png of a totally transparent square (which you can make in GIMP) you can make the panel actually transparent. You may have to add a slight opacity from compiz to make it work properly, but it also means your panel can be slightly non-transparent at the bottom, or what ever effect you can GIMP up.

Just make a transparent .png square with GIMP that is about the thickness of your panel, and save it someplace where it can stay out of your way (like a subfolder in Pictures) After that's done, open up the menu for your panel and select the square as the background image.

Leo

EDIT: Hmm...  I am sorry, apparently it doesn't work. I just tried and it made the exact same pseudo-transparent panel that a it was before. I suppose with a little tweaking from the opacity in compiz it would start to actually look transparent regardless of whither or not you make a small transparent .png square. Sorry bout that!

That is because someone needs to build code into GNOME's panel so it recognizes when compositing is available, and uses real instead of psuedo transparency.

---

### Post by xelapond on 2008-04-16
They added composiitng is Gnome 2.22, so they might have fixed this issue.  If not you could always submit a feature request.

---

### Post by prshah on 2008-04-16
> **bryanchicken said:**
> 
I've tried setting the panel as solid colour  with transparency and also using a transparent image with no luck.
Cheers!

Maybe you are looking for functionality only provided by the AWN (Avant Window Navigator). Unfortunately, I have not been able to get it up and running; maybe you will have better luck.

It's not in the repositories, you will will have to hunt around for it: there's a good starting point somewhere on these forums, search for  AWN...

Took my own advice... landed up with [http://ubuntuforums.org/showthread.php?t=385981&highlight=install+avant+window+navigator](http://ubuntuforums.org/showthread.php?t=385981&highlight=install+avant+window+navigator)

---

### Post by bryanchicken on 2008-04-19
cheers for the suggestions guys. I'll give it all a go and see what i come up with.

---

### Post by Hairy_Palms on 2008-04-19
if your running compiz then you if you try putting your mouse pointer over the panel then hold alt and turn the mouse scrollwheel you can send vary its opacity, not sure if this is what ur looking for or not.

---

### Post by st0n3cutt3r on 2008-04-19
> **Hairy_Palms said:**
> if your running compiz then you if you try putting your mouse pointer over the panel then hold alt and turn the mouse scrollwheel you can send vary its opacity, not sure if this is what ur looking for or not.

probably not, as it makes all icons and options on the panel equally transparent...  good suggestion though.

---

### Post by bryanchicken on 2008-04-21
Hairy_Palms,
had a go at this and yep, that is as close to what i want as i have managed. Would be good to have kept the icons non-transparent, but seeing as i actually wanted semi-transparent this will do until something better.

Shame it can't be done with plain old Gnome instead of Compiz. Having compiz turned on seems to dramatically slow my login time. Oh well.

Thanks for your help everyone.

---

