---
title: "Image and security problems in Firefox"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by MMosley on 2007-10-23
I just upgraded to Gibbon and I've had two problems with Firefox since the upgrade.  

I'm having trouble loading images consistently on some websites.  Sometimes they all load, sometimes half of them load, sometimes none load.  It's different every time I open the browser.

I'm also having problems with secure websites.  I sometimes get a message that the security certificate for a secure page has the wrong signature on it, but then other times I can load the secure page with no problem. 

Both of these issues started immediately after I upgraded to Gibbon.  I haven't made any other changes.  Any help or suggestions would be appreciated!

---

### Post by MMosley on 2007-10-23
Bumping, with more problems :(

After a full day of internet use I'm finding that all of my browsers (Firefox, Epiphany, Opera) are behaving strangely.  Images are loading intermittently, I'm getting random 404 errors for major websites like google and cnn.com, and I'm still getting strange certificate signature messages when I visit secure sites.  I've also had a few instances where I've typed in a URL and ended up on an entirely different website (and no, I wasn't making typos ;) )

I'm a very new Linux user and I'd appreciate any suggestions for getting my internet applications to behave again.

---

### Post by alienexplorers on 2007-10-23
Try these two links with your image problem.
> [http://forums.mozillazine.org/viewtopic.php?t=288184](http://forums.mozillazine.org/viewtopic.php?t=288184)
> [http://kb.mozillazine.org/Images_or_animations_do_not_load](http://kb.mozillazine.org/Images_or_animations_do_not_load)

---

### Post by MMosley on 2007-10-24
Thanks alienexplorers.  Unfortunately those links weren't able to help me.

I've reinstalled Gutsy Gibbon and the problem persists.  I'm still having random image errors, 404s on major websites (I've been able to verify that the sites are not down using my other computer), and security certificate warning messages on secure pages.  None of these problems were happening with Feisty Fawn, they all started when I changed to Gibbon.  

I have no browser add ons.  My internet connection is functioning, and the problems usually go away if I close and restart my browser, however restarting my browser every time this happens is cutting into my productivity, to say the least.  

I'm using a Toshiba Satellite A135-S4527.  I'm also very new to Ubuntu, so even seemingly obvious suggestions may help me.

---

### Post by philinux on 2007-10-24
Goto Application Accesories and click terminal

Type firefox and press enter to run it and it will show any errors in the terminal screen, maybe this will identify the problem.

The other thing to try is again in the terminal type firefox -safe-mode

Then post back

---

### Post by MMosley on 2007-10-24
> **philinux said:**
> Goto Application Accesories and click terminal

Type firefox and press enter to run it and it will show any errors in the terminal screen, maybe this will identify the problem.

The other thing to try is again in the terminal type firefox -safe-mode

Then post back

Thank you for responding :)  Firefox opened normally and no errors were listed in the terminal screen.  Same result in safe mode.

---

### Post by n3tfury on 2007-10-24
are you running wireless or CAT5/6?  if so what kind of router do you have?  it could be an ipv6 problem:

try this:

> First, in firefox address bar, type "about:config". Locate "network.dns.disableIPv6" and set it to true.
restart firefox.

For some people that solves is already, not for me. Second thing to do then:

sudo gedit /etc/modprobe.d/aliases

Locate the line that has "alias net-pf-10" Change it to "alias net-pf-10 off"

^i saved that bit from the forum somewhere, but i don't know the author.  however, it cleared up slow 'net problems after their upgrades.

good luck.

---

### Post by MMosley on 2007-10-24
Thank you n3tfury, that seems to have done the trick.

---

### Post by n3tfury on 2007-10-24
you're welcome.  would you minding marking your thread as solved?

---

