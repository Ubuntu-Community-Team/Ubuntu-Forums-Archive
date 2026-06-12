---
title: "Just a general question..."
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by NewDisciple on 2006-06-10
I have notice that many times when trying to use terminal commands I get an error msg: command not found; and at other times I will get nothing.  Is this due to missing applications and or dependencies?  Also, I wondered if there is a method for checking dependencies for any given application?  Anyway I just wanted to clear up a little general confusion in my mind.

---

### Post by tronica on 2006-06-10
what are some of the commands?

---

### Post by ????? on 2006-06-10
Open Synaptic Package Manager and try to find a package with the same name of the command you want to use (ex. if you have errors running command foo, go look for foo in Synaptic). Chances are that package is not installed

---

### Post by IYY on 2006-06-10
If it doesn't say the command is not found, it means the command is found. To find out where it is, use this:

```
which mycommand
```

For example, if I want to find out what gets executed when I run the command 'cat', I can do the following:

```

which cat

```

And the output will be

```
/bin/cat
```

---

### Post by NewDisciple on 2006-06-10
Most of the commands I have tried to use have come from these forums and wiki.  Many relate to post install setup.  And at times I was just in the mood to explore and experiment a little bit.  My main goal here is to build on my knowledge base which still has gaping holes.  Someday I may even be able to leave my noob status behind me.  Anyway, thanks for the info.

---

### Post by weasel fierce on 2006-06-10
Somewhat related, but as I found after half a day of struggling with something, be very carefull and specific about capital letters :)

Stuff is a completely different file than stuff

---

### Post by xael on 2006-06-10
Here are a few pages that can help you understand a bit about GNU/Linux :

[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

[http://www.brunolinux.com/](http://www.brunolinux.com/)

[http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)

---

### Post by richbarna on 2006-06-10
Look at my sig for BASH commands
|
|
V

---

### Post by NewDisciple on 2006-06-10
Thanks to Xael and richbarna.  Man...those are great links.  Wish I had them two weeks ago, could have advoided the blood, sweat & tears.  All of those links would be benefical to all newbies.  Too bad there isn't a sticky with these listed.  Maybe look at these before you post, or something along those lines.  Again, my deepest appreciation!

---

### Post by richbarna on 2006-06-10
[QUOTE=NewDisciple]Thanks to Xael and richbarna.  Man...those are great links.  Wish I had them two weeks ago, could have advoided the blood, sweat & tears.  All of those links would be benefical to all newbies.  Too bad there isn't a sticky with these listed.  Maybe look at these before you post, or something along those lines.  Again, my deepest appreciation![/QUOTE]

No problem at all, have fun BASHin' around ;)

One thing that you can do to help people, is to go to your user CP, and create a signature like ours with a few handy links.
You will see that most regular users have them.

---

