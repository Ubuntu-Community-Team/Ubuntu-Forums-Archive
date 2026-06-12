---
title: "[SOLVED] Rhythmbox DAAP iTunes"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2008-01-29
Rhythmbox and iTunes sharing does not work for me. I've activated it and a list of libraries show but when I try to load their songs the list wont open.

It says in the bottom left "retrieving songs from music share" and nothing else.

Other people on windows machines with iTunes can play my music though.

---

### Post by Prefader on 2008-01-29
This is a known issue - some time ago, an update to iTunes broke network sharing between iTunes and non-iTunes apps.  For the sake of backwards compatibility, iTunes is still able to see shares from older versions, which is why iTunes can see your Rhythmbox library.

So, nothing is configured wrong on your end, it's just more iTunes "goodness".

[http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol#DAAP_authentication](http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol#DAAP_authentication)

---

### Post by farueulogy on 2008-01-30
Can I help fix this problem? Is there anyone working on it?

---

### Post by jcbwalsh on 2008-02-17
After some trial and error I've found a decent work around. I shared the iTunes Music folder and then set the Library Location in Rhythnbox to the share. 

In my case I'm running iTunes on a Mac but the trick should work in Windows just as well. One added note for doing this on a Mac. I used a Program called SharePoints to set up the share. The first time I tried this my iTunes Music folder was in the default location in my Users folder. I could not access that folder from Ubuntu no matter what I tried. I had to more my iTunes Music folder to an external drive this weekend. I updated the share location and now I can access it both in Rhythmbox and other ways. I'm guessing there some extra security on the User folder that prevented it before.

---

