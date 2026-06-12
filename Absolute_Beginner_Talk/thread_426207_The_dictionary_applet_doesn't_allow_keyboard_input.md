---
title: "The dictionary applet doesn't allow keyboard input."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Esben Kramer on 2007-04-28
I experienced this in Edgy. It's still a problem in Feisty, it seems. Anybody else have this?  It's impossible to enter a word in the dictionary (the that can be put on the panel).

---

### Post by sagara on 2008-02-23
I have the exact same problem and I am using Gutsy.  The dicitonary applet wont take any text.  According to this bug tracking post in launchpad this was already fixed for gutsy as a backport.  Need to find where to get it.

More info: [https://bugs.launchpad.net/ubuntu/+source/etoile/+bug/175151]("https://bugs.launchpad.net/ubuntu/+source/etoile/+bug/175151")

---

### Post by sagara on 2008-02-24
For **Gutsy** it turns out that compiz fusion (the composite desktop) is at fault.  A bug in compiz prevents you from typing into the dictionary applet.

A fix addressing this issue was release as a backport for **Gutsy**.  To install it simply go to

(1) System->Administration->Software Sources

      Click on the Updates tab, make sure "Unsupported updates (gutsy-backports)" is enabled

(2) in a terminal window type [FONT="Courier New"]sudo apt-get update[/FONT]

(3) In a few minutes, the "updates is available" icon should appear, install all updates and reboot.

(4) Your dictionary applet should now work  =D

---

