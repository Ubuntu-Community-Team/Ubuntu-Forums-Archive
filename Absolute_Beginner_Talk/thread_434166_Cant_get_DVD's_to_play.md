---
title: "Cant get DVD's to play"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Buggy on 2007-05-05
Hi all.
I'm trying to get DVD's to play using Totem.  I'm getting an error that says 
"Could not open location. You may not have permission to open the file."

Why wouldn't I have permission to play a DVD?  And how can I correct this?
Thanks.

---

### Post by [ajax] on 2007-05-05
I think you need to install DVD playback capability.  It isn't included by default because of legality issues, as the format is proprietary.  Here's the easy fix:

1. Download and install Automantix
[http://www.getautomatix.com/](http://www.getautomatix.com/)

2. Run Automatix. Under "Codecs and Plugins" select "AUD-DVD Codecs"

...lots of cool stuff in Automatix...

---

### Post by SectionThree on 2007-05-05
Totem won't do much, so you want to get Ogle for your DVD needs. Before you can do that though, you need to enable all of the software repositories (Ubuntu is set by default to only use the strictest open-source software).

So, in Synaptic you want to choose Repositories from the Settings menu. Open the Ubuntu Software tab and check all of the boxes (Ogle is in the Universe Repository). Hit OK.

Now you can install a package called ogle-gui.

---

