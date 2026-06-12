---
title: "[SOLVED] firefox extension error- invalid file hash - 261"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Straywolf on 2008-03-02
Hello all, love gutsy, but recently firefox has acted up. I can no longer install addons from mozilla. I get the "invalid file hash -261" error no matter what extension I try to install. I have googled the web and have found no significant fix for the problem. Some kind of "broken mirror issue. Anybody out there find a fix yet? I am using version 2.0.0.12 of Firefox and I never had this problem with Feisty. Help!

---

### Post by scorp123 on 2008-03-02
Clear your browser cache. Then try again. I just had this issue on a laptop a few days ago and completely clearing the cache helped. So in Firefox that would be:
**Edit > Preferences > Privacy > Section "Private Data" > Button "Clear now" ...**

... from there select what you need to have cleared. I'd clean the browser history, download history and the cache. Close your browser. And then try again to install the extension that gave you trouble.

---

### Post by Straywolf on 2008-03-02
Tried that, Still same error. Happens with every extension I try.

---

### Post by Oldsoldier2003 on 2008-03-02
> **Straywolf said:**
> Tried that, Still same error. Happens with every extension I try.

reinstall? sudo apt-get install --reinstall firefox

---

### Post by Straywolf on 2008-03-02
no luck with that either :(

---

### Post by elwood_j_blues on 2008-03-03
There's a bug in the Mozilla bugtracker for that: [https://bugzilla.mozilla.org/show_bug.cgi?id=420278](https://bugzilla.mozilla.org/show_bug.cgi?id=420278)

---

### Post by elwood_j_blues on 2008-03-03
The version 3.0.1 of the Video Downloadhelper extension is likely causing your problem, updating will fix it. See: [https://bugzilla.mozilla.org/show_bug.cgi?id=420278#c17](https://bugzilla.mozilla.org/show_bug.cgi?id=420278#c17) .

---

### Post by Straywolf on 2008-03-06
tried everything to no avail, so I backed up everything and reinstalled gutsy, even formatting my home folder. The problem is solved. Thanks to all for the help and I will keep a better eye on things I install and the problems that arise afterward. I suspect it was a bad extension install that caused the problem.

---

