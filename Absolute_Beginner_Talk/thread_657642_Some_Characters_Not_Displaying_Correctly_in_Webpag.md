---
title: "Some Characters Not Displaying Correctly in Webpages/Documents"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by LordKelvan on 2008-01-03
Hi:

I have what I think is a font problem, as there are many characters which show up as a square with 4 circles inside: 

[IMG]http://img295.imageshack.us/img295/5440/screenshotgooglereaderkn1.png[/IMG]

The above picture is a screenshot which I took of my Google Reader page.  What I want to know is how do I go about fixing this issue.  The following are my font settings for Firefox:

Proportional: Sans Serif (Size 14)
Serif: Times New Roman
Sans-serif: sans-serif
Monospace: monospace (Size 16)
Minimum font size: None
Default Character Enconding: Western (ISO-8859-15).
Allow pages to choose their own fonts, instead of my selections above.

These settings should be the same as my Windows install (which shows the pages correctly), because I used an extension to back-up my Windows Firefox profile and overwrite my Ubuntu Firefox Profile when I switched over from Windows to Ubuntu.  Can someone help me out?

Cheers,
LK

---

### Post by steve8track on 2008-01-04
I would just guess that you don't have Unicode installed.

I would make sure you have libgucharmap6 installed, as well as libicu36 or any other possibly relevant Unicode installations (I just searched Unicode in Synaptic).

My other thought is maybe firefox is now set to use some font that isn't fully supported in Ubuntu (since you imported settings), so try changing the settings.  My firefox is set to Unicode instead of Western, and my autodetect is off.

As a LAST RESORT (though you WILL loose ALL of your bookmarks, settings, plugins, saved passwords, cookies, etc), you can remove firefox completely with a command something like this:

```
sudo apt-get remove --purge firefox
```

DON'T do that unless you want to start firefox from scratch.

I hope this helps

---

### Post by LordKelvan on 2008-01-04
Hi:

steve8trac: 
Thanks for replying.  I checked, and I have both libgucharmap6 and libicu36 installed.  I changed my default character encoding to Unicode (UTF-8), but it doesn't help either.  I have also created a blank new profile, just to make sure it wasn't some settings issue, and I can still see the problem.
I was wondering if you could do me a huge favour: could you subscribe to the HardOCP RSS feed?  Just browse through it, and tell me if you see those weird symbols as well.  If you don't, maybe I could change my font settings to completely match yours and see if that helps.

---

### Post by LordKelvan on 2008-01-19
Hi:

I have done a bit more investigating and and checked out the actual RSS feed (i.e., the XML file) and I saw that in the places where the weird symbols were showing up, there was either the string "&#63" or "&#146;" (note: the quotation marks aren't part of the string).

So for example, if I was looking at Google Reader, and a particular line says "Sprint[funny symbol]s new CEO is making major cuts to help the company ", then that same line in the actual XML file of the RSS feed would say "Sprint&#146;s new CEO is making major cuts to help the company".

Does anyone have any ideas now?

Cheers,
LK

---

### Post by steve8track on 2008-04-06
hmm, sorry for the late reply.  I don't see any wierd characters in the RSS feed myself, but I could have the wrong feed, since that site seems to have quite a few RSS choices.  I just used Firefox 2's RSS reader.

---

