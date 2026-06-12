---
title: "After Xubuntu 18.04.1 LTS install my keyboard would not work - fixed"
date: 2018-12-10
forum: Apple Hardware Users
---

### Post by gerald-mcinally on 2018-12-10
For the last two days I have been repeatedly installing Xubuntu 18.04.1 LTS on a Macbook 5.2 (no idea if thats relevant).
My keyboard layout is Norwegian (no idea if thats relevant either)
Anyway the install process went fine with no issues but each time that I booted into the installed system the keyboard didnt work. 

I read a suggestion about trying the Onboard onscreen keyboard and that did work although the suggested sudo command to fix the issue didnt work. Then I noticed that after pressing the '123' button in Onboard, the NumLock key was toggled on (RED), so I toggled it off and hey presto my Macbook keyboard worked just fine! 

So something in the 18.04 latest install is switching on Numlock by default which is screwing up some keyboards at least on some machines and some layouts after install - this may just affect Xubuntu but maybe not. As I said this can be fixed by using the onscreen keyboard and toggling numlock off but that a bit lame.

Note for the cure to be persistent in Xubuntu you need to tick off the keyboard setting to remember that last numlock setting, otherwise it defaults to on again.

Hope this helps - please fix

---

### Post by howefield on 2018-12-10
Thread moved to the "*Apple Hardware Users*" forum.

---

