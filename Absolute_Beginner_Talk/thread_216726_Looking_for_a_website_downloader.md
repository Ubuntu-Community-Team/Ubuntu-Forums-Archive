---
title: "Looking for a website downloader"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by arthurbarnhouse on 2006-07-15
On the Mac I used a program called webdumper ([http://www.versiontracker.com/dyn/moreinfo/macosx/12801](http://www.versiontracker.com/dyn/moreinfo/macosx/12801)) to download websites so that I could use them offline.  does anyone know of such a program for linux?

---

### Post by Anduu on 2006-07-15
httrack and webhttrack are available in the repos.You must have universe enabled.

I have not tried these so....don't yell at me if they are crap ;)

---

### Post by [S|G] on 2006-07-15
You can use wget to download entire sites for offline viewing, and it is a standard tool (meaning you won't have to install anything new). You would use the following command on a terminal:
```
wget -r http://website.com
```

---

### Post by vexorian on 2007-08-16
as always I am amazed at how complete the default linux setup is, wouldn't think wget would have a recursive option, I found this thread thanks to the automatic search that is done by this forum when you type the title.

---

### Post by bosshoof on 2007-12-24
but where can i find the downloaded website on my PC ?

---

### Post by adam.tropics on 2007-12-24
using the above command it would be in your home directory.

---

### Post by LaRoza on 2007-12-24
> **adam.tropics said:**
> using the above command it would be in your home directory.

In a directory named after the site's domain. If there is another domain involved, it will be in another directory.

There are more options for wget, and they allow for a deeper recursive depth, unlike the default 1.

---

### Post by adam.tropics on 2007-12-24
> **LaRoza said:**
> ...
There are more options for wget, and they allow for a deeper recursive depth, unlike the default 1.

You know, just reading through the man page....WOW! I knew wget to be useful, but I honestly didn't realise how complete a set of options it had. Incredibly useful. Note to self: read more man pages! Thank you.

---

### Post by Dr Small on 2007-12-24
```
cd ~
mkdir portableread
cd portableread
wget -r http://website.url
```

---

### Post by LaRoza on 2007-12-24
> **adam.tropics said:**
> You know, just reading through the man page....WOW! I knew wget to be useful, but I honestly didn't realise how complete a set of options it had. Incredibly useful. Note to self: read more man pages! Thank you.

No problem. I was surprised at wget when I first read it.

---

### Post by Dr Small on 2007-12-24
As soon as I run out of ideas, my first thought and natural instinct is to read the man pages. They are so helpful and show me lots of useful arguments to use, that I never knew of :D

---

### Post by LaRoza on 2007-12-24
> **Dr Small said:**
> AThey are so helpful and show me lots of useful arguments to use, that I never knew of :D

It sounds like some sort of social manipulation program. A program to get good arguments.

---

### Post by sujoy on 2007-12-26
I also didn't realise the full potential of wget till i saw the man pages...... its awesome

---

### Post by GSF1200S on 2007-12-26
Really cool... didnt know you could use wget as such...

That said, if simple is what youre after, couldnt you use the scrapbook extension for firefox? You just go to the page, and click on capture page. Additionally, you can select how many links deep from the main page you want scrapbook to capture. Then, it will be listed like bookmarks in the scrapbook menu, and you can access them offline. Heck, Ive even captured flash game pages and could play them offline..

[https://addons.mozilla.org/en-US/firefox/addon/427](https://addons.mozilla.org/en-US/firefox/addon/427)

---

