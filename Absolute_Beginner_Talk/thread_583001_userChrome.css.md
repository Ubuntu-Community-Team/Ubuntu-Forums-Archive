---
title: "userChrome.css"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-10-20
So I moved userChrome.css to the correct folder but the text is not changing, I restarted firefox and all....:( any ideas?

---

### Post by kingofpain on 2007-10-20
Hi,

The userChrome.css file doesn't need to be moved. If you are in the correct folder, than you should see there two examples: userChrome-example.css and userContent-example.css.
All you need to do is to modify userChrome-example.css, and then to change it's name (removing "-example").
The path to the file should look something like that: "/home/<your username>/.mozilla/firefox/3xbkot7e.default/chrome"

For examples of what can you write into your userChrome.css, take a look at: [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)

Good luck!

---

### Post by GlennW on 2007-10-25
> **kingofpain said:**
> Hi,

The userChrome.css file doesn't need to be moved. If you are in the correct folder, than you should see there two examples: userChrome-example.css and userContent-example.css.
All you need to do is to modify userChrome-example.css, and then to change it's name (removing "-example").
The path to the file should look something like that: "/home/<your username>/.mozilla/firefox/3xbkot7e.default/chrome"

For examples of what can you write into your userChrome.css, take a look at: [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)

Good luck!

After installing 7.10, I wanted Firefox to look and perform like it did in xp, so I copied the userChrome.css file (in xp), copied it into the userChrome-example.css file, saved it, and renamed it. 

Nothing happened!! Admittedly, I'm quite the Linux/Ubuntu newb but I thought that I could get that right.

Suggestions would be welcome...

---

