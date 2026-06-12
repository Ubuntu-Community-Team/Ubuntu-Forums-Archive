---
title: "[SOLVED] Internet Radio help"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by natman on 2007-12-18
Hi, i know there are loads of posts on this but not that i have seen that actually works, i have 64 bit ubuntu and want to play radio from this site
[http://www.rte.ie/radio/index.html](http://www.rte.ie/radio/index.html)

Click Listen live ( right hand column top. I have VLC, xmmx, and loads more nothing seems to work as well as in windows.

---

### Post by p_quarles on 2007-12-18
Looks like that site uses Realplayer for streaming media. For some reason, it's not currently available in Gutsy's commercial repository, but you can get it following the method described in this link:
[http://ubuntuforums.org/showpost.php?p=3652221&postcount=33](http://ubuntuforums.org/showpost.php?p=3652221&postcount=33)

---

### Post by natman on 2007-12-18
Hi that actually worked out perfect on my old 32bit Desktop, but still no help on my 64bt laptop, just complains about the wrong arch. 
I did some google and see stuff about a Helix player but its not in adept/synaptic, can someone help?
Thanks

---

### Post by p_quarles on 2007-12-18
Well, commercial software always take a lot longer to get distributed for 64-bit OSes. At this point, that's the only disadvantage to using 64-bit Ubuntu. 

There are some tutorials for installing 32-bit apps on the 64-bit OS, though, in the x86-64 Users forum.

---

### Post by learning curve on 2007-12-18
Go into the synaptic package manager and click on the search tab and type in mplayer.  See if that will stream your station.:guitar:

---

### Post by learning curve on 2007-12-18
Sorry, I tried your link and it looks like realplayer for linux is the best solution.

---

### Post by sgarrand on 2007-12-18
> **natman said:**
> Hi that actually worked out perfect on my old 32bit Desktop, but still no help on my 64bt laptop, just complains about the wrong arch. 
I did some google and see stuff about a Helix player but its not in adept/synaptic, can someone help?
Thanks

Try the linked thread's suggestions but use:  sudo dpkg -i --force-architecture realplayer_10.0.9-0.1_i386.deb

This is how I get 32 bit software installed on my 64 bit system.

Scott

---

### Post by p_quarles on 2007-12-18
> **sgarrand said:**
> Try the linked thread's suggestions but use:  sudo dpkg -i --force-architecture realplayer_10.0.9-0.1_i386.deb

This is how I get 32 bit software installed on my 64 bit system.

Scott
Yep, that's the way to do it. Anyone who wants to try this, though, should be advised that the dpkg man page considers the "--force-architecture" option to be a potentially dangerous one. 

My understanding is that it's much less dangerous with non-essential packages (like this one), but something to keep in mind. Run the following for more info:
```
dpkg --force-help
```

---

### Post by sgarrand on 2007-12-18
Thanks for that info. I was taught this but without the disclaimer. I've never used it for essential packages. I use Synaptic for those.

Scott

---

