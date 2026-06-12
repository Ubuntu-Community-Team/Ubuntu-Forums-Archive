---
title: "Where are the Firefox bookmarks?"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2006-10-14
I've decided to wipe the laptop and reinstall Ubuntu from scratch, since I've manged to mess around so thoroughly with things I don't understand that I now have difficulties getting it to even boot. Sometimes it works, sometimes it doesn't....

Before I do that though, I want to make sure everything important is backed up, and among those important things are my Firefox bookmarks. Frustratingly, I can't find them. Would somebody mind telling me where that file is, so I can copy it to my USB harddrive?

Thanks,
Mimsy

---

### Post by taurus on 2006-10-14
It shoud be in ~/.mozilla/firefox/4f0rc89r.default (or whatever the numbers and letters in front of .default)...

---

### Post by crazymonkey on 2006-10-14
You can also export them using the Bookmark Manager

Bookmarks > Manage Bookmarks
then
File > Export...

It will make a html file out of your bookmarks which you can reimport on your fresh install following the same procedure but choosing Import...

---

### Post by Mimsy on 2006-10-14
Thank you, I shall go look for it. :)

While I was digging around, I came across the file /etc/firefox/profile/bookmarks.html

That's not it then?

---

### Post by taurus on 2006-10-14
That's a generic bookmarks.  Your personal bookmark is in ~/.mozilla/firefox/<letters_numbers>.default.  If you don't believe me, look at both of them and you will see...

```

more /etc/firefox/profile/bookmarks.html
more ~/.mozilla/firefox/<letters_numbers>.defaults/bookmarks.html

```

---

### Post by Mimsy on 2006-10-14
Never mind. Crazymonkey must have posted while I was still typing up my post. The Bookmark Manager method looks really quick and easy and painless. I'll try that one, since i'm in Firefox already anyway. :)

Thanks again.

/Mimsy

---

### Post by Mimsy on 2006-10-14
> **taurus said:**
> That's a generic bookmarks.  Your personal bookmark is in ~/.mozilla/firefox/<letters_numbers>.default.  If you don't believe me, look at both of them and you will see...

```

more /etc/firefox/profile/bookmarks.html
more ~/.mozilla/firefox/<letters_numbers>.defaults/bookmarks.html

```

Oh, I believe you. I just want to be sure that I back up the right file, so I won't lose anything important. :)

I'm a big believer in the "measure twice, cut once" method.

/Mimsy

Edit:
And now I've cut twice. Bookmarks have been exported, and the bookmarks.html file that taurus pointed me to has been copied over to the USB hard drive as well. Not that I'm paranoid or anything... :) Now off to format and reinstall. Wohoo. Great way to spend a weekend!

---

### Post by SnackySmores on 2006-10-14
you might wanna try the foxmarks extension, I use it to sync my windows & my linux bookmarks :mrgreen:

---

