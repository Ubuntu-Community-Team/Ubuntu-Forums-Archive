---
title: "Adding new font will slow down my PC?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-04-02
The title says it all.. I was planning to copy the contents of my roommate's PC's c:\windows\fonts folder to my /usr/share/icons/truetype/ folder.. But will more fonts make my computer slow as it does for Windows..??

---

### Post by lswest on 2008-04-02
well, i have thousands of fonts in both Linux and Windows and the only thing that slows down is the loading of the fonts folder, but, word of warning, copying windows fonts from a windows fonts folder does NOT work, at least, when i added them over 80% of the fonts did not work, and actually trashed my Xserver (until i got around to deleting the fonts i had that messed up the xserver) Best to copy a few windows fonts (stuff like imprint MT shadow does work i think) or just get them off something like [http://www.dafont.com](http://www.dafont.com) (and the ubuntu-restricted-extras metapackage has some core microsoft fonts)

---

### Post by sayakb on 2008-04-02
I did not install the msttcorefonts package but copied Tahoma, Times and some common windows fonts to the folder and they worked great. Are you sure that they don't work?

---

### Post by Therion on 2008-04-02
I've only noticed a slowdown when installing what I would call an insane amount of additional fonts (think: thousands).  The installing of a more casual number should have no effect on your system's responsiveness... Emphasis on "should", since every PC is different.

Also here's [another good source](http://ubuntu.wordpress.com/2007/05/21/300-easily-installed-free-fonts-for-ubuntu/) of fonts that you can install in "packages" with easy-peasy command line cut-and-paste.

---

### Post by lswest on 2008-04-02
I can't say for sure which don't work, but yes, i do know for a fact that some fonts from Windows just don't bode well if installed in a Linux system.

---

### Post by JustAboutRealJAR on 2008-04-02
I copied the entire windows XP fonts folder into linux with no problem... are you sure it won't work?

I only had the default windows fonts though, so maybe that's the difference.

---

### Post by Crafty Kisses on 2008-04-02
> **LinuxIsInnovation said:**
> The title says it all.. I was planning to copy the contents of my roommate's PC's c:\windows\fonts folder to my /usr/share/icons/truetype/ folder.. But will more fonts make my computer slow as it does for Windows..??

I don't think so.

---

### Post by lswest on 2008-04-02
Hmmm, it may be the Adobe fonts i had (Garamond Premier and such, which comes with the Adobe CS3) but i don't know, also, it was a Vista fonts folder i copied, and there are new fonts in Vista (different selection than XP at least)

---

### Post by JustAboutRealJAR on 2008-04-03
also, I think the new Xorg (in gutsy) has addressed the issue of bad fonts freezing the xserver

---

### Post by lswest on 2008-04-03
Hmm, i do believe i tried copying the fonts over to a Gutsy install, but i'm not sure, it seems more likely it's fixed in the new version of xorg in Hardy, if at all.  But my advice?: Make a list of the files, then copy em over, if it doesn't work, delete them. :P

---

### Post by cometa2k7 on 2008-04-03
I had a few problems when I stole all of the fonts from my Vista installation (I hate it, but I need it) Some of the fonts in Vista aren't TTF, and some just don't work. I used a Nautilus script to install my fonts though. But I haven't had any ill effects.

Some of the naming conventions of Microsoft fonts don't seem to fit in with Linux, so some failed.

Other than that, it should slow you computer down until you try to load the font list, and a lot of fonts may make the list quite long, and hard to get through.

---

