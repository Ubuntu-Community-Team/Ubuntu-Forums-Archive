---
title: "Hotmail in thunderbird?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by FLCLFan on 2006-07-03
I just got Xubuntu and installed webmail/hotmail in thunderbird but unlike windows i didnt see a webmail option in the new accounts setup, and when i look at the webmail status i see "Error" for pop, smtp, and imap :? ?
Anyone know how to make hotmail work?

---

### Post by raffytaffy on 2006-07-03
Been trying to get hotmail to work with evolution...something called "getmail" was promising but a no go..i sure would like to see a way to make hotmail work with one of our email clients

---

### Post by RaoulDuke on 2006-07-03
Alright, I just got Thunderbird going and have all 3 of my webmail accounts (Hotmail, Yahoo, and another) running fine through it.

I just followed the directions from the Mozilla site. As far as your errors for POP, SMTP and IMAP just change them to anything over 1024 I believe. I just put a 1 or 11 infront of them and they worked fine. If you notice the little message that says the OS may be blocking any ports under 1024, thats what gave me the idea.

Post again if you have any other problems.

---

### Post by HereInOz on 2006-07-03
You need to install the WebMail extension from here:

[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

Just follow the instructions and it will all come together. 

Cheers,

Alan

---

### Post by FLCLFan on 2006-07-03
Ok, I figured the rest out and it all works fine! Thanks everyone :)

---

### Post by AmandaKerik on 2007-02-01
My biggest slip up is not clueing into the fact that I needed to set the ports in the add-on FIRST, then in the account settings AFTER. And they must be ABOVE 1024.

I'll write up a tutorial when I get some extra time on the computer :)

---

