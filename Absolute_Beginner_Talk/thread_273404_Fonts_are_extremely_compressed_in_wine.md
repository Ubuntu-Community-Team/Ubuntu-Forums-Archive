---
title: "Fonts are extremely compressed in wine?"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by mon_m on 2006-10-08
So I've converted my friend from Windows to Ubuntu... but it was on the basis that I assured him he would have no problem running some of his Windows apps using Wine.

One of the main things he uses his computer for, is to play Magic Online.  I showed him how easy it was to install it, and everything was fine.  However, he started up the application and we quickly noticed that there was an issue with all the text throughout the program.  It looks like it's just all smashed together - making it entirely unlegible.

[screenshot]("http://www.enyo.info/images/Screenshot.png") (sorry about the .png)

I've already tried to consult the MTG:O community, but they're not very linux savvy.  Is it possibly a missing font file in the MTG directory? ](*,) 

Any help at all would be greatly appreciated.  Thanks guys.

---

### Post by kerry_s on 2006-10-08
Have you install the msttcorefonts? Those are the windows fonts.

---

### Post by mon_m on 2006-10-08
Yeah, that was actually one of the first things I tried :( 

But actually, through a lot of trial and error - I finally figured it out.  It was a registry problem (somehow the windows registry still finds a way to haunt me in linux).  Anyways, just for future reference, because, this actually fixed other font problems my friend was having in his other wine apps:

HKEY_CURRENT_USER >> Software >> Wine >> X11 Driver (you'll need to create this key)

then add these two strings:

ClientSideWithCore
ClientSideWithRender

then set both of their values to "N"


It's pretty terrible that you have to do that, is this something you can put in for a bug report on the wine site?

---

### Post by josys36 on 2006-10-18
This helped me quite a bit!

I now have an app that I can at least use in Wine, even though I don't have my favorite windows font in it.

Jason

---

