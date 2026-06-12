---
title: "cannot install ati X300 driver"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by medaillon on 2006-09-28
Dear Ubuntu users,

I have a problem with installing the Ati x300 drivers on my Ubuntu OS. this problem caused me to reinstall Ubuntu 4 times already:(
I tried to follow several solutions on this forum without succes. I also downloaded the ati drivers from [www.ati.com](www.ati.com) wich caused a startup problem.

I have installed Ubuntu as a dual boot with Winxp on a Laptop.
It is a Dell Inspiron 9300 intell centrino 1.6, with 1 gig ram.
the videocard is a ATI X300 video card.

Can somebody help me with installing the drivers or tell me wich drivers i need to use?

thanks in advanced!

---

### Post by Kateikyoushi on 2006-09-28
Did you check [this]("http://ubuntuforums.org/showthread.php?t=190133&highlight=x850") thread ?

---

### Post by medaillon on 2006-09-29
Yes i did but the given solution did not worked for me. i receive the same error. i've once again reinstalled linux but it seems like i cant install xgl and compiz..everytime i log in as XGL i get a black screen, please help me!

---

### Post by Kilz on 2006-09-29
> **medaillon said:**
> Yes i did but the given solution did not worked for me. i receive the same error. i've once again reinstalled linux but it seems like i cant install xgl and compiz..everytime i log in as XGL i get a black screen, please help me!

Ok [Here is a great howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually"). But some of the lower end cards have problems with drivers from 8.27.10 up. So if you keep having problems try the 8.26.8 version[ i386 version of Ubuntu]("https://support.ati.com/ics/support/KBAnswer.asp?questionID=22595") or [amd64 version of Ubuntu]("https://support.ati.com/ics/support/KBAnswer.asp?questionID=22597").

---

### Post by medaillon on 2006-09-29
I want to thank you guys for replying!
I will try the how to on my laptop when im home.

At this moment i am at work and have a similar problem what i have at home.
that is when i follow this guide: [link]("http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/")
i receive this message:E: Couldn't find package gset-compiz when i want to install xgl and compiz along with the supporting packages.

Please advice me:-D

---

### Post by Kilz on 2006-09-29
> **medaillon said:**
> I want to thank you guys for replying!
I will try the how to on my laptop when im home.

At this moment i am at work and have a similar problem what i have at home.
that is when i follow this guide: [link]("http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/")
i receive this message:E: Couldn't find package gset-compiz when i want to install xgl and compiz along with the supporting packages.

Please advice me:-D

Did you happen to notice this blatent warning on that howto you linked to?

[SIZE="5"]WARNING: due to some sweeping changes to compiz, this howto is now badly out of date. i’m going to be working on a new (much better) version targeted for edgy eft. until then, please head on over to compiz.net for help.[/SIZE]

---

