---
title: "Cant find the invert fire fox plug in"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2008-02-09
I've bee gone awhile, I had to brush up on my Windows for my new job. I went and reinstalled Ubuntu as my default OS, some things have changed in the past few months. Which is all nice. I like the point and click file sharing with samba. System -> Administration -> Shared Folders. I'd like to see more options in that GUI, but I'm certain that it is coming.

Anyhoo, the purpose to this thread; I can't seem to find my favourite Fire fox plug in. It is the one that inverts the entire web browser window so that the bright white web page with black text becomes a black web page with white text. Can anyone link me to it please?

---

### Post by kellemes on 2008-02-09
Don't know about an extension that does that..
But you can use one the many themes.
An example.. [PitchDark]("https://addons.mozilla.org/en-US/firefox/addon/1529")

---

### Post by Presto123 on 2008-02-09
There doesn't seem to be one anymore from what I can tell, but you can go here and try this [http://lifehacker.com/software/lifehacker-code/invert-web-page-colors-with-the-darken-bookmarklet-259456.php](http://lifehacker.com/software/lifehacker-code/invert-web-page-colors-with-the-darken-bookmarklet-259456.php)

*Edit* Just bookmark that Darken link they give and you can have control over what gets darkened.

---

### Post by badmedic on 2008-02-09
Also, if you are running Compiz Fusion (Desktop Effects) and have the CompizConfig Settings Manager, there is an accessibility option called Negative that allows you to invert your entire screen.

---

### Post by y-lee on 2008-02-09
Never heard of that particular add on, but [Accessibar]("https://addons.mozilla.org/en-US/firefox/addon/4242") would serve that purpose and can do a lot more. I'm still looking btw.

---

### Post by richardh9936 on 2008-02-17
You might mean "DARKEN", which is a block of javascript that lives in a bookmark.
javascript:(function(){var newSS, styles='* { background: black ! important; color: grey !important } :link, :link * { color: #0000EE !important } :visited, :visited * { color: #551A8B !important }'; if(document.createStyleSheet) { document.createStyleSheet(%22javascript:'%22+styles+%22'%22); } else { newSS=document.createElement('link'); newSS.rel='stylesheet'; newSS.href='data:text/css,'+escape(styles); document.getElementsByTagName(%22head%22)[0].appendChild(newSS); } })();

---

### Post by ant2ne on 2008-02-23
> **badmedic said:**
> Also, if you are running Compiz Fusion (Desktop Effects) and have the CompizConfig Settings Manager, there is an accessibility option called Negative that allows you to invert your entire screen.
:mrgreen: Perfect!

---

