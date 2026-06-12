---
title: "Need a guide.."
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by strider* on 2008-01-30
I setup a DNS on my Ubuntu server and I'm so very thankful for this source [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093) ... It really helps... thanks..

I'd follow the instructions carefully that's why I didn't mess up. The thing is I'd just follow it, without even knowing of what's the use/importance of those files and there functions...

>db.0
>db.127
>db.255
>db.empty
>db.local
>db.root
>named.conf
>named.conf.local
>named.conf.options
>rndc.key
>zones.rfc1918

although some of those files were not included to edit on the tutorial, I still want to know about them... I hope this don't take too much but I still want to give it a try to ask it here.. I hope someone will give me enlightenment about this matter... Thanks in advance

---

### Post by kidders on 2008-01-31
Hi there,

Some of the files you mentioned contain information designed to prevent the propagation of DNS queries that would violate the protocol specification or open your network to security issues. I can give you a more detailed explanation if you'd like me to, but imo, the following fall under that heading...
[LIST]
[*]db.0
[*]db.127
[*] db.255
[*] db.empty
[*] db.local
[*] db.root
[*] zones.rfc1918[/LIST] Then you have...
[LIST]
[*] **named.conf** - The master config file.
[*] **named.conf.local** - Somewhere for you to define local zones.
[*] **named.conf.options** - A place to declare settings that affect the overall operation of your DNS server.
[*]** rndc.key** - A secret key, normally used in the course of dynamic DNS updates.[/LIST]Ordinarily, many of these files would be blended together into a much smaller set, making your server configuration much easier to understand. However, the Ubuntu devs seem to prefer to separate reasonably self-contained groups of configuration options into individual files ... an approach which, while confusing at first, has a number of major advantages. Apache is another good example of where the Ubuntu gods have done this sort of thing.

Essentially, you can ignore most of the files you listed, and leave Ubuntu to manage them on its own, as it sees fit. The ones you'll be most interested in on a day-to-day basis are probably **named.conf.options** and **named.conf.local**. It's generally best not to do anything that might alter the content or timestamps of the others, if you can avoid it. Whatever about the second group of files I listed, you should certainly not modify any in the first for any reason, unless you _really_ know what you're doing.

Anyhow, I hope that helps.

---

