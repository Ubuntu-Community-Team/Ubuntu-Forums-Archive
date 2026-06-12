---
title: "switching function of Ctrl and Command keys?"
date: 2008-06-01
forum: Apple Hardware Users
---

### Post by Zeep on 2008-06-01
So I just started using ubuntu after using OSX for quite a while and I was wondering if it was possible to switch the function of the Control key and the Command key, since most of their uses are opposite in the two OS's. If there's no simple way to do it that's fine, I was just wondering, since it would make it a bit easier on me.

---

### Post by hpp3 on 2008-06-03
To make a short answer, no there is no easy way.

However, if you want to take a crack at it, you can modify your xmodmap file. 
Read here:
[http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys)

Just for the record, I ran xev on a PC and on a Mac G4 with Gutsy installed.
The keycodes for alt (option on the mac) and ctrl are the same for both, and the keycodes for the Mac command keys are 115 and 116 for left and right command keys, respectively.

---

