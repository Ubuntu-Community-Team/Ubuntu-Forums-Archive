---
title: "[SOLVED] Remove the search dropdown firefox"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2008-03-30
How do I remove the drop down search button in firefox?

**Note** - I do not want to remove the entire search box - just the button which selects which search engine to use. I always use google and don't want the choice button there. 

[IMG]http://lh5.google.com/albertblack/R_AMdFGsCsI/AAAAAAAAAHo/GApR-pKLVVg/s800/Screenshot.png[/IMG]

---

### Post by annda on 2008-03-30
you can use the dropdown option "manage search engines" to remove everything except google, but the functionality is there to stay.

btw: i really like the screenshot

---

### Post by farueulogy on 2008-03-30
there has to be something I can do to the userchrome file or something to get rid of it - it's how I got rid of the drop down for the address bar.

anyone?

---

### Post by farueulogy on 2008-04-01
I made a trip over to the mozillazine forums and [got a solution]("http://forums.mozillazine.org/viewtopic.php?p=3320833#3320833") from a guy called bozz and it works great.

For firefox 2.0+

```
/* hide search type (google, yahoo etc) drop down */
.searchbar-engine-button {
display: none !important;
}
```

In [the mozillazine thread]("http://forums.mozillazine.org/viewtopic.php?p=3320833#3320833") it is also explained how to remove the google text label:

```
#searchbar[empty="true"] .textbox-input-box {
max-width: 0px !important;
}
```

---

### Post by farueulogy on 2008-04-01
This is what I've got going on (the address bar has been shortened to fit it in). It all seems to fit tango a lot better this way.

[IMG]http://lh3.google.co.uk/albertblack/R_IRoFGsCtI/AAAAAAAAAII/hwjI01r6Vgc/s800/Screenshot.png[/IMG]

---

