---
title: "Remove Extra Entries"
date: 2007-10-14
forum: Art &amp; Design
---

### Post by troy1of2 on 2007-10-14
So anyway, I was playing around with this Gnome Artwork Manager that someone just told me about and thinking, hey this is so cool! I can install all of this stuff from gnome-look without having to go to gnome-look to look for it. So I'm going along and I install some Icon Themes and one of them is Crystal SVG so I think to myself 'I've seen that one somewhere before.' But I install it anyway to check it out. Now, I remember where I've seen it before. It's one of the default themes that comes with Ubuntu. So now when I go to the Appearance Preferences (I'm using Gutsy) and look under the Icons tab on my custom theme I have two entries for Crystal SVG.

 No problem, I think because I can always delete the extra entry and be back to one. **WRONG** The delete button on both of them is grayed out. I assume this is because it is one of the defaults but I'd really like to remove the second entry from the list because every time I go in there it is sort of screaming out at me **YOU IDIOT, YOU INSTALLED AN ICON THEME YOU DIDN'T NEED!** and I really can't have that because it's quite embarrassing to have your Appearance Preferences yelling at you. So, can someone tell me if there is a configuration file somewhere I can edit to fix this little problem? Well, I'm sure there is, I just need someone to point me to where it is.

---

### Post by arsenic23 on 2007-10-15
More then likely the one that you installed is in your Home directory, while the one that comes with Ubuntu is in /usr/share/icons .

Just go to ~/.icons and remove the extra one.

---

### Post by troy1of2 on 2007-10-15
> **arsenic23 said:**
> More then likely the one that you installed is in your Home directory, while the one that comes with Ubuntu is in /usr/share/icons .

Just go to ~/.icons and remove the extra one.

Well, the thing is, it didn't actually install the icons in ~/.icons nor put a second set in /usr/share/icons  but it did add an extra entry into the menu so it says Crystal SVG twice in a row. So I think all I need to do is find where that menu info is saved so I can edit out the extra entry. You're right though, the other icons I installed are indeed in ~/.icons but no sign of Crystal SVG in there anywhere.

---

### Post by troy1of2 on 2007-10-15
Okay, well, I guess I sort of fixed it. I went into /usr/share/icons which only has one directory for crystalsvg which is why I reported back a bit ago that apparently no extra set of icons was installed and I thought perhaps only a menu file had an extra entry. Well, just to see what would happen I renamed  the directory crystalsvg to crystalsvg.bak thinking most likely both entries for Crystal SVG would disappear from the menu if anything changed at all. To my surprise when I went back into System>Preferences>Appearance and chose Customise>Icons there was only one entry for Crystal SVG so things were back to normal as far as the menu was concerned. So I thought to myself, well surely if I choose that one it's not going to change my icons because I just renamed that directory to something else so it's not going to find them. But lo and behold, it does indeed change all my icons to the Crystal SVG set when I select just as it normally should. So I can only guess the original Crystal SVG set is saved somewhere else besides /usr/share/icons and the one I renamed is the new one I installed tonight.

Well, this little experiment has given me an opportunity to learn a little bit more about how the system is set up but where those original icons are is still a mystery to me. I suppose I'll poke around some more and figure it out. Thank you again for your input!

---

