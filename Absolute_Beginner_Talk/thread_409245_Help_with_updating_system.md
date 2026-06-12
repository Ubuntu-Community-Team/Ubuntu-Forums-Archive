---
title: "Help with updating system"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by sombster on 2007-04-14
I just installed Ubuntu, and I've got it pretty much the way I want it, however, theres a specific version of Scrollz (irc client) that I want installed. I managed to get it installed, however when I try to update, it wants to upgrade to 1.9.9 (I don't want/like/need this version).

How can I force it to not even attempt to update Scrollz. I have 1.9.5-2 or something right now, and I'd like to keep that version.

I have no idea what I need to search for, to even get started on a resolution, so maybe someone can lead me in the right direction?

Thanks!

---

### Post by raja on 2007-04-14
You can select the package in synaptic and choose lock version from the menu.

---

### Post by sombster on 2007-04-14
Sweet, thanks. That fixed PART of the problem.

Now when I run apt-get upgrade though, it still wants to install the newer version. Is there somewhere I can set it to prevent that as well?

Thanks.

---

### Post by raja on 2007-04-14
Have a look at ```
man apt_preferences
```, I think the answer may be there. However, I am not sure.

---

### Post by sombster on 2007-04-14
Trying it like this;

Package: scrollz
Pin: 1.9.5*
Priority: 1001

Still wants to upgrade to 1.9.9, and it will in fact do it, if I let it.

---

