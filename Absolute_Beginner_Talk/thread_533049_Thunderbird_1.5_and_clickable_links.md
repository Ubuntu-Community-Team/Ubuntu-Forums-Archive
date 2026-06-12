---
title: "Thunderbird 1.5 and clickable links"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by dndrich on 2007-08-23
I installed Feisty for Grandma on her old Dell machine.  Really works well.  I have her using software in the repositories so she doesn't have to do any updating herself.  So she is using Thunderbird 1.5 for email, and Firefox for browsing.  Now, when Thunderbird email receives an email with a clickable link to a web page, it does not fire up Firefox.  Nothing happens.  If Firefox is running, then it brings up another tab like it is supposed to.  I am using Feisty, but am using Thunderbird 2.006.  It works fine for me.  So why does Thunderbird 1.5 not fire up Firefox?  Is there some way to fix that?

Daniel

---

### Post by alienexplorers on 2007-08-23
In system>preferences>prefered applications do you have firefox listed as the default driver.  This works in Ubuntu 6.06, not sure how it works in other versions.

---

### Post by por100pre1 on 2007-08-23
> **alienexplorers said:**
> In system>preferences>prefered applications do you have firefox listed as the default driver.  This works in Ubuntu 6.06, not sure how it works in other versions.

Works the same in Feisty. Be sure to use this command for Firefox:

```
/usr/lib/firefox/firefox "%s"
```

---

