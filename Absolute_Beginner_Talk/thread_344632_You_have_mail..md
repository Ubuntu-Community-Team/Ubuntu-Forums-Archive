---
title: "You have mail."
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Aberrix on 2007-01-23
I run an Ubuntu 6.06 LTS server, I administer it via ssh. I've installed pine also. every time I log in I get the message 'You have mail' however, when I go into pine and check... there is none? how can I clear this message and correct this? thanks!

---

### Post by Jussi01 on 2007-01-23
Have you checked your junk mail? I had a similar problem with a different app and it was reporting new junkmail as mail...

---

### Post by Aberrix on 2007-01-24
i think this is more referencing system mail.

---

### Post by j19sch on 2007-01-24
Try the command "mail'.
It's a very minimal program. Type '?' for help.
Unread messages might be displayed immediately. If not, type the number of the message and press enter (just start with '1' and work your way down if necessary). Typing 'q' and pressing enter quits.

Joep

---

### Post by Aberrix on 2007-01-24
mail is not installed, nor was it found on my apt-get repos...

I removed pine, then installed mutt (apt-get install) and checked a message and deleted it, then installed pine and then removed mutt... seems to be okay now, the new mail message is gone... but that sure was weird?

---

