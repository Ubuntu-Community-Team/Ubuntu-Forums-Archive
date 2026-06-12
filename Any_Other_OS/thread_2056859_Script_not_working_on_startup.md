---
title: "Script not working on startup"
date: 2012-09-12
forum: Any Other OS
---

### Post by elemenophee on 2012-09-12
I just changed from Ubuntu to Debian Testing. Actually I have everything configured but I'm facing this problem..

In Ubuntu with the "Applications on startup" (don't know the right name because I don't use the english version) I wrote the command of the script and it worked perfect.

Now in Debian there isn't any interface for do it so I have to do it manually. I have created the script and put it in /etc/init.d/, then I executed update-rc.d scriptname defaults and checked that there is a symlink in each /etc/rcX.d/ directory. 

But when I start the system the script isn't loaded... However the script is fine because if I run it, it works perfect. The only problem is that it isn't loaded on startup.


edit: finally I got it! Using gnome-session-properties

---

