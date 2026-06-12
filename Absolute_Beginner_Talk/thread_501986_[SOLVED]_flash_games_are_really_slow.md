---
title: "[SOLVED] flash games are really slow"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-07-16
flash based sites and games are slow..it works but some of them are slow.. is there a way to fix it ?

---

### Post by kavon89 on 2007-07-16
1. System Specs?
2. Make sure you have the latest Flash, check the Synaptic Package Manager and search for Flash. A little ways down you should find "flashplugin-nonfree" which is currently the latest version 9. Install that and see if it speeds things up.

---

### Post by HunkieChan on 2007-07-17
i already have flash firefox plugin and its 9.. but when i checked synaptic i found libflash-mozplugin. so i installed it. i hop ethat works

---

### Post by bretticus on 2007-07-17
I have noticed that flash for linux (in firefox) seems to run slower than the windows counterpart on certain flash files. Yet on others, I see no difference. I suggest updating to the very latest. You can bypass apt/dselect/synaptics and download straight form adobe.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

I pick the tar.gz option, extract, and run the installer with root privileges (so you can install it under /usr/lib/mozilla-firefox.) That updates it to minor version 48 which seems to have come out on July 10th of this year. That certainly sped up at least one site that I'm aware of significantly.

---

### Post by askreet on 2008-03-03
None of this worked for me.  Version 9,0,115,0 is the 'latest' and was slow as hell.  However I went here: [http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1)

I downloaded the v9 archive which contains many versions of installers for all OSes.  I used r48 isntead of r115 and flash is much better now.

Hope this helps someone.

---

### Post by HunkieChan on 2008-03-03
i heard its slow on linux

---

### Post by askreet on 2008-03-04
Not if you follow the instructions in my post, it's pretty quick.

---

