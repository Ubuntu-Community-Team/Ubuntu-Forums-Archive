---
title: "No &quot;open&quot; link in Firefox's Download Manager"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by davesmith on 2007-06-04
Hallo

I've just upgraded from Edgy to Feisty and I use Firefox as my browser. 

In Edgy the Download Manager had a really cool feature, it would stay open after the d/l was finished and an "open" link would appear.

Somehow I dont have this in Feisty now. I've checked the firefox preferences

<edit - preferences - Main> 
and there is no box to check to give me the "open" link feature.

Can anyone plz explain what's wrong here and how to fix it? I liked the "open" link feature!!

Thanks in advance

Davesmith

---

### Post by coolbrook on 2007-06-04
Sounds like a Firefox issue.  2.0.0.4 was just released.  If you don't have the lastest version then consider upgrading to see if that resolves the matter.

---

### Post by steeleyuk on 2007-06-04
In Preferences - Main, is there a check in the box that says 'Close it when all downloads are finished'? If so, you need to uncheck that.

Alternatively, if the download manager is closing then you will need to do the following:

In the address bar, type

about:config

In the filter box type 'download'. You need to look for the entry which is 'browser.download.manager.closeWhenDone'. Double click it to change the entry to false.

If either of those isn't the solution then I don't know. ;)

---

### Post by davesmith on 2007-06-04
Thanks for both your replies

I'm using firefox 2.0.0.4 so it's the latest version

I have unchecked the 'Close it when all downloads are finished' box in <preferences - main> but still I dont have an "open" link when the d/l has finished

I tried <about:config> and typed download

there is a entry <browser.download.manager.openDelay> with a default integer of 0....does this need changing, if so to what?

---

### Post by coolbrook on 2007-06-04
It's not really good troubleshooting to solve your problem, but have you tried any Firefox extensions related to the download process?   One of them might produce the results you desire as well as provide more features and functionality.

[https://addons.mozilla.org/en-US/firefox/browse/type:1/cat:5](https://addons.mozilla.org/en-US/firefox/browse/type:1/cat:5)

---

### Post by Cypher on 2007-06-04
One of the extentions I use in relation to downloading is the "Download Statusbar", it puts all of your downloads in the statusbar and when it's done, you can just double-click it to open it or right click on the statusbar and shoose "Clear all finished" to just clear the bar..

---

### Post by coolbrook on 2007-06-04
I don't know what prompted me to install that one recently but I did.  I haven't used it yet but it's one of the popular ones.

---

### Post by ivesjd on 2007-06-04
You could try reinstalling firefox. I just downloaded something to check, (dont normally use firefox) and the open button is there. Im running firefox 2.0.0.4. That may or may not fix it. Hope it does though!

---

