---
title: "tip: if firefox eats your bookmarks"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2006-04-13
This is a tip, no need to reply :)

Using Firefox 1.5.0.1... I heard 1.5.0.2 was ready, so I started firefox with ```

sudo firefox --safe-mode

```to get the updates and install them. Well, there was no updates, so I opened firefox back with my own privileges. As it turns out, firefox ate / erased / lost my bookmarks. All, everything is gone. 

Good thing firefox backs up bookmarks. If this happens to you, close firefox and do the following:

```

cd
cp .mozilla/firefox/<manynumbers>.default/bookmarkbackups/bookmarks-<pickadate>.html .mozilla/firefox/<manynumbers>.default/bookmarks.html 
```

When unsure, double-tab (tab on your keyboard) to see what options/files are available for you to navigate / copy. 

<manynumbers>.default is the random number+characters assigned to your profile name by firefox. There will be only one <manynumbers>.default under ~/.mozilla/firefox unless you created a new profile(s). If so, well, do some trial and error ;) 

I guess firefox saves daily snapshots of your bookmarks. so you will pick a nice <pickadate>, which is up to you. You can always use diff (diff file1 file2) to see differences between files or open up the bookmarks-<somedate>.html in firefox or other browser. 

I didn't file a bug yet. Will do it if this happens again during an update.

---

