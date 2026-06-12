---
title: "Firefox Freezes and system monitor shows firefox using 100% cpu"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-09
This is a nuisance, every so often firefox freezes, mostly on this website!

Checked system monitor and its firefox on 100%

Weird or what.

---

### Post by MenZa on 2007-08-09
Try running Firefox from a terminal, and paste the output here (from about the time it crashes).

---

### Post by ErusGuleilmus on 2007-08-09
I'm sorry that I don't have more info for you. I fixed this by typing in about:config into the url bar and changing an option. I don't remember what that option was. Go to cnet.com and search "how to make Firefox faster" by changing that option you turn off the caching of the web pages you visit. This worked for me.

---

### Post by K.Mandla on 2007-08-09
I've also seen something like this happen when I change a theme and Firefox is running. Is it possible that you're seeing the same thing?

---

### Post by philinux on 2007-08-09
Not changed anyting for 2 weeks but it happens regularly on this website, not seen it on others though.

---

### Post by kayvortex on 2007-08-09
Adding to what ErusGuleilmus said, I think disabling ipv6 *could* be the solution to your problem. I've not done it myself, but you can do this from about:config.

Edit: Although, do as MenZa says and run firefox from a terminal and post that here first!

---

### Post by MenZa on 2007-08-09
Again, try running it from the terminal.

---

### Post by philinux on 2007-08-09
Trying this from about:config

filter    network

set network.http.pipelining  > change to true
set network.http.proxy.pipelining >change to true

Found this from google increase firefox speed.

I'll have to try it though

---

### Post by philinux on 2007-08-12
Thought this had fixed it but it's back again. And mainly this website, I wonder if it's java?

---

### Post by MenZa on 2007-08-13
To my knowledge, there's no Java on this website. Could you, as I've asked you three times now, try running Firefox from a terminal and tell me what (if any) output you get when this problem occurs?

---

### Post by philinux on 2007-08-14
Ok ran forefox from terminal. After aout 10 mins surfing and on this website, same thing. No messages in terminal apart from killed when I closed it for not repsonding.

---

### Post by forkman on 2007-08-24
Having the same issue. Running 64bit version. Always freezes on youtube, ebay, and pretty much any site with flash. have tried with gnash and with libflash. Had no problems with 64bit fawn.

---

### Post by forkman on 2007-08-24
I should also add that konquer works fine.

---

### Post by bmilleker on 2007-10-12
I was getting these errors when running firefox with gutsy:

```
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Message timeout
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Message timeout
```

They were caused by nsplugin errors. Something during the Gutsy upgrade must effect nsplugin.

I fixed it by completely removing nsplugin, and then adding flashplugin-nonfree.

---

### Post by rattusdatorum on 2007-10-21
I have the same problem, it goes like this:

firefox goes black/white -> gray and doesn't really react. The mouse cursor changes, but
nothing happens.
also it happens on different sites, one time I wasn't actively surfing (just watching a movie), also it happend when there was no flash involved (I use the non-free stuff).

so far it only happened 2 times in about 3-4 days.

---

### Post by Fire on 2007-10-22
I am having the same issue.  The on thing that I have found will reproduce the problem consistantly is to go on to a site that is running flash and press something which would open a new window.. that automaticly causes it to freeze... and when this happends one of the processers goes to 100%

---

### Post by philinux on 2007-10-23
Just add blocked *google-analytics* and this site loads a lot faster

---

### Post by alienexplorers on 2007-10-24
The grey issue I had was caused by the Visual Effects turned on in Ubuntu.  
> [http://kb.mozillazine.org/Firefox_hangs](http://kb.mozillazine.org/Firefox_hangs)
> [http://kb.mozillazine.org/Firefox_crashes](http://kb.mozillazine.org/Firefox_crashes)
> [http://kb.mozillazine.org/Firefox_CPU_usage](http://kb.mozillazine.org/Firefox_CPU_usage)
> [http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions)

---

### Post by WiFi Ed on 2007-10-24
I sometimes get 100% cpu usage on one core and a 20 second "hang" when using the Cntrl key / mousewheel combo to change font size in Firefox. My Firefox install is stock with no additional extensions or add-ons, but I am using flash with ndiswrapper. Odd...

---

### Post by slowpoison on 2007-10-25
I was facing the same problem... particularly if I tried to spawn more than 2 windows of Firefox it would always start consuming 100% CPU and hang. I discovered this to be a Google Toolbar problem. I disabled the toolbar and it's OK now.

One thing I realized while disabling various plugins - with no plugins at all, firefox is hella lost faster!!

---

