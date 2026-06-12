---
title: "A few basic questions."
date: 2008-10-16
forum: Apple Hardware Users
---

### Post by nageekdoog on 2008-10-16
Ladies and gentlemen,

I am considering dual booting my MacBook with Ubuntu Linux. I've worked with Linux before on a PPC Mac so I'm vaguely familiar with installations and everything like that. 

I have a few concerns that I want to clarify before I section off my hard drive and go through the whole process of installing Linux. 

1) Will all my hardware work? - The airport card, namely. 
2) Will I be able to read from my OSX partition from my Linux partition to access music and pictures etc?
3) Is there any advice you may have for a relatively novice Linux user?

Thanks so much!
KG

---

### Post by schauerlich on 2008-10-16
1) [This](https://help.ubuntu.com/community/MacBook) should answer most of your questions about hardware
2) Linux can read hfs+, I'm not sure about writing though.
3) Don't be afraid of the terminal. Learn as you go. A lot of the terminal knowledge you gain from Linux will apply to OS X, although there are some differences. But mostly, don't expect Linux to work like any other OS you've used. Every time you try something new you must learn, and Linux is no different.

---

### Post by cyberdork33 on 2008-10-16
please see the "before you post" link in my signature to find the proper wiki page for your mac.

You can read and write to HFS+ if you disable journalling. (You can read-only without disabling journaling). Be aware that there are file permissions issues you will neeed to work around (the osx users' files will not be accessible to your ubuntu user).

---

