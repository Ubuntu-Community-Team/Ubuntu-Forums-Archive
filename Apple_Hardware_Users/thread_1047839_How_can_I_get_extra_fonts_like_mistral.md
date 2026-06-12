---
title: "How can I get extra fonts like mistral?"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by Brightbelt on 2009-01-22
Hi,
 I need the mistral font to transfer a project into Linux, and I can't seem to find it. I've downloaded extra fonts through the Synaptic Package Manager, but so far, no luck getting mistral. 

I've already installed msttfwebcore fonts; that's always the first thing I do. I just installed intrepid, so I did the true type fonts right away.

I appreciate any guidance on this - for what it's worth, I want the font to work with CD printing from within Gimp.

Many Thanks, Frank B.

---

### Post by albinootje on 2009-01-22
> **Brightbelt said:**
> Hi,
 I need the mistral font to transfer a project into Linux, and I can't seem to find it. I've downloaded extra fonts through the Synaptic Package Manager, but so far, no luck getting mistral. 

You already have the Mistral fonts somewhere on a MS-Windows partition ?
A quick web search engine search gave me the impression that the Mistral fonts are not for free, is that correct ?
[http://www.fonts.com/FindFonts/detail.htm?pid=201684](http://www.fonts.com/FindFonts/detail.htm?pid=201684)

You can drag and drop fonts in your ~/.fonts directory, that should work.
Ubuntu Intrepid offers FontMatrix in the repositories, which also makes it possible to add a font.

---

### Post by Brightbelt on 2009-01-22
Thanks for responding. Kind of a Duh-moment here. 

I'm on a Mac and I just went to the Mac Applications Folder and went into FontBook and copied the font to the main User Folder. 

From there, I went into Ubuntu - did 'sudo nautilus' to get permissions - and went to the Filesystem to usr/share/fonts/msttwebcore fonts and copied the font into that folder. Voila, I can access it in Gimp just fine.

Like I said, a Duh-moment, but I've also come very close to screwing up a perfectly good computer by mishandling fonts before, so I'm extra cautious.

Many Thanks, Frank B.

---

