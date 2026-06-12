---
title: "browsing history in dropdown window in firefox 3 b does not erase"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Michl on 2008-03-29
In Firefox 3 beta I seem to have a problem.  Clearing
the private data does not clear all the browsing history
in the dropdown window.  I'm not sure what principle
is being used because recent pages I browsed
are erased, but others are not.

---

### Post by FreewareFan on 2008-03-29
I can confirm this in Swiftweasel 3 beta 4.5 also.   Very odd indeed....

---

### Post by Michl on 2008-03-31
Does anyone else have this problem?  I'm thinking of launching
a bug report;

---

### Post by Michl on 2008-04-13
ANyone concerned with this see this thread:

[http://ubuntuforums.org/showthread.php?p=4712049#post4712049](http://ubuntuforums.org/showthread.php?p=4712049#post4712049)

---

### Post by Chaparrito29 on 2008-07-13
you can use this solution....it works for me

write about:config in the url window
it will show a warning message....just press the button "I'll promise"..
in the filter window write browser.urlbar
look for the line browser.urlbar.maxRichResults and change the value to 0
in the line browser.urlbar.matchOnlyTyped change the value to true

The default value to the rich results in the url bar is 12, setting it to 0 will show nothing on it.
The other change instruct the browser to only show lines like the one you're typing.

That's the way I resolve this  little puzzle in my new Firefox 3 browser.

have a good one

---

### Post by Michl on 2008-07-23
> **Chaparrito29 said:**
> you can use this solution....it works for me

write about:config in the url window
it will show a warning message....just press the button "I'll promise"..
in the filter window write browser.urlbar
look for the line browser.urlbar.maxRichResults and change the value to 0
in the line browser.urlbar.matchOnlyTyped change the value to true

The default value to the rich results in the url bar is 12, setting it to 0 will show nothing on it.
The other change instruct the browser to only show lines like the one you're typing.

That's the way I resolve this  little puzzle in my new Firefox 3 browser.

have a good one

The link mentioned in a previous note in this thread discusses this
solution.  There are a number of problems with it. One is that it
is a kludge and the other is that if you return about:config b ack to
12 all the old addresses still show up.  So it doesn't really clear the
history.

---

