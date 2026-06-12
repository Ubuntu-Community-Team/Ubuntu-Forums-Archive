---
title: "Screenshot app"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by tqprvn on 2008-03-10
Hi all

Aware of the screengrab option in accessories, but curious if there is something more powerful a la Webshot on Windows.

More specifically, we regularly take screenshots of web pages which scroll down.  Webshot captures the page in its entirety and saves it to a jpg.

Anything like that under ubuntu?

TIA

Matt

---

### Post by aashay on 2008-03-10
Does this help?
[https://addons.mozilla.org/en-US/firefox/addon/5648](https://addons.mozilla.org/en-US/firefox/addon/5648)

---

### Post by sayakb on 2008-03-10
If you use compiz, you might have the Screenshot plugin for Compiz. It saves the files as png when you press Print Screen. Also, it captures, the Window snap on pressing Alt+Print. Plus an additional screenshot plugin under ccsm when checked can take screenshots of selective areas when selected with the Super key pressed..

---

### Post by bcl1713 on 2008-03-10
> **aashay said:**
> Does this help?
[https://addons.mozilla.org/en-US/firefox/addon/5648](https://addons.mozilla.org/en-US/firefox/addon/5648)

no linux version... just windows.  installs okay but doesn't run right.  :(

---

### Post by tqprvn on 2008-03-10
> **LinuxIsInnovation said:**
> If you use compiz, you might have the Screenshot plugin for Compiz. It saves the files as png when you press Print Screen. Also, it captures, the Window snap on pressing Alt+Print. Plus an additional screenshot plugin under ccsm when checked can take screenshots of selective areas when selected with the Super key pressed..
ya, but that wont capture a whole web page though will it?  Only the area visible in the window?

---

### Post by sayakb on 2008-03-10
> **tqprvn said:**
> ya, but that wont capture a whole web page though will it?  Only the area visible in the window?

Yes it won't.. Why don't you just Save the page instead? (File->Save Page As..)
Though I'm sure you know that you won't get this one in jpg format.

---

### Post by tqprvn on 2008-03-10
> **LinuxIsInnovation said:**
> Yes it won't.. Why don't you just Save the page instead? (File->Save Page As..)
Though I'm sure you know that you won't get this one in jpg format.
I run a PR company in Vietnam.

Basically because most of the time when we do this, we are capturing a news story on a website, inserting the jpg into a word processor, and then translating the news into English for our clients.

There are quite a few Windows apps to the same end (we use Webshot now), so looking for a Linux equiv

---

### Post by bcl1713 on 2008-03-10
you could print to file which creates a pdf file then use imagemagick to:
```
convert image.pdf image.jpg
```

---

### Post by sailor2001 on 2008-03-10
or use istanbul for a short movie.   ksnapshot for screen

---

### Post by tqprvn on 2008-03-24
> **bcl1713 said:**
> you could print to file which creates a pdf file then use imagemagick to:
```
convert image.pdf image.jpg
```

sorry, still havent got this licked.

If I print webpages out to a PDF file, they come out as multiple pages (this thread for example comes to a 4 page pdf)...meaning that the conversion will likely be a mess.

Is there any way to get cups/pdf to print webpages out as a single long scrolling page rather than automatically make multipage documents?

---

### Post by Lord Illidan on 2008-03-24
This should work under Linux : [https://addons.mozilla.org/en-US/firefox/addon/1146](https://addons.mozilla.org/en-US/firefox/addon/1146)

---

### Post by tqprvn on 2008-03-24
you are my god!

---

