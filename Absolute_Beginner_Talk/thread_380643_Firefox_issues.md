---
title: "Firefox issues"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Drew555 on 2007-03-09
Firefox keeps randomly shutting down and I don't know why.

I can surf for ages, then it'll just close the window. Then it'll maybe do it again shortly afterwards, be fine for a while then 3 more times in succession.

Any ideas?

And how can I get rid of that download box that pops up in front of the back button everytime I save a picture?

Oh yeah, and how do I change the home page?

Sorry bout this, but I'm new to Linux, and loving it but these little things are doing my head in and I'm just getting familiar.

---

### Post by taurus on 2007-03-09
What version of firefox are you using?

---

### Post by invalid on 2007-03-09
Try opening firefox from a terminal. When it crashes, it may provide some helpful information for debugging.

---

### Post by Drew555 on 2007-03-09
It's version 1.5.0.10 and I wouldn't know how to open firefox from a terminal.

I know I'm terminally aggravated...

---

### Post by taurus on 2007-03-09
Applications -> Accessories -> Terminal
```
firefox
```

---

### Post by Drew555 on 2007-03-09
LOL, bloody n00bs eh....

---

### Post by zubrug on 2007-03-09
> **Drew555 said:**
> LOL, bloody n00bs eh....

lol

---

### Post by Drew555 on 2007-03-09
Right, here's what we got:

drew@mission-control:~$ firefox
Segmentation fault
drew@mission-control:~$ firefox
Illegal instruction


Any wiser?

And that download box is still doing ma heed in...

---

### Post by invalid on 2007-03-09
> **Drew555 said:**
> Right, here's what we got:

drew@mission-control:~$ firefox
Segmentation fault
drew@mission-control:~$ firefox
Illegal instruction


Any wiser?

And that download box is still doing ma heed in...

Are you doing anything particular each time they occur? Perhaps the same thing each time?

---

### Post by Drew555 on 2007-03-09
Not that I've noticed.

---

### Post by invalid on 2007-03-09
As far as the donloads box, you can disable this in your preferences. On the Main preferences there is an option to Show the Downloads window when downloading a file, and Close it when all downloads are finished.

---

### Post by Drew555 on 2007-03-10
Sorted the downloads box, and re-set my home page, thanks for pointing me in the direction of the 'preferences' menu, Invalid. I hadn't found it before.....

Now to sort out the crashing...

Did it again just now, as I was typing [www.google.com](www.google.com) into the home page box, I got as far as [www.google.c](www.google.c) and it died, reporting a Segmentation fault again.

---

### Post by DJ_Peng on 2007-03-10
Try upgrading to Firefox 2. While many peope still use Firefox 1.5.0.10, you may have a combination of things that are causing a bug that may be fixed in Firefox 2.

---

### Post by viergeame on 2007-03-10
> **DJ_Peng said:**
> Try upgrading to Firefox 2. While many peope still use Firefox 1.5.0.10, you may have a combination of things that are causing a bug that may be fixed in Firefox 2.

I use Firefox 2 and I still have this happen often.  I haven't tried running it from the terminal yet though, so I can't really say if I have the exact same error log.

---

### Post by DJ_Peng on 2007-03-10
I know there were some regressions in Firefox 2.0.0.2, but they had a commusinty test day today for Fx 2.0.0.3. It may not help you now, but there's a new version coming out very soon that will fix some problems that crept up in 2.0.0.2. That said, I had no problems with 2.0.0.2 accessing Gmail, but you may have a combination of things causing a problem. You may also want to  look at any extensions you have added or updated recently, as I've seen extension updates break things.

---

