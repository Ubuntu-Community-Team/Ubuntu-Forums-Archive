---
title: "how do you Save entire homepages in Linux? [Resolved]"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-03-22
How do you Save entire homepages in Linux?  I'm trying to download other ppls homepages to study in Windows XP when clicking Save As in Firefox you have 3 options given by Windows to save homepages.

But this luxury seems to be gone in Ubuntu.  Do you know of any programs for Ubuntu that enables me to download whole contents of homepage?  (html+images+css)

Right now I need to download every piece bit by bit compared to Windows XP :(

---

### Post by buuntuu! on 2007-03-22
no big deal!
you'll find "webhtttrack website copier" in the repositories.
makes a 1:1 mirror on your hd :)
have fun

---

### Post by aysiu on 2007-03-22
You can try *wget*: ```
wget -m http://www.nameofpage.com
```

---

### Post by laidback on 2007-03-22
Scrapbook for Firefox may be of interest.

---

### Post by go2dell on 2007-03-22
The fastest way, without learning a new tool, is to just use Firefox's File -> Save Page As.

You should get a dialog box asking for the name of the page.  Since web pages often have strange names, you can rename it something sensible.  You should also make sure that it ends in ".htm" or ".html" to ensure you can open it again easily by just double-clicking.

Firefox will save the page, along with a folder containing images and other related content so that you have a complete offline copy.

As a previous poster already noted, you could also try [Scrapbook]("https://addons.mozilla.org/firefox/427/") from the Firefox Add-ons site.

---

### Post by jingo811 on 2007-03-22
tnx problems solved :)

---

### Post by jingo811 on 2007-03-23
**OFF TOPIC**
I've got a situation that has to do with this copying of homepages.  In our country some guy has made it into a business to rip off other peoples entire webdesigns and and just pasted it entirely into some of his many 1.000 of  domains like .info and such.  Normally you would think that sueing this guy would end the problem right there, but the thing is our country's laws seem to protect this guy like he was Al Capone or something.

Even if the press several years back have information about him selling legal drugs (drugs that haven't been classified as illegal yet) he still didn't go to prison.  Now he claims to have moved on from the drug business on the Internet and are trying new ventures.
This new venture seems to have something with SEO to do, that's why he is ripping of other ppls entire sites and just paste it on other domains.  Like with the drug incident time he seems untouchable by the law at this business also.  

**Question:**
That's why I want to know what methods there are to prevent people from ripping off commercial webpages?  Or at least make it harder for people with bad intentions.
By not having to use Flash sites, it make sites heavy and laggy.

---

### Post by aysiu on 2007-03-23
I don't think there is a way to prevent ripping off of your webpage. If it's viewable by the public, it's usually easily mirrored.

---

### Post by jingo811 on 2007-03-23
Isn't there some sort of passwording of webpages but on a visible but invisible layer of existence.  If you know what I mean.  As to block someone who doesn't know much about advanced html coding from getting all the bits and pieces entirely.  So that they have to reconstruct some of it by hand to fix things?

Coz that rip off bandit doesn't seem to put much efforts in advanced html and coding stuff, he primarily focuses on experimenting with new SEO methods.

Anything to slow down a bandit would be valuable, since most bandits of that caliber in my example don't put their efforts into real creation techniques.  Maybe that little slow down will make them skip my page and go onto some less security built site.

---

