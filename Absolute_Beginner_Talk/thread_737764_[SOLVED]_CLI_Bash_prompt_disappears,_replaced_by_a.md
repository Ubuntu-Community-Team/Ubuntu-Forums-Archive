---
title: "[SOLVED] CLI: Bash prompt disappears, replaced by a &amp;quot;&amp;gt;&amp;quot;, Have to reboot"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by DBrocks on 2008-03-27
Hey guys, I've been having some strange things happening. If I enter a command Ubuntu doesn't particularly like, something strange happens. my 
```

Dan@Email-Server ~$
``` disappears, and is replaced by a 
```
>  
```
Then, I can't do anything. I tried to change my PS1, and that didn't work. The only thing that works is a restart. Any help is appreciated! Thanks!

~Dan

---

### Post by Joeb454 on 2008-03-27
What happens if you hit ```
ctrl c
```

As in Ctrl & C at the same time ;) Thought I'd make it completely clear :)

---

### Post by DBrocks on 2008-03-27
Thanks for the speedy response. That works. I can't believe how simple that was. Thanks again! That made my life so much easier! Now, might I ask, why does it do that. (I want to learn!) lol :)

---

### Post by Joeb454 on 2008-03-27
Why does it do what? Go to the > prompt?

It's because it doesn't know what to do, chances are you've given a valid command with an invalid flag (e.g. mv -ah) so it will try and do something, then just sit there like that.

I have no idea why. But Ctrl + C seems to be the universal command for killing processes from a terminal (even in Windows).

---

### Post by DBrocks on 2008-03-27
> **Joeb454 said:**
> Why does it do what? Go to the > prompt?

It's because it doesn't know what to do, chances are you've given a valid command with an invalid flag (e.g. mv -ah) so it will try and do something, then just sit there like that.

I have no idea why. But Ctrl + C seems to be the universal command for killing processes from a terminal (even in Windows).

Thanks alot man. (My first question answered!!) Might I say: I am going to stop using google as my main source of answering my ubuntu-related questions. I am turning to these forums first. There are so many people with so much know-how who are willing to share it with others! Its people like you I look up to, and want to be like. Thanks alot! Happy to mark this thread as "Solved".

---

### Post by Joeb454 on 2008-03-27
Thanks for that! It always helps marking a thread as solved, for us trying to help, and for people trying to find an answer :)

There's also a thanks feature (it's the gold star ;)) Now I'm just being vain :lolflag:

---

### Post by DBrocks on 2008-03-27
> **Joeb454 said:**
> Thanks for that! It always helps marking a thread as solved, for us trying to help, and for people trying to find an answer :)

There's also a thanks feature (it's the gold star ;)) Now I'm just being vain :lolflag:

No, also, I wanted to know how to thank people so it registers. Carry on your way of geniusness. Don't stick around here long! :lolflag:

---

### Post by Joeb454 on 2008-03-27
:lolflag: I like your style ;)

Don't hesitate to make another thread if you need help though :) Somebody will have an answer

---

