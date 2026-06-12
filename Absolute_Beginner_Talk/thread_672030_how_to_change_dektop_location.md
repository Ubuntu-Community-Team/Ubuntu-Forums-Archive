---
title: "how to change dektop location"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by hsigp on 2008-01-19
hi,

i am facing following problem
i renamed ~/Desktop to ~/desktop
restarted gnome, and since that no matter what i do on desktop is displayed content of ~/
not even changing back to original ~/Desktop name works,
gnome obviosuly detected directory doesnt exist and changed location,

so my question is what conf file and property should i edit to setup
desktop to ~/desktop ?

thanks a million,
tried several searches and no relevant result,
Mathew

---

### Post by jeffus_il on 2008-01-19
See  this:
[http://ubuntuforums.org/showthread.php?t=436718](http://ubuntuforums.org/showthread.php?t=436718)

---

### Post by kellemes on 2008-01-19
> **hsigp said:**
> hi,

i am facing following problem
i renamed ~/Desktop to ~/desktop
restarted gnome, and since that no matter what i do on desktop is displayed content of ~/
not even changing back to original ~/Desktop name works,
gnome obviosuly detected directory doesnt exist and changed location,

so my question is what conf file and property should i edit to setup
desktop to ~/desktop ?

thanks a million,
tried several searches and no relevant result,
Mathew


I can imagine you get a hole lot of trouble when doing this, packages depending or doing anything with "Desktop" will have issues with the renaming..
Why do you want to do the renaming if I may ask?

---

### Post by jeffus_il on 2008-01-19
> **kellemes said:**
> I can imagine you get a hole lot of trouble when doing this, packages depending or doing anything with "Desktop" will have issues with the renaming..
Why do you want to do the renaming if I may ask?

I asked myself the same question, I often deal with the dilemma whether to bring it up or not , I guess use have some inalienable right to do funny things, so I help them along on the self destructive journeys, in the hope that next time it will be better!

---

### Post by kellemes on 2008-01-19
> **jeffus_il said:**
> I asked myself the same question, I often deal with the dilemma whether to bring it up or not , I guess use have some inalienable right to do funny things, so I help them along on the self destructive journeys, in the hope that next time it will be better!

Nothing wrong with that.. ;-)

---

### Post by bethebunny on 2008-01-19
Personally I've always found it odd that while almost every file in linux, ever, used all lower case to make navigating via cli easier, Desktop was capitalized, I can definitely see wanting to make things homogeneous ;)

---

### Post by jeffus_il on 2008-01-19
> **bethebunny said:**
> Personally I've always found it odd that while almost every file in linux, ever, used all lower case to make navigating via cli easier, Desktop was capitalized, I can definitely see wanting to make things homogeneous ;)

Yes I also love to see my stuff neat and tidy, I just wonder if the price one pays, as an unsophisticated user is worth it. By the way, I was surprised to find out (if it is correct) that "Desktop"  is hard coded, definitely not a good practice, I looked for a setting in the gconf-editor and googled it but found nothing.

---

### Post by jeffus_il on 2008-01-19
Oops, Seems like there is a way:
[http://ubuntuforums.org/showthread.php?t=341607](http://ubuntuforums.org/showthread.php?t=341607)

---

