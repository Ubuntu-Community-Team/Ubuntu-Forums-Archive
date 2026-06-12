---
title: "[SOLVED] problems with restricted drivers 7.10"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by mitchlourens on 2007-10-20
I'm trying to get my Nvidia Legacy drivers to work, but when I click on the checkbox to enable them, I get the message:
 "The software source for the package

   nvidia-glx-legacy

 is not enabled."

This is a fresh installation of Ubuntu and its my favorite OS by far, I'm just putting it on the fairly old PC for the first time and I want to know if it will work.  Is there a missing repository or something?

---

### Post by Pumalite on 2007-10-20
Try with this command:
sudo apt-get install nvidia-glx-legacy
Or download and install from here:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by mitchlourens on 2007-10-20
> **Pumalite said:**
> Try with this command:
sudo apt-get install nvidia-glx-legacy
The problem was in the Repositories.  I went to Software Sources, and every single box was left unchecked (how it was like this, I don't know).   I've checked off every one that I want, and now everything is back to normal!

---

### Post by dhruva023 on 2007-10-20
open synaptic. ( system >> Asministration >> Synaptic Packge Manager )

click on search

and type

"nvidia-glx-legacy"

then select it, and click on apply.

then try to enable the driver again.

---

### Post by mitchlourens on 2007-10-20
Well, i did goto synaptic at first, but it wouldn't download anything due to the fact that the repositories weren't existent.  Thanks for the quick help though!  I really love the Ubuntu system and community.

---

