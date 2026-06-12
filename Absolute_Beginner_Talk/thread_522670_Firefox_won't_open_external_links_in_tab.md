---
title: "Firefox won't open external links in tab"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-08-10
On my mac, in firefox, when I click on a link that would normally open in a new window, it gets opened in a new tab instead. I didn't set this, it was the default. I would like this in ubuntu too. But, using firefox in ubuntu doesn't do this. I've checked to see if all the options were the same from "new pages should be opened in a new tab" in the preferences to "about:config." I can't seem to find what setting would produce the same results. Does anyone know what I'm overlooking?

---

### Post by p_quarles on 2007-08-10
You can install this extension:
[https://addons.mozilla.org/en-US/firefox/addon/1122](https://addons.mozilla.org/en-US/firefox/addon/1122)

Then, you can configure it to open everything in new tabs.

---

### Post by cjnkns on 2007-08-10
Just curious, but why do we need this extension?
I mean all external links in firefox open in tabs on windows? Why not ubuntu/linux?

---

### Post by arijarot on 2007-08-10
> **p_quarles said:**
> You can install this extension:
[https://addons.mozilla.org/en-US/firefox/addon/1122](https://addons.mozilla.org/en-US/firefox/addon/1122)

Then, you can configure it to open everything in new tabs.

Thank you for the suggestion, but I'd like to know what firefox option does this...

---

### Post by arijarot on 2007-08-10
> **cjnkns said:**
> Just curious, but why do we need this extension?
I mean all external links in firefox open in tabs on windows? Why not ubuntu/linux?

so, firefox had the same config in windows too? :-k then, it figures that it must be a configurable  option in firefox, right?

---

### Post by p_quarles on 2007-08-10
> **arijarot said:**
> Thank you for the suggestion, but I'd like to know what firefox option does this...
Sorry. I thought you wanted a solution. If you want an explanation, you should go to the developer's forums.

---

### Post by original_jamingrit on 2007-08-10
If you want to do some fiddling around it's the best way to learn.

check out your preferences on a file by opening your terminal, and entering:```
cd //usr/share/firefox/defaults/pref
gksudo gedit firefox.js
```

Then look at lines 236-240.  It should explain it.  Just be careful not to do any unnecessary editing in that file.

---

### Post by Dgurion on 2007-08-10
I think this is what you wanted. As posted in another post:

> **6StringKng said:**
> create a new tab, enter about:config in the url bar, hit enter, search for this "browser.link.open_newwindow" and change its value to 3 and should work...sorry if someone posted this, didn't want to read all of that, lmao.

Now all links that want to open as new windows will open inside a tab instead.

---

### Post by arijarot on 2007-08-11
> **Dgurion said:**
> I think this is what you wanted. As posted in another post:



Now all links that want to open as new windows will open inside a tab instead.

This worked perfectly and was the easiest method, thanks.

Thanks everyone for the alternative methods too:)

---

