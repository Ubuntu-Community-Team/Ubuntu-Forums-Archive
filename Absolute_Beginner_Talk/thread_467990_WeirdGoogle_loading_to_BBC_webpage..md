---
title: "Weird:Google loading to BBC webpage."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by OmnificienT on 2007-06-08
This is really weird, I just opened my browser (firefox) and it opened the BBC news page, instead of google, as displayed in the place where the URL goes...

---

### Post by indytim on 2007-06-08
It's hard to read your screenshot, but check the url listed.  From what I can cypher here, doesn't look like the google url (again difficulty with the resolution of your screenshot).

IndyTim

---

### Post by rich.bradshaw on 2007-06-08
It is right, click the image and it gets bigger.

What happens if you

dig [www.google.com](www.google.com)

 in a terminal?

What happens when

dig [www.bbc.co.uk](www.bbc.co.uk)

Have you tried restarting etc?

---

### Post by Inxsible on 2007-06-08
That is weird !
I just tried to go to google.com and it worked fine. Does it happen everytime you open up a browser? Try restarting the browser.
 
IndyTim, you can click on the image to expand it to normal size. A browser normally reduces the size of the picture

---

### Post by Inxsible on 2007-06-08
Rich got to you first 
 
Ah Crap ! ;)

---

### Post by viciouslime on 2007-06-08
> **Inxsible said:**
> That is weird !
I just tried to go to google.com and it worked fine. Does it happen everytime you open up a browser? Try restarting the browser.
 
IndyTim, you can click on the image to expand it to normal size. A browser normally reduces the size of the picture

Same here and I'm in the UK. Going to google.com just redirects me to google.co.uk as it should...

---

### Post by HereInOz on 2007-06-08
It is either a problem with the DNS server of your ISP, or you have an entry in your hosts file which is directing traffic for google.com to the BBC site.

Try entering this into your browser address bar:

[http://64.233.169.99/](http://64.233.169.99/)

If that doesn't take you to Google, then I am completely wrong.  If it does, then I am probably right.

---

### Post by OmnificienT on 2007-06-08
Well, I think you were right, since that also happened to me yesterday with the ubuntu forums. Another thing is that there was a rss feed to the bbc site, on the bar above the webpage display window. Maybe firefox muddled it up. Anyway I removed the rss feed and google now loads normally, although in still shows a tiny BBC icon in the URL bar before the url.

---

