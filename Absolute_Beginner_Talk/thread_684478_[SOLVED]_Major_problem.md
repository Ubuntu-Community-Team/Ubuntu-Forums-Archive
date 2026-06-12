---
title: "[SOLVED] Major problem"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by MarkX on 2008-02-01
Google refuses to load in Firefox, nor will hotmail get past the login and the login page has logos missing.
I checked the Firefox error console and these  warnings/errors show:

Unknown property 'filter' declaration dropped

Unknown property 'zoom' declaration dropped

Warning: Unknown property 'text-index'.  Declaration dropped.

Error: [Exception... "'Component does not have requested interface' when calling method: [nsIInterfaceRequestor::getInterface]"  nsresult: "0x80004002 (NS_NOINTERFACE)"  location: "<unknown>"  data: no]

Error: uncaught exception: [Exception... "Component returned failure code: 0x804b000a [nsPIProtocolProxyService.configureFromPAC]"  nsresult: "0x804b000a (<unknown>)"  location: "JS frame :: chrome://browser/content/preferences/connection.js :: anonymous :: line 121"  data: no]

Error: $ is not defined
Source File: [http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)
Line: 2777


Error: $("q").addEvent is not a function
Source File: [http://ubuntuforums.org/newthread.php?do=newthread&f=73](http://ubuntuforums.org/newthread.php?do=newthread&f=73)
Line: 1119


Heeeelp! It all worked fine when I used it at my place, but it won't at the friend's house.

---

### Post by billgoldberg on 2008-02-01
Well.

The easiest thing to do might be reinstalling firefox. Or use another browser like epiphany.

Some add-ons might give problems.

Sorry I can't help you any more. It's been ages since I used firefox.

Anyway, it's a nice threat bump.

---

### Post by jan quark on 2008-02-01
I love this typo
[http://en.wikipedia.org/wiki/Threat](http://en.wikipedia.org/wiki/Threat)

you can try other versions of web browser 

opera

the mentioned epiphany

or kazekahase

---

### Post by Seisen on 2008-02-01
Run firefox in safe-mode from the terminal and see if you still have the same problems.
```
firefox -safe-mode
```

---

### Post by MarkX on 2008-02-01
> **Seisen said:**
> Run firefox in safe-mode from the terminal and see if you still have the same problems.
```
firefox -safe-mode
```

No difference. Heeeelp!
Without google and Firefox Ubuntu is utterly useless  to my friends.

---

### Post by jan quark on 2008-02-01
why does it have to be firefox at all costs?
have you tried the other web browser?
do you get the same errors?

---

### Post by MarkX on 2008-02-01
> **jan quark said:**
> why does it have to be firefox at all costs?

Have you tried the other web browser?
do you get the same errors?

Because they are reluctant computer users and only know firefox.
I haven't tried another one, Firefox should work.

---

### Post by jan quark on 2008-02-01
It would really help to see if only FF has problems or any other browser too.

---

### Post by MarkX on 2008-02-01
> **jan quark said:**
> It would really help to see if only FF has problems or any other browser too.

Epiphany won't connect to google either but other sites work.

---

### Post by jan quark on 2008-02-01
epiphany is like firefox based on mozilla, so its almost the same :)

but it is weird that only google does not load properly 
someone an idea?

---

### Post by Seisen on 2008-02-01
Just out of curiosity are you guys using a proxy server? Also try pinging googlecom from the terminal and see what happens.

---

### Post by tgalati4 on 2008-02-01
Try deleting the cache.  Tools-->delete private data.  If there is bad cache data for a specific site, like google, it will continually cause problems.

---

### Post by MarkX on 2008-02-01
> **Seisen said:**
> Just out of curiosity are you guys using a proxy server? Also try pinging googlecom from the terminal and see what happens.

No, and I being a noob I have no idea what to do with "information" from a ping, not that I would know how to ping (I'd rather have software that doesn't need me to fix it's bugs).

---

### Post by MarkX on 2008-02-01
> **tgalati4 said:**
> Try deleting the cache.  Tools-->delete private data.  If there is bad cache data for a specific site, like google, it will continually cause problems.

I'll try that when I am at the friend's place next.

Edit: Actually I already have it set to delete private data every time it shuts down.

---

### Post by Seisen on 2008-02-01
To ping google.com open up the terminal by going to  Applications>Accessories>Terminal and once that opens up type this in.

```
ping www.google.com
```

---

### Post by MarkX on 2008-02-01
> **Seisen said:**
> To ping google.com open up the terminal by going to  Applications>Accessories>Terminal and once that opens up type this in.

```
ping www.google.com
```

I'll try that, thanks.

---

### Post by MarkX on 2008-02-05
> **Seisen said:**
> To ping google.com open up the terminal by going to  Applications>Accessories>Terminal and once that opens up type this in.

```
ping www.google.com
```

Did that and here's a sample of the reply:
64 bytes from [www.google.com](www.google.com) (66.102.9.147): icmp_seq=1 ttl=242 time=42.8 ms
64 bytes from [www.google.com](www.google.com) (66.102.9.147): icmp_seq=2 ttl=242 time=46.5 ms
64 bytes from [www.google.com](www.google.com) (66.102.9.147): icmp_seq=3 ttl=242 time=43.1 ms
64 bytes from [www.google.com](www.google.com) (66.102.9.147): icmp_seq=4 ttl=242 time=46.4 ms
64 bytes from [www.google.com](www.google.com) (66.102.9.147): icmp_seq=5 ttl=242 time=43.8 ms


OK COME ON NOW, this is no joke! I can't get to any of the search engines (they just time out)  but plenty of other sites! Please HEEELP!!! Hotmail won't log in either. 
I tried the useragent switch, no difference. Is it some stupid font thing maybe?
[COLOR="Red"][SIZE="7"]HEEEELP![/SIZE][/COLOR]

---

### Post by MarkX on 2008-02-05
[COLOR="Red"][SIZE="7"]FIXED IT![/SIZE][/COLOR]

I upgraded the firmware on my Draytek which solved the problem in UBUNTU (though it worked in XP before no problem).
It appears that XP works better with marginal adsl than ubuntu for some reason.

---

