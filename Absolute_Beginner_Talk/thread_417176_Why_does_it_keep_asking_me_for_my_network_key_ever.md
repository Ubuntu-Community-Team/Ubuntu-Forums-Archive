---
title: "Why does it keep asking me for my network key everytime I start Ubuntu?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by diargasm on 2007-04-21
Is there anyway to make it accept my settings and store it?  I never had this problem with 6.10.  Every time I log on to Ubuntu it makes me want to add a keyring and put in my network key.  Also, I can't mute my volume. I can make it show that its mute, but there is still sound coming through.  Thanks for help in advance.

---

### Post by Kobalt on 2007-04-21
Install the package *libpam-keyring* with Synaptic and then edit this file : ```
gksu gedit /etc/pam.d/gdm
``` 
Add this line at the end of the file then save and close : 
> @include common-pamkeyring

That should do it for your keyring problem...

---

