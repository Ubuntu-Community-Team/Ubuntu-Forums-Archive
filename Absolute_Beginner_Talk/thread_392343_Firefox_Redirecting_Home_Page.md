---
title: "Firefox Redirecting Home Page"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by marianoi on 2007-03-24
Hello Everyone,

After letting my 3 years old kid playing with Ubuntu for about 2 hs yesterday, I noticed that Firefox does not open the Home page (even though it is set to open directly to the home page) and is trying to open "http://u/", which shows, of course, a 404 error.

I completely removed Firefox and re-installed it but again the same problem....I even deleted my profile and no luck...

Would anyone have an idea why I am getting this problem (besides not letting a 3 years old kid playing with the PC )?

Thanks!

Marianoi

---

### Post by halitech on 2007-03-24
why not just go to Edit -> Preferences and reset the home page?

---

### Post by marianoi on 2007-03-24
Hello,

Thanks. 

That's the first thing I did. The Home Page is the Ubuntu's Default...And Firefox is set to go there directly...but it does not..it tries to go to "http://u/"...

Any idea?

Cheers

Mariano

---

### Post by bulldog on 2007-03-24
Do you use an separate icon to start Firefox?

Throw it away and create a new,or try to start Firefox from the menu option.

To start Firefox hit CTRL-F2 and type firefox %u to see what happens.

---

### Post by halitech on 2007-03-24
sorry, missed that you said you had reinstalled. can you get to any other page when you get the 404 error or are you stuck there.

---

### Post by marianoi on 2007-03-24
Hello,

Thanks guys...

1) If I run firefox from the terminal it also goes to the http:\\u\

2) Except that, everything works fine. If I hit "home" it goes to the Ubuntu's default home page....

I deleted all the cookies from the "clear private data" and no luck either...

Ideas????

Thanks a lot!

Mariano

---

### Post by halitech on 2007-03-24
this may not have anything to do with it but in the prefs, what option is selected for when firefox starts?

---

### Post by ljpm on 2007-03-24
Check the properties of your shortcut.
 
Mine has 
```
firefox %u
```
for the command.

I remember reading on this board a couple of months ago that a similar problem had something to do with the %u.

Hopefully this is enough info to lead you in the right direction.

---

### Post by chamberlain2006 on 2007-03-24
Perhaps you're missing the % before the u, ie "firefox u" instead of "firefox **%**u"  This would cause firefox to try to load "u" or "http://u/".  Make sure your launcher has the % sign, and this could fix your problem.

---

### Post by marianoi on 2007-03-24
Hello Guys,

Thanks for your posts. In fact the %u was missing...now Firefox is back to normal...

Cheers

Mariano

---

