---
title: "Remember position of windows and Firefox?"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by dugh on 2007-07-03
How can you get Ubuntu to remember the positions of windows like Firefox and Thunderbird?

Also possibly have it re-open folders when you login that were open in your last login.  I know there is a "save session" option, but that is more like putting your computer to sleep it seems.

Instructions I've seen don't work (there is no "advanced settings" option when you click a folder window now):
[http://ubuntuforums.org/archive/index.php/t-36505.html%3C/t-199815.html](http://ubuntuforums.org/archive/index.php/t-36505.html%3C/t-199815.html)

---

### Post by Juan_VCS on 2007-07-03
You could try [Devil's Pie](http://www.burtonini.com/blog/computers/devilspie)

---

### Post by dugh on 2007-07-05
Is there not a bugzilla # for this over at mozilla.  I'm surprised such a basic feature is missing (window position is remembered in windows with firefox).

You can't get more basic than saving the position of a window before exiting.

onclose
    save_window_position()

onopen
    load_window_position()
    set_window_position()

---

### Post by dugh on 2007-07-05
Apparently this is a mozilla bug that hasn't been fixed in 6 years:
[https://bugzilla.mozilla.org/show_bug.cgi?id=71402](https://bugzilla.mozilla.org/show_bug.cgi?id=71402)

Actually they are saying it is gnome's fault, since "unix types seem to prefer that Mozilla not override the window positioning provided by their window managers":
[https://bugzilla.mozilla.org/show_bug.cgi?id=31086](https://bugzilla.mozilla.org/show_bug.cgi?id=31086)

And I cannot find this "advanced preferences" that someone mentioned in another forum for having gnome remember window positions.  Right clicking on a title bar does show this preference.

---

### Post by dugh on 2007-07-05
Apparently the Ubuntu team fixed this in early Feb., but I am seeing it in Feisty which wasn't released until April:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/65841](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/65841)

---

