---
title: "firefox-pgo-beta 3.1b2-1 SO FAST!"
date: 2009-01-18
forum: Arch and derivatives
---

### Post by crimesaucer on 2009-01-18
firefox-pgo-beta 3.1b2-1 in the AUR: [http://aur.archlinux.org/packages.php?ID=22919](http://aur.archlinux.org/packages.php?ID=22919) is about the fastest browser I've used yet. (with flash 10.0.d21.1-1 / jre_beta 6u12_b03-1 working perfectly)


I just went through a week of trying a bunch of different browsers. I built midori-git (with libwebkit-git) as well as epiphany-webkit (also using libwebkit-git).... both were very fast but lacked a working jre plugin..... plus there were other things that were buggy or just broke (like epipnany's url search engine).


I also was using google chrome and opera on my Vista partition. They all felt faster than my FF3.0.5-2 that was optimized for my processor (which is still faster than my Vista FF3.0.5.... but this FF3.1b2-1-PGO is feeling much faster..... and pretty stable too.....

---

### Post by RedSquirrel on 2009-01-18
> **crimesaucer said:**
> firefox-pgo-beta 3.1b2-1 in the AUR: [http://aur.archlinux.org/packages.php?ID=22919](http://aur.archlinux.org/packages.php?ID=22919) is about the fastest browser I've used yet. (with flash 10.0.d21.1-1 / jre_beta 6u12_b03-1 working perfectly)
Interesting.  Can you elaborate?  In what way(s) is it faster? Where are you seeing the improvement?

---

### Post by crimesaucer on 2009-01-18
> **RedSquirrel said:**
> Interesting.  Can you elaborate?  In what way(s) is it faster? Where are you seeing the improvement?

I had been using firefox 3.0.5-2 for the last 4 months that was built with CFLAG optimizations and all sorts of stuff stipped out. It was faster than swiftfox and regular FF3.... but it never had that snappy feeling of epiphany. (even with all of the ArchWiki "about:config" tips)


This FF3.1b2-1 has the snappy "loads-all-the-page-at-once" feeling. Even on large pages like the Ubuntu Screenshots thread.... or other pages that would take a couple of re-trys to load.... like Digg.com with a bunch of comments.


I don't have a way to benchmark it, but it just seems to load all pages instantly whether it's a forum page or a page full of photos.


I think they have really made some improvements with this new beta. Maybe it's the profile-guided optimization and CFLAGS/LDFLAGS.....


I warn you that this PGO build took me over an hour-and-a-half to compile.... but everything is pretty stable (for a beta).

---

### Post by SomeGuyDude on 2009-01-18
Yes. It's much faster, and the compile is PAINFUL. I figured it'd be 10 minutes. So I unplug my laptop and go to play some RockBand while keeping an eye on the machine. Hour later my battery's almost dead and my CPU temp is 9000 degrees. Still, I like it, even if some of my plugins don't work right.

---

### Post by crimesaucer on 2009-01-18
> **SomeGuyDude said:**
> Yes. It's much faster, and the compile is PAINFUL. I figured it'd be 10 minutes. So I unplug my laptop and go to play some RockBand while keeping an eye on the machine. Hour later my battery's almost dead and my CPU temp is 9000 degrees. Still, I like it, even if some of my plugins don't work right.

I had a broken link to this "libhx509.so.4.0.0" shared library (I must of built heimdal and it's related packages in the wrong order).... so I ended up building "FF3.1b2-1" THREE different times (each time it gave an error at the very end of the build about my libhx509.so.3 not existing to point to the shared library)..... so after I finally made a libhx509.so.3 symlink to access that shared library I was able to build it properly.


So it actually took me about 6+ hours to get it correct.

---

### Post by RedSquirrel on 2009-01-18
> **crimesaucer said:**
> This FF3.1b2-1 has the snappy "loads-all-the-page-at-once" feeling. Even on large pages like the Ubuntu Screenshots thread.... or other pages that would take a couple of re-trys to load.... like Digg.com with a bunch of comments.

I don't have a way to benchmark it, but it just seems to load all pages instantly whether it's a forum page or a page full of photos.

I think they have really made some improvements with this new beta. Maybe it's the profile-guided optimization and CFLAGS/LDFLAGS.....

I warn you that this PGO build took me over an hour-and-a-half to compile.... but everything is pretty stable (for a beta).

According to the [What's New]("http://www.mozilla.com/en-US/firefox/3.1b2/releasenotes/") page, there are a number of improvements (on paper, anyway) in the new version, even without a PGO build. I don't think I'll jump in just yet, but thanks for the info you have provided. :)

---

### Post by smartboyathome on 2009-01-18
I just compiled it. First thing it made me think: TOO MANY DARN LINES! The lines are about 3 pixels tall, and all over under words. Thin them up, please. :(

Second thing it made me think: Oh no, not the new tab button. I usually dont use that. Is there any way to get rid of it?

Third thing it made me think: Wow, this IS fast. I only wish that a few plugins worked with it. :(

---

### Post by smartboyathome on 2009-01-18
Edit: Dang, double post.

---

### Post by crimesaucer on 2009-01-18
> **smartboyathome said:**
> I just compiled it. First thing it made me think: TOO MANY DARN LINES! The lines are about 3 pixels tall, and all over under words. Thin them up, please. :(
I don't understand this?


Also, I don't have a new tab button. I thought they removed that feature. As for plugins..... my about:config had this:

```

extensions.checkCompatibility = False
extensions.checkUpdateSecurity = False

``` 

So most my plugins are working for me. (at least my important ones)

---

### Post by SomeGuyDude on 2009-01-18
Second attempt: it's fast but... inconvenient.

One problem: the URL bar has totally lost half its functionality. It used to be if you put in a word, it would check if it was a domain and, barring that, google the word. So I could punch in "ubuntu" and it would give me the Ubuntu homepage. Now if I just put in a word I get an error.

Second: Speed Dial used to leave the URL bar blank so if I opened up a new tab, I could just start typing something. Now Speed Dial has its own URL in there and I have to highlight/delete, THEN type. It's getting bothersome and I downgraded.

---

### Post by smartboyathome on 2009-01-19
> **crimesaucer said:**
> I don't understand this?


Also, I don't have a new tab button. I thought they removed that feature. As for plugins..... my about:config had this:

```

extensions.checkCompatibility = False
extensions.checkUpdateSecurity = False

``` 

So most my plugins are working for me. (at least my important ones)

I thought they did too, but the new tab button is back for me.

Also, thanks for those settings. It helps a lot. :)

---

### Post by SomeGuyDude on 2009-01-19
Further update. I tried to install the firefox-pgo non-beta version, and both times after it spent about an hour compiling it completely locked up my machine. I am... SO done with those things. Wasted my entire evening.

---

### Post by ghindo on 2009-01-19
When is the final release supposed to be?

---

### Post by gjoellee on 2009-01-19
Yes Firefox 3.1 is fast, and it hopefully will be faster.

ave anyone tried Opera 10? That is extremely fast as well!

---

### Post by smartboyathome on 2009-01-19
> **gjoellee said:**
> Yes Firefox 3.1 is fast, and it hopefully will be faster.

ave anyone tried Opera 10? That is extremely fast as well!

Nope, and I won't be either unless the Qt integration gets better. I'm done with trying to fight with Opera to get it to blend in with my desktop.

---

### Post by gjoellee on 2009-01-19
> **ghindo said:**
> When is the final release supposed to be?

Still not known, but it will be before August I guess ;)

---

### Post by crimesaucer on 2009-01-19
> **gjoellee said:**
> Yes Firefox 3.1 is fast, and it hopefully will be faster.

ave anyone tried Opera 10? That is extremely fast as well!


I'll probably use that on my Vista partition.

---

### Post by crimesaucer on 2009-01-19
> **smartboyathome said:**
> Also, thanks for those settings. It helps a lot. :)


No problem.

---

### Post by linkmaster03 on 2009-01-20
Making plugins compatible: [https://addons.mozilla.org/en-US/firefox/addon/6543](https://addons.mozilla.org/en-US/firefox/addon/6543)

---

### Post by smartboyathome on 2009-01-20
> **linkmaster03 said:**
> Making plugins compatible: [https://addons.mozilla.org/en-US/firefox/addon/6543](https://addons.mozilla.org/en-US/firefox/addon/6543)

Use that, but found it only worked on already installed stuff.

---

