---
title: "Safari - For linux as well?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by LinuxLoserr on 2007-06-11
Hi guys, just found out about the "oh so wonderful," new safari by Apple.
Thought it would be worth a try to see if it is actually as good as they say.
But i just wanted to know if it'll work on linux at all- without using wine?
Thanks.

---

### Post by Modred on 2007-06-11
I haven't heard anything about Safari coming to Linux, but considering the current platform availability of most Apple products, I wouldn't keep my hopes up.  Looking at notable Apple products such as iTunes and QuickTime, I'd say a Linux port of Safari is unlikely.

Of course, Safari and Konqueror use the same engine down at the core, but Safari and Konqueror are quite different beasts due to the additional work Apple has done on top of Konqueror, so don't expect KDE's browser to feel or act like Safari if you happen to try it out.

---

### Post by p_quarles on 2007-06-11
I saw a dozen stories in my feed aggregator about it this morning, and none of them mentioned Linux. So, no.

As for how good it is: I installed it in my Windows partition today, and yes, it's slightly faster in loading plain html than Firefox is. But, you know, loading marked up text is not really a huge resource drain for any modern computer. I only wanted it cause I design web pages, and its nice to have it around for testing.

---

### Post by RomeReactor on 2007-06-11
Hi. From what I [read]("http://news.bbc.co.uk/2/hi/technology/6742439.stm"), the port will be XP and Vista only

---

### Post by LinuxLoserr on 2007-06-14
konqueror?
I've never heard of it, is it like a linux version of safari or something?
and if so, is it faster than firefox?

---

### Post by starcraft.man on 2007-06-14
> **LinuxLoserr said:**
> konqueror?
I've never heard of it, is it like a linux version of safari or something?
and if so, is it faster than firefox?

Konqueror is the browser in KDE. You can install it to try via apt with the following in terminal.

```
sudo aptitude install konqueror
```

I personally don't get all this "faster than firefox" business (everyone seems to say it). Is raw speed on pages the only thing that matters in a browser, if so we should just strip out all the features and give ya an url bar and a forward and back button. It is supposedly faster, and is based on khtml. You may find it has trouble loading some pages due to that.

I'm sticking to Firefox, and I wouldn't ever use Safari, it comes from Apple and thus supporting them by using that is encouraging them in general which in turn supports DRM and hardware lock in. I don't like supporting that.

---

### Post by teddybairs1 on 2007-06-14
Epiphany is a quick browser written for Gnome. It is also faster than FF, due to it being a little smaller, but so far can display everything FF can. I recommend getting it by using synaptic or the add/remove, and all of the mozilla plugins which it makes use of. And if you really want the "Safari Look" head over to gnome-look.org and check out the "leopard" theme somebody just recently posted.

---

### Post by Modred on 2007-06-14
Epiphany is basically Gecko (the guts of Firefox) running an interface more finely integrated to GNOME.  I don't know that it actually displays pages any faster than Firefox, but the program itself may load faster.  The first thing I usually do on a fresh Firefox install is to go in and manually edit the settings in about:config to turn on pipelining and increase the max number of connections per server.  After making some optimizations like that, the only browser I've seen compete on page load times is Opera.

Just speaking from personal experience here, so don't expect it to be canonical (hmm...pun....meh).

---

### Post by hyper_ch on 2007-06-15
Konqueror is more than just a webbrowser... it also support multi-pane windows... like where you can easily move things from left to right or bottom to top (different panes) and another nice feature is the fish protocoll which allows me to scp into my server.... it's my default "file system browser" in my xubuntu install.

---

