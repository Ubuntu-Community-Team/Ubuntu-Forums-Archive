---
title: "Question about wget"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by linuxneeewb on 2008-04-19
I have a simple question about wget. Does using wget allow you to download files from the internet any faster than if you used an internet browser like Firefox to download? Or are there any other specific advantages that wget has? Any and all help is appreciated.

Thanks

:lolflag:

---

### Post by Xiong Chiamiov on 2008-04-19
Except for differences coming from, say, certain extensions in Firefox that slow it down, no, wget isn't any faster; it's still using the same connection, and the same transfer protocol.  The advantage comes from it's flexibility and ability to download large portions of websites with no input from you.  For example, I just used it in a script to download ~120 very large tiffs from a university website (so that I could convert them to png and upload them to Wikimedia Commons).

---

### Post by gsmanners on 2008-04-19
The main advantage to wget is that you can start it up in a console in the background and then ignore it for a while. It also has several optional features like setting the number of retries and downloading multiple files recursively.

---

