---
title: "instant messenger in feisty ?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by jrev on 2007-07-01
Do you use an instant messenger on feisty ? 

which one  ?

Does it work properly ?

Thanks for your advice. I just installed feisty and gaim 2.0.0 beta 6 but no start of it 

there is no pidgin in synaptic:D

---

### Post by Jimmyfj on 2007-07-01
Yes I use IM in Ubuntu. My favourit is aMSN and Pidgin

---

### Post by Delkster on 2007-07-01
I use Gaim, the version supplied with Feisty. It works okay for me.

---

### Post by AlexenderReez on 2007-07-01
> **jrev said:**
> Do you use an instant messenger on feisty ? 

which one  ?

Does it work properly ?

Thanks for your advice. I just installed feisty and gaim 2.0.0 beta 6 but no start of it 

there is no pidgin in synaptic:D

hm..there must be wrong setting somewhere....you can get pidgin in extra repository provided by community ......

---

### Post by psycho78 on 2007-07-01
I use kopete in Kubuntu..., and licq under fluxbox on my laptop..... both work great..!

---

### Post by trigun on 2007-07-01
hi. I used gaim for a long time but now with i use pidgin (actually it's the same thing :P) pidgin  with all the plugins it's very complete e still simple :) ...it's a shame that doesn't have support  for some things,..yet ;) cheers

---

### Post by paradoxni on 2007-07-01
i prefer amsn as it supports direct file transfers in MSN, where as in GAIM/Pidgin file transfers occur at 2k/sec. 

the standard amsn doesnt look so pretty, but i used the script available [here]("http://ubuntuforums.org/showthread.php?t=297676") to install it with anti-aliased fonts and changed the font to Bitstream Vera Sans, size 9 in amsn preferences > appearance.

here is a screenshot:

---

### Post by AndyCooll on 2007-07-01
I use GAIM, the version that comes in the default Feisty install. Works fine for me.

To the OP, can you please be more specific about what issues are you having with it?

:cool:

---

### Post by jrev on 2007-07-01
I downloaded aMSN from Automatix then 

I just tried aMSN which proposes to download a TLS file.

I chose Linux-x86 first on the list 

and when I accept the download of the file is complete but the installation failed 
[[img]http://www.enregistrersous.com/images/vignettes_images/31658576320070701152841.png[/img]](http://www.enregistrersous.com/images/3/31658576320070701152841.html)

---

### Post by paradoxni on 2007-07-01
try this in terminal

```
sudo apt-get install tcltls
```

the script worked fine for me before, perhaps the server is down or the file is no longer on the server.

---

### Post by jrev on 2007-07-01
Thanks paradoxni,

I got the message that it's already installed

---

### Post by paradoxni on 2007-07-01
and is amsn working or still complaining about tls not found?? you could try manually adding /usr/lib/tls1.50 to preferences > advanced > TLS: location

---

### Post by jrev on 2007-07-01
tcltls is already installed ...

---

### Post by jrev on 2007-07-01
OK thanks 

I start all over again with new doc...

---

