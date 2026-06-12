---
title: "How can I speed up boot?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-04-08
For some reason things don't seem to be booting up as fast as they used to...

I'm not sure what is going on. I've posted my bootchart and help or advise would greatly be appreciated.

The really weird thing is that after I login I have to wait 20-25 seconds before the desktop appears (it just sits on a brown background)

---

### Post by Tatty on 2008-04-08
Annoyingly bootcharts only go up to the GDM screen, yours looks fine as far as that goes.

Unfortunately it has been a common complaint with Gutsy Gibbon that it can seem to twiddle its thumbs for a few momoments after logging in.  It certainly affects both of my ubuntu machines.

However, 20-25 seconds does seem like a bit too much... two things spring to mind to check:

1. Have you recently installed anything that might be loading on boot?
2. How full is your hard drive?  (if it is over 80% then it might be fragmenting)
3. Try disabling any services you dont need in System->Administration->Servicess

A lot of threads which discuss the slow booting after the GDM suggest that it might be something to do with the Network Manager.  Perhaps it might be worth uninstalling network manager and see if that helps at all.


Sorry I know its not much help, and looking at your post count I imagine you know enough to have checked most of these things already.  But I thought its worth trying to eliminate the more obvious first.  :)

---

