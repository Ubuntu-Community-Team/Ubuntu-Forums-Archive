---
title: "How to install Dokuwiki?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by xnooby on 2007-01-13
Is there an online guide for getting Dokuwiki to work on Ubuntu?  Googling seems to find websites that are using dokuwiki.  I have a G4 mac mini running PPC ubuntu 6 LTS, with Apache2 working.  I installed dokuwiki from synaptic - and I can see some of its files when I do a 'locate dokuwiki'.  I have configured dokuwiki on windoze boxes, so I know a little about it.  I think I need to make Apache aware of dokuwiki, and set up permissions.  The dokuwiki website has some linux install instructions, but I didnt want to mess up my system by manually mv'ing directories around when I didnt really know what I was doing.  ideally there is an online guide somewhere.

From what I've seen online, its supposed to "just work", but I am getting a 403 permission error.  I havent made a single change other than install from synaptic.  Does anyone have this working?

---

### Post by xnooby on 2007-01-14
Wow, my question is on page 9 already.

---

### Post by mjrclark on 2007-03-26
Similar happened to me.. I did a manual (sudo) chmod on the dokuwiki files (for me they were at /var/lib/dokuwiki if I remember correctly) to 775 (possibly 777, but I do not think so. This fixed the issue.

---

