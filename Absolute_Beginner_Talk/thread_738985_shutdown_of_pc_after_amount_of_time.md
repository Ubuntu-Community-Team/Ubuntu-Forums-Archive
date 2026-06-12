---
title: "shutdown of pc after amount of time"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by brdohman on 2008-03-29
I have put a line in my rc.local that shuts down the machine after 60 mins of usage, but would it be possible to add another line that will work with that one, that will either shut it down after 60 mins of usage or at a particular time?  say shutdown at 4:00pm?

thanks
Brandon

---

### Post by jken146 on 2008-03-29
```
shutdown -h +60
``` shuts the machine down in 60 mins' time.  I'm not entirely sure what you're asking though.

---

### Post by Inferied on 2008-03-29
And "shutdown -h 16:00" will shut it down in 4:00 pm. Other options are in "man shutdown".

---

### Post by brdohman on 2008-03-29
Ok thanks for the help.  I was looking for a way to shut it down at 4:00pm, and the second post answered that.  Sorry if my question wasnt' clear.

Also, is it possible to have both of those lines in a rc.local?

If so, will one rul out the other if it comes first?  Or can I only have the one line?

---

