---
title: "Hwo to fax in Ubuntu Gusty (7.1)"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by taekr on 2007-12-25
Hi,

I'm using Ubuntu 7.10 on Inspiron 9300.  Ubuntu automatically installed Software modem driver but while I was looking for a way to fax, I found that Dell is supplying a driver 

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)

Someone says this driver is working with his computer (same as me) in Ubuntu 7.1. so installed it and diabled softmodem driver that ubuntu installed. 

Then, I installed 3 programs,  gfax, efax, kdeprintfax, in rotation..  

I just don't know how to use them... I doesn't seem to be working... 

Three questions I'd like to ask..

1. Should I use software Modem driver which Ubuntu automatically installed under restricted drivers or should I use the one from Dell?

2. How can I test that the modem is working?

3. How to fax??? how to use a fax program??

Thanks, million..

---

### Post by taekr on 2007-12-25
Anyone can help me with this???

---

### Post by SoDanishWasLike on 2008-01-17
I'm not sure about the drivers, but in System -> Administration -> Synaptic Package Manager, make sure you have both "efax" and "efax-gtk" installed.

Then, hit Alt + F2 and type in "efax-gtk" to run efax. From then on, it should be straightforward.

---

