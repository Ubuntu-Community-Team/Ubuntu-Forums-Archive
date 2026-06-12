---
title: "Compiz Installation, cgwd"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-09-17
From the Compiz Installation Walkthrough:
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)
> **In the scripts or session modifcations you have made in earlier parts of the walkthrough, change gnome-window-decorator to cgwd.** To apply themes run gcompizthemer either from your preferences menu or from a terminal. Also please note cgwd uses an .ini file, not the gconf keys used by gnome-window-decorator, so you must use gcompizthemer to apply themes as setting gconf keys will not work.
Where is this and how do I change it?

---

### Post by bulldog on 2006-09-17
When you have all setup and you have the repo's enabled you should install

sudo aptitude install cgwd cgwd-themes cgwd-themes-extra

And the latest compiz works with csm.

needed repo's:

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

Put this to your sources.list and

sudo aptitude update

Now you can install the latest compiz packages like csm and cgwd etc.

Go to your sessions and remove everything what points to compiz like compiz-start or compiz-start.py or the future.

Put /usr/bin/compiz-start in your sessions menu and logout and login.

Now you should have in preferences two new Icons,Compiz Settings Manager and CGWD Themer.

---

### Post by alex-desktop79 on 2006-09-17
All that is done, but CGWD Themer simply does not install the themes I tell it to, I asked how to change that line in the first post.

oh, wait, I wasnt in xgl. brb

---

### Post by bulldog on 2006-09-17
Gcompizthemer is replaced by cgwd-themer so you haven't to change that anymore.

If you installed csm you can remove gsetcompiz as well if installed,it's all out of use now.

Go into synaptic and do a search for cgwd.
If you have update synaptic you should see at least three entry's.

cgwd----cgwd-themes----cgwd-themes-extra.

Also should csm be there if you do a search.

---

