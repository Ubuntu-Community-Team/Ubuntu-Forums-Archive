---
title: "Solved: &quot;libgtk-x11-2.0.so.0: undefined symbol&quot;!"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by klausner on 2008-01-06
About a week ago,  I thoroughly [shot myself in the foot]("http://ubuntuforums.org/showthread.php?t=650185") while trying to install the latest version of synce. I found that I could no longer get compiz, nautilus, firefox, or many other applications to start. The common error seemed to involve:

> 
libgtk-x11-2.0.so.0: undefined symbol

Doing multiple Google searches, and posting a request for help here turned up many similar requests for assistance, but little in the way of solutions. I tried deleting the packages I thought I added, and I tried re-installing Gtk and anything else I could think of, but with no effect. ](*,)

Finally, I found the answer! [IMG]http://www.kellyforums.com/forum/images/kc_forums/smilies/hurray.gif[/IMG]Seems that my efforts to install synce had loaded a second copy of libgtk into /usr/local/lib. Every time Gtk tried to start, it would preferentially load this newer, incompatible copy, and barf. BUT... the error messages implied that the problem was with the original version in /usr/lib.

The solution is to delete the version in /usr/local/lib]. No amount of reinstalling packages will have any effect as long as the incompatible version located there is being preferentially referenced. 

Hopefully, this will save some others grief, and maybe even get some more useful error messages in future versions!

---

### Post by Toxicity999 on 2008-01-06
Also, the undefined symbol thing doesn't mean anything. It just means that it crashed and wasn't able to pull information about the crash. Searching for that is sort of like Figuring out how a plane crashed by saying "A plane crashed!". Doesn't go very far. Good work on solving your issue though. :)

---

