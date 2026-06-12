---
title: "[SOLVED] chattr: Inappropriate ioctl for device - What's going on?"
date: 2006-06-29
forum: Apple PPC Users
---

### Post by RavenOfOdin on 2006-06-29
The thread title says it all.
When I try to execute:

```

sudo chattr +i /bin

```

or for that matter /sbin or /lib, those are the only directories I've tested it with yet, I get the message:

```

chattr: Inappropriate ioctl for device while reading flags on <dir>

```

What the heck is going on?!  I thought this was the correct way to execute the chattr command.  I've tried removing bad links from each directory in question but that doesn't work.

---

