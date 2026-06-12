---
title: "Bad request browser  message"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by urvaksh on 2007-07-12
When I try to log into a Bank of America account while in Linux, I get this message:

Bad request
Your browser sent a query this server could not understand. 

I don;t have a problem with any other site. Also, this problem occurs whether I use Opera or Firefox 
please help. Thanks.

---

### Post by Moop on 2007-07-12
I use Firefox to log into my BOA account no problem. I read in another thread that it could be a flash problem. There is an extension for firefox that will block flash. Maybe try that. Noscript would be another extension to check out.

---

### Post by p_quarles on 2007-07-12
It might be one of those sites designed specifically for MSIE. 

In Firefox, you can install this:
[http://prefbar.mozdev.org/installation.html](http://prefbar.mozdev.org/installation.html)

That'll allow you to identify as Explorer.

In Opera, right-click on the page you're viewing, choose the "Edit Site Preferences" option, then click on the "Network" tab. The dropdown menu on the bottom will allow you to identify the browser as Explorer.

---

### Post by urvaksh on 2007-07-13
This problem with the BOA site only began a few days ago. Also, I can log into the site from my lappie when I'm booted into Windows. This seems to be a problem only when I'm in Linux and just this site.
I tried the work around in Opera, but that doesn't seem to work.
I use NoScript and have been doing so for months.

---

### Post by Hatchetfish on 2008-07-24
I just started getting this a week or two ago.  First in Opera, since it's my preferred browser, then tried in:
Swiftfox
Firefox
Konqueror
Epiphany
Galeon
Amaya
Lynx

Same issue in *every* one (except lynx, that gives an http 500 Internal Server Error)

Then I tried it from a windows machine in my living room, and lo, it loaded.  Opera, Firefox, Internet Destroyer, Safari.  no problem for any of them, using the same settings in opera and firefox I do on ubuntu.  (seriously, I take great pains to synchronize the settings)

I'm growing suspicious that maybe BofA is sniffing for the OS, and being boneheads when it comes up anything but Win or Mac.

---

