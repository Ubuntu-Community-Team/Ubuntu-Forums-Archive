---
title: "Black Screen on startup - my fault"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by craigyjack on 2007-03-26
Hi,
Well I know this is totally my fault and I will be prob be a total noob forever now. But I deleted some packages from the synaptic package manager and now after the login screen I just get a black screen with the cursor on it.

I don't know really what I deleted now. Sorry for being a total noob.

Is there anyway that I can load back in the default packages from the install so I can get my GUI back up and working. I know I shouldnt have been messing around where I was and I am going to be staying out of there until I'm more experienced. I can go into recovery mode and insert commands and it seems X server is loading, but just a black screen then plus the cursor.

I hope there is some way I can save my GUI.

Thanks,
Craig

---

### Post by jbayone on 2007-03-26
reboot in safe mode then type ```
sudo dpkg-reconfigure xserver-xorg
``` you can first try the vesa driver when prompted to select the type of video card you have.  after all of that ```
sudo /etc/init.d/gdm start
```

---

### Post by craigyjack on 2007-03-26
I did what you said. Still a black screen.
I configured it with vesa and nv (the nv video drivers is what i was using).
Neither way worked....

EDIT: SOLVED
I reinstalled the gnome desktop (sudo aptitude install ubuntu-desktop) and it works now. I was pretty sure I deleted a gnome package or two and this makes me think I did. I shall not be messing with synaptic package manager unless I really know what I am doing from now on. I didn't know how to reinstall the DE but I found the command and thought I'd try it. So it's all fixed now, thread can be closed. Thanks.

---

