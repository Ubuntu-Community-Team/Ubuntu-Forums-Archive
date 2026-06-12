---
title: "[SOLVED] URL is impossibly slow using v7.10 &amp;amp; Firefox 2.0"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by JackS on 2007-12-21
Windows loads this web page quickly and ubuntu loads it VERY slowly.
Acually, this URL runs so slowly that it is not useful:
[http://lgb.webtrak-lochard.com/introduction.html](http://lgb.webtrak-lochard.com/introduction.html)

I need speed.  Does anyone have any advice?
What am I missing in my linux configuration?


Here's my hardware and software:
$ uname -a
Linux sunbus-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

Here's a little bit about my Firefox 2.0 application:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11

I have installed the Adobe SVG plugin, from here:
[http://www.adobe.com/svg/viewer/install/main.html](http://www.adobe.com/svg/viewer/install/main.html)
[http://download.adobe.com/pub/adobe/magic/svgviewer/linux/3.x/3.01x88/en/adobesvg-3.01x88-linux-i386.tar.gz](http://download.adobe.com/pub/adobe/magic/svgviewer/linux/3.x/3.01x88/en/adobesvg-3.01x88-linux-i386.tar.gz)

And it passes this test:
[http://www.adobe.com/svg/viewer/install/svgtest.html](http://www.adobe.com/svg/viewer/install/svgtest.html)


I'd love to learn what I need to fix here.  Don't want to use Windows.
Thanks,

-Jack

---

### Post by philinux on 2007-12-21
15 seconds plus to load in opera as well. Keeps waiting for the website to reply with data. Runs better in opera.

---

### Post by sports fan Matt on 2007-12-21
I can confim this behaviour...Maybe installing Opera as a second browser for sities like this one since it is faster then Firefox is an option for you?

---

### Post by JackS on 2007-12-21
I tried a couple different DNS servers.  Thought that might speed
things up.  It didn't.

This URL loads and runs nicely on MS XP-pro at the library.  Too
bad linux isn't up to that pace. 

I will install Opera and see how it goes.  Another thought was to
use WINE and Explorer, but using Windows s/w is a last resort.

Thanks for the replies,
-Jack

---

### Post by JackS on 2007-12-22
Opera installation was dirt simple.  I was up and running in
minutes.  Opera solved the problem.   Opera seems to have
implemented the SVG differently than Mozilla/FFox.
[http://www.opera.com/](http://www.opera.com/)

Thank  you

---

