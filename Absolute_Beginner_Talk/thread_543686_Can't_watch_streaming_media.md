---
title: "Can't watch streaming media"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-09-05
Hello


I''m trying to watch streaming news from Finnish website

[http://www.mtv3.fi/](http://www.mtv3.fi/)

I click on "MTV 3 Anytime Netti TV"  link at top middle of page.  When new window opens I select news item from left margin but nothing happens. Can you help me?

Thank you.

---

### Post by mali2297 on 2007-09-05
According to the information given on the site, it won't work in Linux. They use DRM (Digital Rights Management).

EDIT: I opened the wrong link, the news stream works. Let's see what you need...

---

### Post by lentomies on 2007-09-05
Thank you for your reply. Interesting to note your in Uppsala. I understand my people come from there.

Please let me know if you find the fix to my proplem.

---

### Post by mali2297 on 2007-09-05
Alright, you need to add the Medibuntu repository, see here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

Then you need to install w32codecs. In the terminal, type:
```

sudo apt-get install w32codecs

```

and possibly mplayer-plugin for firefox:
```

sudo apt-get install mozilla-mplayer

```

You can also use Synaptic to install the packages.

---

### Post by lentomies on 2007-09-05
I get this error message when trying to get the windos codecs

paavo@paavo-desktop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
paavo@paavo-desktop:~$

---

### Post by svalding on 2007-09-05
Look thru synaptic for the packages, you should be able to find them there.

---

### Post by lentomies on 2007-09-05
Well here come the stuoid questoin. What is Synaptic and where is it located?

---

### Post by mali2297 on 2007-09-05
Try *Manually edit sources.list* in the link I gave you. Check that there isn't a # in front of
```

deb http://packages.medibuntu.org/ feisty free non-free

```
Then proceed with the instructions given.

---

### Post by mali2297 on 2007-09-05
> **lentomies said:**
> Well here come the stuoid questoin. What is Synaptic and where is it located?

It's the package manager for Ubuntu. It's an alternative to running *apt-get* in the terminal. You can find a bunch of programs in Synaptic that are available for installation. It should be the first place to look when you want  to install something. It can be found somewhere in the *Systems* menu, perhaps under an alias like *Package Manager*.

---

### Post by lentomies on 2007-09-05
Well I think I have done everytihng correctly and still I cannot view this site!

Any other sugestions?

---

### Post by mali2297 on 2007-09-05
Try another stream, like this 
[http://www.cbc.ca/mrl3/14635/thenational/thenational.wmv](http://www.cbc.ca/mrl3/14635/thenational/thenational.wmv)

Does that work?

---

### Post by mali2297 on 2007-09-05
> **lentomies said:**
> Well I think I have done everytihng correctly and still I cannot view this site!

Just so that everything is clear, you did manage to resolve your problem with w32codecs, right?

---

### Post by lentomies on 2007-09-05
Hi again!!

I can see & hear the site you asked me to go to I.E..

ry another stream, like this
[http://www.cbc.ca/mrl3/14635/thenati...henational.wmv](http://www.cbc.ca/mrl3/14635/thenati...henational.wmv)

But for what ever reason I can't see the finnish news on the website I noted above.

I went to sypnatic manager and got the codecs...

What you think it is?

---

### Post by mali2297 on 2007-09-05
Well, the news streams are playing just fine for me. I use mplayer-plugin, you did install that, didn't you?

You might have some special settings, try to clear all cookies (tools-->clear private data).

I'm running out of ideas now... :-k

Sorry.

---

### Post by lentomies on 2007-09-06
That was it! Now it all works perfectly! Each time I go here it shows mplayer plug in!

Thanks!

---

### Post by alienexplorers on 2007-09-06
If you are running firefox have you tried adding the add-on MediaPlayerConnectivity:
> [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

