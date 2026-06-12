---
title: "Find and replace tool?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by TooRight on 2007-01-11
I am almost certain that on my old installation I had a find and replace tool... that is, a program that I could set to search all the files in a directory for a certain word or line of text, have it find it and replace it in all instances with what I told it to. I'm doing a bunch of work on my sites and need desperately to get this program again... does anyone have an idea what it's called?

---

### Post by po0f on 2007-01-11
TooRight,

sed?

---

### Post by TooRight on 2007-01-11
The one I  am thinking of had a GUI, but thanks for the reply!! I was worried this post was going to get buried and I am sooo stressed about these changes that need to be made, lol

---

### Post by po0f on 2007-01-11
TooRight,

Depending on how much you need changed and the requirements, I can help you write out a couple sed scripts.  Post a sample of what you need done.

---

### Post by jagwah on 2007-01-11
.

---

### Post by TooRight on 2007-01-11
Really Po0f?? Wowww!! Thank you!!

What I need it to do is search all the files in a directory ex /home/username/searchthis/

and i need it to find a certain line in each file and change that line, it's actually part of a path for a script, so ex have it change
```
include("/home1a/myserverusername/mysite1/
``` 

to ```
include("/home2b/myserverusername/mysite2/
```


It seems simple enough, but this is an olddddddd php script that I used and has no templating system, therefore this line appears 1-5 times on almost everyyyy php page!! What a headache!!

If you could show me how do that using sed I'd be soooooooooo appreciative!! (gee, that sounded bad :oops: , but ya know what I mean)


krename?? Will check that out, thanks!!!

---

### Post by IYY on 2007-01-11
Now, make sure to backup your directory before you attempt this:

```
 sed -i 's/include(\"\/home1a\/myserverusername\/mysite1\//include("\/home2b\/myserverusername\/mysite2\//g' /home/username/searchthis/*
```

---

### Post by TooRight on 2007-01-11
Cool, will try it and let ya know!! Thank youuuuuuuuu!! :D

---

### Post by TooRight on 2007-01-11
IYY, you are a geniusssssssss !! It worked, yayyyyyyyyyyyy!! :KS 

Thank you thank you thank you thank you!!! :D :D :D

---

### Post by tweedledee on 2007-01-13
> **TooRight said:**
> IYY, you are a geniusssssssss !! It worked, yayyyyyyyyyyyy!! :KS 

Thank you thank you thank you thank you!!! :D :D :D

Not to take away from the above approach, but regexxer is in the repos (even via add/remove) and is a GUI to do the same.  You can probably find others by searching the repositories.

---

