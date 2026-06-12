---
title: "'Generate package download script' in Synaptic Package Manager..."
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by akiratheoni on 2007-10-28
How does this work? I'm thinking of re-installing because Compiz-Fusion is broken right now. (Of course I'm going to back up everything)
 
I'm thinking this would be an easy way to re-install all of my programs, but when I generate the script, it doesn't seem like it does anything.

How do I actually use it? Selecting 'Add downloaded packages' doesn't work.

---

### Post by caffienefree on 2007-10-28
Would [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) help you with what you're trying to accomplish?

Yes, I see what you mean... it creates a shell script with only #!/bin/sh. This can't be expected behaviour...

---

### Post by peterquistgard on 2008-02-13
"Package download script" is used in order to download packages on a non networked system. If you select a few packages to be installed using Synaptic, then create a download script, the script will not be empty. 

In this case the script can be run on any suitable (Linux) system with a decent connection. It will download all the necessary files, which can then be transported back to the non networked system for installation. To install them, go to File->Add Downloaded Packages.

---

