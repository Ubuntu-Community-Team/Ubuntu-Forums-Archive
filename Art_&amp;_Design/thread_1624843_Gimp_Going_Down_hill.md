---
title: "Gimp Going Down hill"
date: 2010-11-18
forum: Art &amp; Design
---

### Post by jedimasterk on 2010-11-18
Quote From:
[http://www.libregraphicsworld.org/articles.php?article_id=21](http://www.libregraphicsworld.org/articles.php?article_id=21)

What's next

Around this January Martin Nordholts decided to try estimating date of 2.8 release. He cooked up a list of features that are likely to go into this version and judging by experience figured out how much time each feature would need to be implemented. As a result release candidate of v2.8 is currently expected by the end of this year.

Apart from features that have already been started or even completed you might expect things like clipping/masking for layer groups, exporting to PDF, streamlined color management and improved assets management. Bear in mind, however, that some features like vector layers have already been ditched from v2.8 plan.

As for 2.10, the plans for this version are not set in stone. It is known that it will feature GSoC projects of this year (cage transform tool, more tools having options rendered on canvas) and is likely to feature unified transform tool for which a functional specification is already written by Peter Sikking.

Full GEGL integration is unlikely to enter 2.10, if the current state of affairs doesn't change to the better. With 3.5 active developers around (rather 2.5, for last couple of months) there is very little place for miracles. I feel there is a need to elaborate here a little to avoid confusions.
There are things the team aspires to do and there is reality in which achieving the goals is several years of hard work ahead. GEGL project already has a history of initial developers burnt out and quitting. You need several active contributors working in team to tame the beast. The way I see it, getting new contributors involved is difficult when GIMP looks like a dinosaur winking back at you and grinning. An application has to look smart to attract interested developers. Therefore implementing a better user interface instead of starting work on GEGL integration right now is a good idea. You don't have to agree with me here, of course :)

If you are developer who is interested in helping the team, but specifically interested in GEGL integration, you don't have to wait few years to get started. There is a number of changes that will be required to make this change happen anyway:

    * porting more file format loaders and savers to GEGL;
    * porting existing GIMP filters to GEGL operations;
    * implement support for 64bit per color channel precision.

So you are not a developer and still want to help the team? This is perfectly fine. As mentioned before, GIMP 2.8 is coming with new assets, so you could create good brushes and patterns that will be generic enough for a wide audience. A dedicated announcement on that will be sent out soon. You can also work on the default set of tutorials at gimp.org that currently look aging.

Remember: GIMP is a community project. The more community is interested in its evolution instead of using pirated Adobe Photoshop, the faster GIMP evolves. You might just like to contribute ;-)


But GIMP doesn't have 16bit/channel support. Photoshop does!!!. And for Astrophotgraphy you need 16bit/channel support!!. 


Can Linux companies like Canonical, Red Hat, Novell, please start investing some time and money to give Linux users some good high end "NATIVE" photo editers, and photography applications!!. Gimp does not cut it. Photography in Linux sucks right now. Plain and simple. There are Linux users who use more than point and shot cameras!!.

---

### Post by ElSlunko on 2010-11-18
Or maybe have a call for user contributions since users give their money to Adobe for their products and support.

---

### Post by earlycj5 on 2010-11-18
> **jedimasterk said:**
> Quote From:
[http://www.libregraphicsworld.org/articles.php?article_id=21](http://www.libregraphicsworld.org/articles.php?article_id=21)

Can Linux companies like Canonical, Red Hat, Novell, please start investing some time and money to give Linux users some good high end "NATIVE" photo editers, and photography applications!!. Gimp does not cut it. Photography in Linux sucks right now. Plain and simple. There are Linux users who use more than point and shot cameras!!.

For me, right now as a photographer Gimp serves its purpose and does quite well.  But I'm moving away from pixel based editing and to photo management like Bibble and Darktable, only occasionally using Gimp to touch things up.

So for this photographer (who uses more than just a P&S) photography in Linux does not suck.  We're getting more tools that suit the way more of us are working with RAW files...

I agree, I wish companies like Canonical, RH, and Novell would invest.  I wish users who want Adobe to port (not gonna happen) would just invest rather than signing petitions.

Just my thoughts, makes me think, I should donate...

---

### Post by robert shearer on 2010-11-18
We all should donate...

[http://www.gimp.org/donating/](http://www.gimp.org/donating/)


jedimasterk, you can make a difference !

EDIT... My donation made moments ago. :D

---

### Post by tgalati4 on 2010-11-18
Stars look white to me.  That would only require 1 bit.  1 for white and 0 for black.

apt-cache search astro 

This brings up a few interesting tools.

How about putting out a call for an astro-photography tool?

Lay out all of the requirements and see who shows up to do some coding.  GIMP may be too entrenched to make a clean 8-bit to 16-bit transition.  It might be easier to start over.

After all, the sky is the limit.

---

### Post by graphius on 2010-11-20
> For me, right now as a photographer Gimp serves its purpose and does quite well. But I'm moving away from pixel based editing and to photo management like Bibble and Darktable, only occasionally using Gimp to touch things up.

Agree, but would add RawTherapee...

---

### Post by earlycj5 on 2010-11-20
> **graphius said:**
> Agree, but would add RawTherapee...

RT is not in the same area as Bibble/Darktable/Lightroom/Aperture IMO.  It's like UFRAW, I can make some adjustments but for serious editing I still need Gimp to use it effectively.

---

### Post by prokoudine on 2010-11-21
> **jedimasterk said:**
> 
Can Linux companies like Canonical, Red Hat, Novell, please start investing some time and money to give Linux users some good high end "NATIVE" photo editers, and photography applications!!. Gimp does not cut it.

Oh. My. Goodness. May I hope that you are not suggesting to reinvent GIMP? :) We really could live without yet another image editor.

All the team needs is one or two people working on GIMP full-time. It's really that simple. However so far no big Linux vendor tried investing into development that much. Only Mark tried sponsoring GEGL back in 2005 or so, and it didn't work.

And right now all the new features started in Git master have to be finished so that GEGL could finally be fully used in whatever version comes after 2.8 (be it 2.10 or 3.0).

P.S. Donations are good &#8212; keep'em coming. They help developers meet periodically to discuss things or get to Libre Graphics Meeting to discuss things with other teams like MyPaint's.

P.P.S. So far nobody volunteered to do new assets for 2.8. Community project, eh? :)

---

