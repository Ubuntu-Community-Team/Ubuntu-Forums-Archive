---
title: "[SOLVED] sim links disappearing"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by serfcx on 2007-11-15
I am trying to run tovid in Gutsy and have been using tovid/todisc for a long time in Feisty with no problem but now I cant burn the dvd I create because tovid is looking for /dev/dvdrw and my gutsy has a sim link /dev/dvdrw1.

I can create a sim link using sudo ln -s /dev/dvdrw /dev/hda as my dvd drive is listed as hda (weird?) but when I reboot the sim link is gone.
I have read that I need to set a script to run at boot time to create this sim link but at this point, being a noob, I am lost.

How do I create this start up script and where do I put it ?

---

### Post by Inxsible on 2007-11-15
I know this does not answer you question, but have you tried K3B or GnomeBaker or Brassero to burn CDs and DVDs ?

---

### Post by serfcx on 2007-11-15
> **Inxsible said:**
> I know this does not answer you question, but have you tried K3B or GnomeBaker or Brassero to burn CDs and DVDs ?

I use k3b for other burning activities, but you are right it doesn't answer my question:confused:

---

### Post by SpiritIsReality on 2007-11-15
[http://www.google.ca/search?hl=en&q=tovid+gutsy+%22startup+scripts%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=tovid+gutsy+%22startup+scripts%22&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=%22startup+scripts%22+gutsy+beginner&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=%22startup+scripts%22+gutsy+beginner&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=+gutsy+beginner+%22startup+scripts+%22+%28guides+OR+tutorials%29&as_qdr=m3&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=+gutsy+beginner+%22startup+scripts+%22+%28guides+OR+tutorials%29&as_qdr=m3&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=%28ubuntu+OR+debian%29+startup+scripts+%28tutorials+OR+guides%29&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=%28ubuntu+OR+debian%29+startup+scripts+%28tutorials+OR+guides%29&btnG=Google+Search&meta=)
[http://www.google.ca/search?as_q=+startup+scripts+tutorials+%7C+guides&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=ubuntu+debian+&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.ca/search?as_q=+startup+scripts+tutorials+%7C+guides&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=ubuntu+debian+&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)
[http://www.google.ca/search?hl=en&q=+startup+scripts+tutorials+%7C+guides+ubuntu+OR+debian+%22sim+links%22&as_qdr=y&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=+startup+scripts+tutorials+%7C+guides+ubuntu+OR+debian+%22sim+links%22&as_qdr=y&btnG=Search&meta=)
[http://en.wikipedia.org/wiki/Special:Search?search=sim+link&go=Go](http://en.wikipedia.org/wiki/Special:Search?search=sim+link&go=Go)
[http://www.google.ca/search?hl=en&as_qdr=m3&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=symlink&spell=1](http://www.google.ca/search?hl=en&as_qdr=m3&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=symlink&spell=1)
[http://en.wikipedia.org/wiki/Special:Search?search=simlink&go=Go](http://en.wikipedia.org/wiki/Special:Search?search=simlink&go=Go)
lord thunderin' I don't know. any ideas?

---

### Post by serfcx on 2007-11-15
I solved the problem by changing the shell used by Tovid and Todisc to burn discs - its called makedvd - by replacing /dev/dvdrw by /dev/dvdrw1

But why Oh WHY would Ubuntu want to create a link to hda (the dvd drive) and call it dvdrw1

Sounds really dumb to me

---

### Post by SpiritIsReality on 2007-11-17
sounds like a foreign language to me. haha! wya to go pard!!!

---

