---
title: "[SOLVED] how do I retrieve bookmarks from hard disk?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-11-08
My old hard disk refused to boot (I've always had problems with the thing - cable or whatever - that connects it to the rest) so I got a new hard disk.
I can handle the rest of the stuff, like transferring data to the new one etc. But is there any possible way to retrieve my firefox bookmarks? I've bookmarked lots of important and interesting stuff so it would be enough if I could just even see the urls.
Please do help. Thanks.

---

### Post by edm1 on 2007-11-08
they should be in somewhere similar to ~/.mozilla/firefox/6n4k96uo.default/bookmarks.html

---

### Post by crf on 2007-11-08
You'll have to attach your old hard disk to the computer, and it may automount, so that you can see it in the file browser.

Then you'll need to find your bookmark file on your old hard drive. If the hard drive was another linux filesystem, then look in the home directory, and it may be in the profile folder under .mozilla or .netscape or .firefox, or something like that I guess.

If the hard drive held windows, then it depends on your windows version and how you set it up. But mozillazine.org has a knowledge base article on how to find your profile folder. Read it :) .

I think the bookmarks are called bookmarks.html or bookmarks.bak.

---

### Post by kleo skywalker on 2008-01-09
My disk was damaged, I just got my data back and found the bookmarks. Thanks!

---

