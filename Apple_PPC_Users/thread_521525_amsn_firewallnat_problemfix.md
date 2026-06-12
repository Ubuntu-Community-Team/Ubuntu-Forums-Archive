---
title: "amsn firewall/nat problem/fix"
date: 2007-08-09
forum: Apple PPC Users
---

### Post by trash on 2007-08-09
I just installed amsn svn 9.7b and ended up with that crazy firewall/resticted ip crap, even though i have no firewall. I've had it before and a fix is always hard to find, since there is no mention of it in the amsn faq even though it seems to be a common and persistant problem, on mac anyway.
Here's the fix that worked for me... oh and i figured i'd post it here since the amsn forum seems difficult to search and find stuff... hope it's useful to somebody. OH and if you don't have the svn version yet GET IT!

The external IP is sent from the MSN servers. 

This configuration seems OK, maybe aMSN detects it incorrectly, the explanation is below. 

You can try overriding this configuration by pressing Ctrl+S in aMSN's main window to see the status log and typing:Code:

set ::abook::demographics(listening) true

After this, try a file transfer or webcam and see if you will be listening.

---

