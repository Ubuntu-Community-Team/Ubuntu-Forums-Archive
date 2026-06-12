---
title: "Taming the fox on fire..."
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by tcoffeep on 2007-07-21
Hey everybody,

I'm just wondering if any of you have a good guide on Firefox tweaking. More or less, the tweaking of about:config. I've tried a few, but they always had something like :

Fast Computer, Fast Connection
Slow Computer, Fast Connection
Slow Computer, Slow Connection
Fast Computer, Slow Connection

And I'm not sure what mine is anyways. Any ideas? I'll owe you my life :)

---

### Post by misfitpierce on 2007-07-21
If you seek a tweaked firefox perhaps try swiftfox... Auto detects cpu and stuff apparently and configs itself.

---

### Post by tcoffeep on 2007-07-21
I want to understand the Gecko engine a tad better, and I've tried Swiftfox, and it didn't suit me. I'm actually very interested in the inner-workings of Firefox, Epiphany, and Galeon, and the such. I'm actually very much interested in self-tweaking. :)
Thanks for the advice, though.

---

### Post by crimesaucer on 2007-07-21
What I suggest is to use Swiftweasel because it worked faster then Swiftfox for me:  [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)


...then, use these about:config settings:

follow this really good older guide: [http://forums.mozillazine.org/viewtopic.php?t=53650](http://forums.mozillazine.org/viewtopic.php?t=53650)

...but use the newest settings for 2.0.0.5 from these guides: 

[http://kb.mozillazine.org/Category:Tweaking_preferences](http://kb.mozillazine.org/Category:Tweaking_preferences)
[http://kb.mozillazine.org/Category:Preferences](http://kb.mozillazine.org/Category:Preferences)
[http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Mail.db+timestamp+leeway](http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Mail.db+timestamp+leeway)
[http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries) 


I find this works perfectly for me.


Then deactivate your IPV6:

edit the file ```
/etc/modprobe.d/aliases
```


by adding the lines: 

```

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off

```

and commenting / removing the line:

```
alias net-pf-10 ipv6
```


You can also try OpenDNS: [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

faq: [http://www.opendns.com/faq/](http://www.opendns.com/faq/)

---

### Post by tcoffeep on 2007-07-21
I'll check those links out :) Thanks alot. If anybody else has more suggestions, please, the more, the merrier. (that's how the saying goes, right?)

---

