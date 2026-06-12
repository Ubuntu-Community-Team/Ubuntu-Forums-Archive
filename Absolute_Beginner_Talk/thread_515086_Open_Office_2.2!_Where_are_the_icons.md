---
title: "Open Office 2.2! Where are the icons??"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2007-08-01
Hello there! Could someone tell me what happened to icons on this release? It's all text (Bold, Italic, UnerLine) what happened to icons? 
Damn OpenOffice is the only things that makes me want to go back to windows (after 2 years with no windows at all, and feeling good :) . Did they skip the usability issues in the process of this new version?

The worst part was to insert the drawing bar and have words like Rectangle, Circle... instead of shapes represantin the actions. What a #$%#


Regards

---

### Post by p_quarles on 2007-08-01
The Ubuntu version of OpenOffice.org ships with a limited set of themes. You're getting the text because you switched your desktop theme, and didn't install the OOo icons for it. Here's how to fix it:
```
sudo apt-get install openoffice.org-style-andromeda openoffice.org-style-crystal openoffice.org-style-default openoffice.org-style-industrial openoffice.org-style-tango
```
Just cut and paste that into a terminal, and you'll install all the icon sets.

---

### Post by SlugO on 2007-08-06
> **p_quarles said:**
> The Ubuntu version of OpenOffice.org ships with a limited set of themes. You're getting the text because you switched your desktop theme, and didn't install the OOo icons for it.

Wow, now **that** is a stupid thing to leave as a default. So if you switch your theme you should automatically know that you also need to install new OpenOffice themes or your OO is left completely unusable? There is absolutely no way of knowing that without prior knowledge of the matter or some random Synaptic browsing.

Not very user friendly in my opinion...

---

### Post by p_quarles on 2007-08-06
> **SlugO said:**
> Wow, now **that** is a stupid thing to leave as a default. So if you switch your theme you should automatically know that you also need to install new OpenOffice themes or your OO is left completely unusable? There is absolutely no way of knowing that without prior knowledge of the matter or some random Synaptic browsing.

Not very user friendly in my opinion...
First of all, these forums are here in order to answer questions such as "where did my OpenOffice icons go?" They are not here for petulant whining.

Second, it *does not* render OpenOffice unusable -- it simply replaces the icons with the text. It's a slight nuisance, and if it's a dealbreaker for anyone, they really need to go back to Windows.

---

### Post by SlugO on 2007-08-08
> **p_quarles said:**
> First of all, these forums are here in order to answer questions such as "where did my OpenOffice icons go?" They are not here for petulant whining.

Second, it *does not* render OpenOffice unusable -- it simply replaces the icons with the text. It's a slight nuisance, and if it's a dealbreaker for anyone, they really need to go back to Windows.

I don't think it's such a bad thing to post some opinions on the forums too. Hardly against the code of conduct I believe.

Maybe my post did seem a bit whiny but I still see the text toolbars as a bad default after switching themes. Only a small fraction of the tools can be seen and if the user isn't very familiar with Synaptic then he isn't going to find the solution himself.

Might be a good idea to install the basic OO theme as a default too or at least notify the user about it after the first theme switch.

---

### Post by lwalsh on 2007-08-28
hi there

I had the same problem, and thanks to this post I was able to fix it. 

That said, Id like to say I don't think slug0 was 'whiney' at all. He had a legitimate criticism of the product and I echo it. I install and support OO for some end users and let me tell you my support calls would go through the roof if I replaced their icons with rows of text. Users interact completely differently with computers than pro's do and it IS a stupid backward step to remove the icons by default. 

And while OO is certainly not unusable by many with the icons removed, I'm sure aunt minnie would disagree!

In conclusion, lighten up p_quarles !! :)

---

### Post by philinux on 2007-08-28
Here Here :lolflag:

---

### Post by reuben on 2007-08-28
I agree, it's a really dumb default. I'm using KDE, and this fresh install of open office had no icons.

---

### Post by mpdemian on 2007-09-06
thanks a bunch p_quarles, your post put me back in business :) -- strange thing though, I would *sometime* get all the right icons, without making any changes, and still can't figure out why

cheers, anyway
  -pm

---

