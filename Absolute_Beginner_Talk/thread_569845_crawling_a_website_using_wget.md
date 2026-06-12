---
title: "crawling a website using wget"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by l337a on 2007-10-07
Just wondering how I could crawl and download EVERYTHING from the site using wget. I know it's possible, and you know that I know that you know. So spill the beans?

---

### Post by Vixis on 2007-10-07
Try:
```
wget -r -l0 -np -k http://www.yoursite.com/
```

---

### Post by helphope on 2007-10-12
I've be trying hard to use wget to download links also pointing outside the site, but I can't get the right flags.

So please, > I know it's possible, and you know that I know that you know. So spill the beans?

Thanks

---

### Post by l337a on 2007-11-26
This gets all the web page data, but it doesn't get files like .zip and .avi etc. That's the stuff I want, and apparently wget doesn't want to give it to me. :lolflag:

---

