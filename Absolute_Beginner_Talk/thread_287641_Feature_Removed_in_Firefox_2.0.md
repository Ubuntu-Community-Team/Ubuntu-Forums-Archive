---
title: "Feature Removed in Firefox 2.0?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by doctorberen on 2006-10-29
Hello guys.

I'm having a problem in Firefox 2.0. When I click on some links, a new browser window opens. 

I can't seem to configure Firefox to open links in new tabs instead of opening a new instance of the browser. 

In Firefox 1.5, there was an option to force links to open into a new tab, but this feature suddenly disappeared in Firefox 2.0.

Does anyone know what's going on? Does anyone know how to fix this?

---

### Post by willy1234x1 on 2006-10-29
I don't know what you're talking about go to edit then preferences then tabs and select new pages load in a new tab so

open firefox>edit>preference>tabs>open in a new tab

---

### Post by doctorberen on 2006-10-29
willy1234x1

I tried that but some links would open in a new browser window instead of a new tab.

---

### Post by yabbadabbadont on 2006-10-29
I don't know if it has been ported to 2.0 yet, but if it has, you might try using the Tab Mix Plus extension.  It has an option to force single window mode.

---

### Post by willy1234x1 on 2006-10-29
no it hasn't been updated to firefox 2.0 quite yet so follow those instructions I put up it's worked for me

---

### Post by yabbadabbadont on 2006-10-29
Found [this](http://forums.mozillazine.org/viewtopic.php?t=459600&highlight=single+window+mode&sid=62aab4c8bf44c77bce49c987b13dfbd9) at the Mozillazine site.  You have to alter an about:config setting to stop JS popups from opening new windows.  The Preferencs setting only affects regular links that open new windows.

---

### Post by Russty of Oz on 2006-10-29
> **yabbadabbadont said:**
> Found [this](http://forums.mozillazine.org/viewtopic.php?t=459600&highlight=single+window+mode&sid=62aab4c8bf44c77bce49c987b13dfbd9) at the Mozillazine site.  You have to alter an about:config setting to stop JS popups from opening new windows.  The Preferencs setting only affects regular links that open new windows.

I too am having the same problem, it only seem to be with Ubuntu as FF 2.0 on windows behaves normally.  I tried the above about:config thing and now some links on pages open in the **same **tab rather than a new one and some other links still open a new window.  I have the preferences set to open links in a new tab but something is overriding it.

---

### Post by doctorberen on 2006-10-29
Thanks for the link, yabbadabbadont.

That link led to [another]("http://kb.mozillazine.org/Browser.link.open_newwindow.restriction").

Reading through it, I modified **about:config** as follows:
[INDENT]browser.link.open_newwindow   3
browser.link.open_newwindow.restriction   0[/INDENT]

This solved my problem. I wonder if mozilla intentionally did this or if this is a bug. Because now, if you want links to open up in a new tab, you would have to do some geeky stuff. Whereas in IE7, clicking the feature will automatically open links in a new tab and not a new window.

---

### Post by esaym on 2006-10-29
kinda same thing here.  I don't use tabs and yet some open in tabs and others in a new window ...

---

### Post by Russty of Oz on 2006-10-29
Yes, it looks like the 3 and the 0 fixes it.   :)

---

