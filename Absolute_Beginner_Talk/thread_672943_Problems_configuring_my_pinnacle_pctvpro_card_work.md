---
title: "Problems configuring my pinnacle pctv/pro card work"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by AdiLit on 2008-01-20
Hello to everyone I am a total beginner in linux, and I am in desperate need of assistance in configuring my tv-tuner card :). I have read a couple of posts related to the subject, I have created the famous modeprobe.conf file placed it under /etc folder, but sill I can't make tv time work. Here is my modeprobe.conf:
alias char-major-81 videodev
alias char-major-81-0 bttv
options bttv card=39 tuner=33 autoload=1 pll=1 radio=1 bttv_verbose=0 bttv_gpio=0 bttv_debug=0  
options tuner pal=b 
 
If I run the command lspci I can see that the system sees my tv-tuner card:
01:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

I would appreciate any help. Thanks

---

### Post by arkoudi on 2008-01-20
I don't want to dissapoint you but it won't work..I 'm looking for a solution to this problem 3 years now. But nothing...only TV works with this card. I managed once to make radio Work with DMCradio on SUSE 7.0 but it had an old version of the bttv drivers. I came up to the conclusion that the bttv for the radio does not work with this card. Tried dapper, edgy and now gutsy..no luck :)

P.S I posted at 2006 a post like you but noone answered :)
Google helped me a lot.

---

### Post by AdiLit on 2008-01-21
Thanks Arkoudi for the head's up, I still hope I'll find some solution to the problem. I have found some post's,but I can't recall where, in which they were talking about this card with specific instructions about it and how one should  set up the modeprobe, however I've  tried that with no result. I may have to review that. It  seems to me that some people actually managed to get this card functioning. I will do some more research, maybe someone will have an idea.

---

