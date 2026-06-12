---
title: "Going crazy... Connection problem..."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Ozcu on 2007-09-02
Its driving me insane, like 2 weeks of trying to get Ubuntu working correctly. Yet no web connection working

So... I run in terminal: sudo dpkg-reconfigure dchp3-server
And it says that its not installed and no info is avaible. 

What should I do? Also when i plug the internet cable, the boxses light doesn't show... I hope you understood what I meant

Any help?

---

### Post by jamvegan on 2007-09-02
Hm.  I see a couple of potential problems.  First, if that is exactly how you are trying to run the command, then your problem may just be a typo.  It's dhcp, not dchp.  I'm also wondering if you're really wanting to run a server?  If you're just trying to get a computer to connect to an existing network, then you need dhcp3-client, but not dhcp3-server.

Hope this helps. :-)

---

