---
title: "Strange update issue/Question"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-12-30
Hey all,

I installed opera again as I wanted it as an alternate to Firefox if Firefox was misbehaving.  I noticed Opera is a version behind (9.24) So I did a Sudo apt-get update (thinking that it would catch the update to Opera and no luck.  Then I tried a Sudo apt-get upgrade with the same results..

My question is why wouldnt it catch the updates to Opera through those 2 methods, its part of the programs installed (using refresh in synmpatic just showed 9.24)  Am i missing something here?

---

### Post by JoshuaRL on 2007-12-30
Are all your software repository sources enabled?  That might be the problem.

---

### Post by p_quarles on 2007-12-30
The partner repository probably doesn't keep up-to-date with every release. Opera's web site has .deb files for both current versions (9.25, and 9.50Beta).

---

### Post by RomeReactor on 2007-12-30
Hi. If you installed Opera from Synaptic, by having the "Partner" repository enabled, then that would explain why your version of Opera is slightly behind. As I understand it, packages from the repositories are often a little behind due to the maintainers ironing out quirks certain programs might have with Ubuntu, making sure those programs are as compatible as possible.

As a side note, be aware that Opera 9.25 has problems with Flash; Opera 9.50 beta has corrected this problem. You might want to keep your 9.24 for the moment, or if you absolutely must upgrade, try the 9.50, which is very stable.

---

