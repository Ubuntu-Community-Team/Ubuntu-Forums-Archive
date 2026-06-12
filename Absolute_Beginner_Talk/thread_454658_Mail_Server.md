---
title: "Mail Server"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by allllec on 2007-05-25
Hi there,

firstly im new. so like. hay :-) *waves*

secondly - im running ubuntu server on my uh server! and its fantastic :-)

now anyway,

im slowing moving all my server roles over to the linux box and i've got the the last one... the mail server.. the rest was okay becuase all my old server apps are also on linux (ie apache, mysql etc) but my mail server app isnt.. so need your advice!

what is the best mail server to use. its low traffic but it must be fairly fast and as simple as possible. and most importantly it must be able to foward all mail to another email address (thats all it will be doing!)

cheers

alec

---

### Post by kidders on 2007-05-26
Hi there,

_Personally_, I would stick with Postfix, which is a highly scalable, pretty standard choice. If you ever run into trouble, or want to extend its capabilities (eg virus/spam protection, and so on), you can be certain that help will always be at hand.

I've been using it for years, without even a minor problem. I'm sure the same can be said for many other SMTP servers, but I thought I would offer my opinion anyway. :-)

[SIZE=1][COLOR=Silver][*[UAResolved]*]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR][/SIZE]

---

### Post by irish_flu on 2007-05-26
I am a total fanboy lately for "Zimbra".  It's a postfix back-end with a cool AJAX front-end that makes configuration and such pretty easy.

The only caveat is that (if you were insterested in it) you'd need to make sure it wasn't gonna conflict with your other services first....

---

### Post by nickburns on 2007-05-27
Zimbra is the way to go, easy to install on Ubuntu now.  (Just 1 year ago it took hours, not 5 minutes.)

Good Luck

BTW, I have Apache2, Mysql and Zimbra all running on the same box, just need configuration.

---

### Post by allllec on 2007-05-27
Zimbra looks pretty swish - however to be honest i would be inclined to install it on its own box. anyway - a bit overkill so i will try postfix for now :-) thank you for the suggestions however! when i have more time in the future i will deffinatly try it out.

thank you

alec

---

### Post by hyper_ch on 2007-05-27
well, over at howtoforge.com there are "Perfect" tutorials that will guide you through an ISP setup... meaning how you can setup a box in a ISP manner that you can have multiple sites and mailserver and stuff...

---

### Post by allllec on 2007-05-27
Infact Ignore me...

---

