---
title: "Is there some kind of a bootlog?"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by nixclusive on 2006-02-08
When I start my Ubuntu box, the very first thing I see is a lot of scrolling text with a lot of ok(s) in it. Somewhere in the middle is a red [FAIL] signal. But it scrolls up before I'm able to read it anyway. Is there some kind of a bootlog or something where all this is written?

---

### Post by steve.horsley on 2006-02-08
I think the command dmesg does that. For convenience, pipe it to a file or through less, like this:
dmesg > dmesg.txt
dmesg | less

---

### Post by TrendyDark on 2006-02-08
What version of Ubuntu are you using?

---

### Post by nixclusive on 2006-02-08
Ubuntu 5.04 Hoary Hedghog...hey how did you guys get the Ubuntu version you are using in...erm....the left panel of this forum where there's a little user info?

---

### Post by sprok8 on 2006-02-08
Near the top the screen there is a link "User CP". Go to this page, and from the links on the left side of the page select "Edit Profile".

The Ubuntu version question is near the end.

---

