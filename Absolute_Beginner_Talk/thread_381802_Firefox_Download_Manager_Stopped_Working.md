---
title: "Firefox Download Manager Stopped Working"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by cneil on 2007-03-11
Hello,
My Firefox download manager seems to have stopped working.  I can no longer click and download files and the right click method doesn't seem to work either. When I go to Edit>Preferences>Download everything seems fine, but when I go to Tool>Downloads it is always blank and there is no information.
I have both Firefox and Switfox installed and the problem is on both programs.  Also, just to note, Mozilla still works fine too.  Does anyone have any idea about what could have happened?
Thanks

---

### Post by steve.horsley on 2007-03-11
I have no idea. But it must be something in your home directory. You could try renaming .mozilla so Firefox can't find its setings when you start it. See if it works then.

---

### Post by Najand on 2007-03-11
> **cneil said:**
> Hello,
My Firefox download manager seems to have stopped working.  I can no longer click and download files and the right click method doesn't seem to work either. When I go to Edit>Preferences>Download everything seems fine, but when I go to Tool>Downloads it is always blank and there is no information.
I have both Firefox and Switfox installed and the problem is on both programs.  Also, just to note, Mozilla still works fine too.  Does anyone have any idea about what could have happened?
Thanks

Maybe you should reinstall firefox.
```

sudo aptitude reinstall firefox

```

---

### Post by msak007 on 2007-03-11
Before deleting the .mozilla folder or reinstalling Firefox, you can attempt to create a new default profile to see if it's your profile that's corrupt (possibly an extension that messed it up, it's happened to me before). Close out of Firefox, and from the terminal type the following:

```
firefox -ProfileManager
```You'll get a box with your profile (most likely named "Default"), so you'll want to create a new profile and call it something like "Test". Try using that profile to download a file and see if it works. Here's the Mozilla page on managing profiles for reference:

[http://www.mozilla.org/support/firefox/profile](http://www.mozilla.org/support/firefox/profile)

---

### Post by darkeale on 2007-03-11
yeah just make a new profile. i had the same problem

---

