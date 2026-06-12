---
title: "Gconf-editor and urls"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-01
Hi
I'm using Gconf-Editor and its keybinding commands to create shortcuts for apps. 
This works great for apps but not so well for urls (at least, based on my limited Linux experience).
So, putting just the url into the EditKey Value box (as I can do with Winkey in XP) leads to an error.
To get the url to launch, I must prefix it with the path to the browser. While this works fine, it does lead to a second instance of the browser running (if it had already been running).
My preference would be for the new webpage to open as a new tab.
Anybody know how I can achieve this?

Thanks
Paul

---

### Post by aysiu on 2006-08-01
I don't really know whether this will work or not, but have you tried putting %s after the browser path? There seems to be on in System > Preferences > Preferred Applications after the mail client and browser of choice.

---

### Post by PaulFXH on 2006-08-01
Hi aysiu  
Thanks for your reply.
I saw the %s in the location to which you referred but could not get it to do anything at all for me despite a plethora of attempts in many combinations.

In other words, the path became unrecognizable after the insertion of %s and I ended up getting an error message to the same effect.
But it does seem to do something in some cases.
Maybe I'll find out one day.

Paul

---

### Post by Tomosaur on 2006-08-01
Which browser are you using?

---

### Post by aysiu on 2006-08-01
This isn't the ideal solution, of course, but some browsers allow you to have a single window mode. Firefox doesn't by default, but with the Tab Mix Plus extension, you can force everything to be a tab in one single window.

---

### Post by Tomosaur on 2006-08-01
To get this to work in firefox, use this command to launch a new tab when you already have firefox running:

```

firefox -a firefox http://www.blah.com

```

the -a command causes firefox to search for an already loaded process and launches a new tab from that, then passes it the url you give it.

Easy peasy :)

---

### Post by PaulFXH on 2006-08-01
Hi
Thanks to everybody for your replies.
However, I'm afraid I made a rather unforgivable error  :oops: 
When I tried Tomosaur's code and it came up in a new window (rather than the expected new tab) I became suspicious::-k . Then I checked in Edit->Preferences->Tabs in the box marked Open links from other applications in:
I had this set to New Window rather than New Tab.

When I corrected this setting, my own shortcut launched the new URL in a new tab which is what I wanted all along.

With apologies for my carelessness,
Paul

---

