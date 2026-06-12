---
title: "Javascript defaults to http in Firefox all of a sudden"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by samadams on 2007-06-06
For the past few days, any element that is normally set to execute a javascript command such as "save" instead will attempt to execute an [http://save/](http://save/) which of course is meaningless.  The browser then dumps the term "save" to google or it tells me it can't find the server "www.save.com"  This is true of any actionable javascript element.

Any ideas?

Note, Epiphany works fine - this is just in Firefox

I had this problem in Dapper and just last night upgraded to Fiesty hoping the problem might be fixed but it hasn't.

-Sam

p.s I'm using the live Edgy CD because my X just crashed trying to fix something else, but in the raw version - Firefox works fine.  My regular system has Sun Java 5.0 installed - could this be the problem?

**RESOLVED**

I suspected that since the problem was limited to Firefox, that perhaps an extension was the problem.  This was the case.  I had inadvertently selected my Split Link extension to auto-split.  Therefore Javascript codes were split down to their base commands with http:// prefixed to them.  I guess the Split Link add-on can't interpret script commands.

---

