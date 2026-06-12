---
title: "How can I make Frontpage-designed websites display correctly on Linux?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-06-21
I have a certain class that uses websites that, from the looks of the source code, were created by Microsoft Frontpage 5.0.  The problem is that these sites never display correctly in any browser other than IE.  I even tried installing ies4linux to emulate IE in Ubuntu, and the pages still display incorrectly in IE running under wine, but they display just fine in IE running under Windows.  With the site displaying incorrectly, math expressions often display wrong, especially when greek characters are involved, and the website is mostly unusable to me.  How can I make it work correctly under Linux?  Thanks.

---

### Post by h0ax on 2007-06-21
Are they old sites? could you post the link to it?

---

### Post by Brightbelt on 2007-06-21
Check out [www.codeweavers.com](www.codeweavers.com) 
From what I've read there, Frontpage 2002 does pretty well with CrossOver, a pay-for windows emulation program.  It's only $39.95 so it's not too expensive.

Frontpage 2000 and Frontpage 2002 both get an honorable mention and are documented by others to install and run with CrossOver
.
It's possible that it may run with wine ([www.winehq.org](www.winehq.org)) but I can't be sure of that in any way.

I hope this helps,...Frank B.

---

### Post by the.phantom on 2007-06-21
simple. microsoft page creating software is NOT w3 compliant

if you create a page in w3 it will show correctly in all browsers, if you do it in microsoft stuff it will show correct in a IE browser ;-D

<rant>i check my pages with firefox and then IE
netscape and others were around long before microsoft decided to take over the web !</RANT>

if you know html then the above will make sense ;-D

---

### Post by atria on 2007-06-21
I'm surprised how ignorant people can get.

In any case here are some solutions:
1) Install a virtualisation software like VMWare or VirtualBox and install windows on it.
2) Wine + IE probably didn't work because your wine version might be outdated (try updating it), or IE might be too new (which is recently more w3 compliant).

In all cases, frontpage 5 is really ancient (frontpage has been discontinued since the 2003 version) and you might want to start recommending them to turn to other alternatives.

Hope that helps.

---

