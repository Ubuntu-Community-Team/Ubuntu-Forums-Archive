---
title: "ms word character set?"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by ldye on 2005-10-20
I am running edubuntu on a server for a web site at my high school.  I am a teacher and computer gal.
One problem though....
When a user creates an html file in ms word (save as html) and posts it to the site, some of the characters are not visible by users of the site.  Instead, these characters (usually, dashes and apostrophes, etc.) come over as question marks.  This happens regardless of the browser the viewer is using.   In other words, I have to leave eveything as a .doc (ms word) document on the site so tha when users click on it they will start their own version of word to view the document.  I would prefer that people posting to the site have the option to post the word doc as an html.
Is there some code that I must include so that the ms word character set is used?
Please help....or point me in the direction of someone who can!
Laura

---

### Post by Kyral on 2005-10-20
I think the msttcorefonts package MIGHT help here.

```
sudo apt-get install msttcorefonts
```

---

### Post by David Marrs on 2005-10-20
Msttcorefonts would certainly be worth a try, but it's quite possible that Word HTML files rely on other MS-specifics as well. Features like "save as HTML" tend to be best kept to intranet environments where everyone can be guaranteed to be running the same version of Windows, Office and Internet Explorer.

If the aim is to produce a web page then I think it would be easier and better practice (not to mention more educational) to write it as an HTML file in the first place. It's quite easy to do, especially if it's simple prose you're talking about. If you're intending to host these pages on the web itself then I'd definitely recommend it. As a web designer, I recoil at the thought of what Word-generated code actually looks like.

---

### Post by Kyral on 2005-10-20
Whoa...yah didn't see that the OP was making them in Word.

*shudders much at that thought*

Can I reccommend installing bluefish and then going here

[http://www.w3schools.com/html/default.asp](http://www.w3schools.com/html/default.asp)

HTML is easy to learn :D

---

