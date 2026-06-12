---
title: "A true clean install?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by apauloisdead on 2007-10-17
I've been trying out different flavors of Ubuntu, but it's gotten to the point where when i throw in a livecd, they don't run correcly, i have to use safe graphics mode.

I'm probably wrong, but i thought that when i do a clean install nothing is carried over from the previous, but it seems like i mighta screwed some things up.

Is there anyway to set everything back to default? The first time i installed gutsy ubuntu everything worked fine.

---

### Post by bodhi.zazen on 2007-10-17
Well this seems to be two separate questions.

First, depends on what you mean by a "clean install". You should format the root partition / and that should be sufficient 99.9999 % of the time.

If you have a separate /home and there is a misconfigured . file, well unless you format /home it will not be "clean" (as the old config files will be carried forward) and this may be a potential source of problems.

If you want a clean install, use something like dban to clean the hard drive first.

Second, if you are having problems with a live CD that sounds like a hardware issue and unrelated to a "clean install". What videocard and what monitor ?

---

