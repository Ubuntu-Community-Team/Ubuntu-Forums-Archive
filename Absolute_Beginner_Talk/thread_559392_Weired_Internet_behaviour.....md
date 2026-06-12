---
title: "Weired Internet behaviour...."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by aj5string on 2007-09-25
HI...

just wondering if you could help me?  My internet seems really slow when im using ubuntu; saometimes images and eben pages won't load.  It started a couple of days ago - before that it was fine.  I connect directly to a router (LAN).  My girlfirends laptop connects wirelessly to this and is fine, and when i use XP on my computer, connecting in exaclty the same way as i do with ubuntu its fine...

Any ideas?

Alex.

---

### Post by por100pre1 on 2007-09-25
Any programs, Firefox extensions, tweaks 2 days ago? Which browser do you use? Does this happen with all browsers?

---

### Post by hyper_ch on 2007-09-25
Does your router support IPv6 and if not, did you disable it on your ubuntu installation?

---

### Post by HereInOz on 2007-09-25
The first thing that I would do is to test whether it is a networking problem or a webpage rendering problem.  The easiest way to do that is to download a decent sized file - 10MB or so, from a server which you know is good, and is going to give you all the download speed you have.

Watch the download rate and if it is consistent, and about as high as you would expect with your Internet connection, then there is nothing wrong with the way that Ubuntu gets its data through the network interface.  You would then need to look at your web browser and see if you can work out what is going on in that area.

If the download rate of the file is indeed slow, then you can assume that the problem is the network interface, not the browser.  

I know this is probably not much help at the moment, but at least it will narrow down where the problem may be.

---

### Post by lisati on 2007-09-25
Cookies? These can be cleared with the Firefox Tools->Clear private data menu option.

---

