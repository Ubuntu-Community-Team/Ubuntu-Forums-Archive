---
title: "cURL?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Hranj on 2006-12-03
i was on one of the forums i frequent and there was a link to page with a bunch of pics on it. one person posted that if i put curl -o or something like that into the terminal it would download all of the pictures on that page. i tried it and it didnt work. maybe i did it wrong. can someone enlighten me? thanks.

---

### Post by nixclusive on 2006-12-03
I guess you'd like to download all the pictures on a specific page. The easiest way to do so would be to load the page completely in a Web Browser and then save the page with images as well.

---

### Post by TerryHowe on 2006-12-03
Curl would do that if it was installed, but it probably isn't.  I don't know if you can download curl through Synaptic, you might have to download yourself and build it.

But, don't bother, use wget instead.  You should have that loaded already and it does pretty much the same thing.

 wget [http://www.example.com/pix.jpg](http://www.example.com/pix.jpg)

---

### Post by Forceflow on 2006-12-03
> **TerryHowe said:**
> Curl would do that if it was installed, but it probably isn't.  I don't know if you can download curl through Synaptic, you might have to download yourself and build it.

But, don't bother, use wget instead.  You should have that loaded already and it does pretty much the same thing.

 wget [http://www.example.com/pix.jpg](http://www.example.com/pix.jpg)

He wants to grab all the images from a page, not just one image. Don't know the syntax, just try wget --help.

---

