---
title: "Out of gamut colors in GIMP"
date: 2009-11-12
forum: Art &amp; Design
---

### Post by bubblehead74 on 2009-11-12
I tried to do soft proofing in GIMP. I figured out most of it. However, I cannot see out of gamut color warning. I set the color red in Preferences, but I don't see any red. GIMP web site says I should see a neutral gray warning. How to activate this feature? :?

---

### Post by Exodist on 2009-11-12
Right above the tool tip

[IMG]http://lh6.ggpht.com/_04pMYWw39X4/SvyR5ExJ5cI/AAAAAAAAAN0/hAMhnN5MK7g/2009-11-12-165208_687x583_scrot.png[/IMG]

---

### Post by bubblehead74 on 2009-11-12
Thank you for your answer. I know that menu setting. The problem is that it does not seem to work. Can you see an actual out of gamut warning? Also, my default color in the softproofing menu is red not gray. :o I wonder whether you have a newer version of GIMP. I am using the one which came with Ubuntu 8.10.

---

### Post by Exodist on 2009-11-12
> **bubblehead74 said:**
> Thank you for your answer. I know that menu setting. The problem is that it does not seem to work. Can you see an actual out of gamut warning? Also, my default color in the softproofing menu is red not gray. :o I wonder whether you have a newer version of GIMP. I am using the one which came with Ubuntu 8.10.

My bad, I thought you just couldnt find it. I over look stuff sometimes and thought that was the case. 

So its not working? Hmm. IDK I personally never use it since I dont do editing per se and I do more creating and use a lot of translucency making theme graphics. Its possible they added the code and the interface. But disabled it and forgot to remove the interface options from the program. But IDK. It also may be that when the program was compiled that option was left out do to a dependency issue. 

Best answer I can offer is to check and make sure the newest version does work and then compile the newest version from source. GIMP is very easy to compile and most of the stuff you will need to do it will be in the repository, youll just have to install the development source packages. Sounds harder then it really is.

Sorry I cant be more help..

---

### Post by nexius on 2011-07-10
I don't know if It can still helps you but I give you the answer you need.
To see the gamut warning working, you have to choose in that menu the print simulation for the working color profile. Of course you have have also to chose a valid print color profile. Once you select "print simulation" as your working mode, if your image have some area out of the printing profile you have selected, you will see that area gray colored. One more thing, there are a lot of difference among the difference way to render the color profile... I used to use "Colorimetric Relative" to see the out of gamut area for a GMYK color profile, but I suggest you to google some more information.
hope this helps you.

By
Nex

---

### Post by prokoudine on 2011-07-10
> **bubblehead74 said:**
> Thank you for your answer. I know that menu setting. The problem is that it does not seem to work.

What settings do you actually have in that dialog? Is CMS on? What profiles are chosen?

---

