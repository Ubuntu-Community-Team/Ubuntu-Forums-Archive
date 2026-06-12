---
title: "Xine: no mrl?"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-05
Hi,

Trying to simmer down my Ubuntu to teh essential apps. I see no need to have 10 apps for each function. So rather than have cd player for cd's and xine for dvd's and mplayer (or whatever) for something else still i want to just have one application for dvd, cd (music) 

I have taken the cd off as being the default and set it to xine, however, it is not playing my cd's. I get 'there is no mrl' 

Please do not let me go back to cd player with my tail between my legs  :---) 


cheers  :razz: 

--
sophtpaw

---

### Post by Vulpus on 2005-09-05
I also get the no mrl warning in Xine.  I don't even know what that means, except I cannot play DVDs.  

See my other post 'Why won't DVDs play'.

---

### Post by poofyhairguy on 2005-09-05
[QUOTE=sophtpaw]Hi,

Trying to simmer down my Ubuntu to teh essential apps. I see no need to have 10 apps for each function. So rather than have cd player for cd's and xine for dvd's and mplayer (or whatever) for something else still i want to just have one application for dvd, cd (music) 
[/QUOTE]

Only thing I have found that can do all of that well is VLC.

---

### Post by sophtpaw on 2005-09-05
[QUOTE=poofyhairguy]Only thing I have found that can do all of that well is VLC.[/QUOTE]

Thanks Poofy, (is that ok?)

Never heard of VLC before, but there it was in Synaptic. Tried opening it but got the mrl problem shoot up again. At least it told me what it 'mrl' means - media resource locator. Which is the problem i was having with xine and now with vlc. At least now i have a clue what the problem is, but don't know how to fix it. A matter of configuring the application. Interestingly enough my xine plays dvd but not music; for Vulpus it wasn't playing dvd's. 

Didn't have mrl with xine ever before and always played dvd and cd on it before. ???
Anyhow, if you or someone can help configure, if that is what it is, or sort out the mrl question, i would be mucho glad

--
sophtpaw

---

### Post by johanjpk on 2006-11-25
try this:

sudo ln -s /dev/scd0 /dev/dvd

---

