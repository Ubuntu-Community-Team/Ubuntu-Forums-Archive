---
title: "Forbidden"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by laughinglizard on 2008-03-06
I have just finished an install of Ubuntu 7.1 Lamp Server and Gnome desktop, and everything was going smoothly.  Created a new site in /home/me/public_html, copied the configuration file for the default site and modified for me. Wrote a simple index.html file, saved it, tested fine across the lan and localhost. Installed phpmyadmin and configured a cgi-bin directory, still worked fine.  Replaced the index.html with another plus an image folder and now get "Forbidden, You do not have permission to access index.html"

If I clear the folder and just put one index file in it all is well, but the moment I add anything to the folder I get the above error.  I am tearing my hair out here.  Any ideas?

Did I mention I am a Linux noob, but I learn fast.

Any help appreciated!

Kind regards,
LL

---

### Post by elvisd on 2008-03-06
Have you checked file permissions? Maybe the new index.html isn't accessible/readable to the web server.
Try comparing both files (right-click, properties and che in the permissions tab)

Hope this helps.

elvisd

---

### Post by laughinglizard on 2008-03-06
Thank you [COLOR="Blue"]elvisd[/COLOR]!

I had it figured that it was a permission thing, just didn't know where to set them.

All is well, thanks again.

LL

---

