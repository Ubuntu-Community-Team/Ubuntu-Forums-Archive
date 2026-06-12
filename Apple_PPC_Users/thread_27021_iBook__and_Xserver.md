---
title: "iBook  and Xserver"
date: 2005-04-14
forum: Apple PPC Users
---

### Post by Gray Ghost on 2005-04-14
I've been trying to install hoary on my iBook and I've gotten  the installer to work correctly, but Xserve won't work right, I am presented with a command line, anyone know the commands to configure Xserver (X-org?)

---

### Post by erkki70 on 2005-04-15
hi,
Do you read sometimes replies from your previous posts?
Do you use sometimes the search engine on a specific forum such as the Ubuntu Macintosh/Apple/PPC Users?

Sorry I don't mean to be harsh but I don't quite understand how and why you can post again for the same issue when answers are given already and when using the search would 80% of the time put you on the right traks leading you to a working solution...

BTW, if you want people to help you it would be a good idea to be precise and to give as many details as you can.
[QUOTE=Gray Ghost]I've been trying to install hoary on my iBook and I've gotten  the installer to work correctly, but Xserve won't work right, I am presented with a command line, anyone know the commands to configure Xserver (X-org?)[/QUOTE]
This kind of post isn't replied to and silence speaks probably louder than my post, briefly it could be also answered like ```
man Xserver
```

Hope this helps.

Cheers,
Erkki

---

### Post by Gray Ghost on 2005-04-16
[QUOTE=erkki70]hi,
Do you read sometimes replies from your previous posts?
Do you use sometimes the search engine on a specific forum such as the Ubuntu Macintosh/Apple/PPC Users?

Sorry I don't mean to be harsh but I don't quite understand how and why you can post again for the same issue when answers are given already and when using the search would 80% of the time put you on the right traks leading you to a working solution...

BTW, if you want people to help you it would be a good idea to be precise and to give as many details as you can.

This kind of post isn't replied to and silence speaks probably louder than my post, briefly it could be also answered like ```
man Xserver
```

Hope this helps.

Cheers,
Erkki[/QUOTE]
 I've gotten to the xserver configuration screen ,but I don't know what i need to set all of the settings to...

---

### Post by chascon on 2005-04-19
You could look for a xorg,conf on the net for the model ibook you have.  You could use that to edit /etc/X11/xorg.conf
just
cntrl-F1
to get into console
log in 
then
 nano /etc/X11/xorg.conf
then
cntrl-o
to save.

If you mention what ibook it is someone might be kind enough to post their working xorg.conf
If you have to you might get away with a XF86Config-4 too.

Then waltz on over to the ibook and sleep string to enable sleep.

---

