---
title: "[SOLVED] Firefox missing &amp;quot;function indicator&amp;quot; boxes"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by bhold on 2007-11-30
I lack expertise with web / browser terminology but will explain this best I can.

On a bulletin board I occasionally post to - there are icons for "edit post", "delete post", etc. If I hover the cursor over the icon, a little indicator box appears displaying the functionality I will get if I click the icon. This is very useful and works on XP with IE6.

Using Firefox on Ubuntu 7.10 I don't get this little indicator but would like to. Is this a problem with my Firefox settings or an IE/Windows only type of thing?

---

### Post by felicity on 2007-11-30
I can verify that the pop-up informational boxes work in my 7.10 gutsy installation with Firefox 2.0.0.10. I'm not sure why yours aren't working though..

---

### Post by bhold on 2007-11-30
I can see this information with:
ctl-right-click
properties

The "Alternate text" property shows what function the click will provide at the web site I was having problems with..

So I googled on this a little and found:
1. There are some standards conflicts between whether "Alternate text" or "Title" property is the correct place for web developers to stash this information.
2. Different browsers handle it differently. Mozilla seems not to support "Alternate text" but there might be a plugin available to provide it.
3. On this forum - which uses the "Title" property - Firefox correctly displays the informational popup box.

---

