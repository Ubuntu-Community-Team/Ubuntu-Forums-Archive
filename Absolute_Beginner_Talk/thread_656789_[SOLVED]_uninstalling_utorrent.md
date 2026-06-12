---
title: "[SOLVED] uninstalling utorrent"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by esva on 2008-01-02
I went to the utorrent site and I clicked etc it opened with wine, then I checked the bandwith the port and then I closed it.

Now I can't find it anywhere!
I wish to uninstall it since the wine thing seems a hassle I rather use azureus ( is it too heavy? I rather something not consuming) But I can't find the utorrent thing in the wine  virtual c drive thing or the applications menu.
I read someone said there could be some spying involved in utorrent so that also adds to my madness.
 
How can i uninstall it?

---

### Post by ~LoKe on 2008-01-02
uTorrent doesn't have and "spyware" kind of software...but anyways...

Open up the terminal and type:
```
locate utorrent
```

---

### Post by esva on 2008-01-02
I also wwent to the add/remove thing and didn't see it in the installed aplications

---

### Post by ~LoKe on 2008-01-02
> **esva said:**
> I also wwent to the add/remove thing and didn't see it in the installed aplications

It wouldn't be in the installed applications because utorrent is a windows executable.

---

### Post by GuitarRocker2562 on 2008-01-02
use deluge, easy, fast, fantastic, runs native to linux and windows!

---

### Post by esva on 2008-01-02
are those bittorrent programs or for searching around the pc :S

---

### Post by esva on 2008-01-02
this is embarassing.

Nothing happens when I try to locate utorrent in the terminal
maybe it didn't install at all? but then hoq could I use it for a bit, htis is just weird/suspicious

---

### Post by PeterJS on 2008-01-02
Wine installs stuff in ~/.wine/drive_c/ and it's menu entries are some where under ~/.local/, but I don't rembmer the exact locations, there's not many things under there it shouldn't be hard to find.

---

### Post by ~LoKe on 2008-01-02
> **esva said:**
> this is embarassing.

Nothing happens when I try to locate utorrent in the terminal
maybe it didn't install at all? but then hoq could I use it for a bit, htis is just weird/suspicious

You probably clicked "open with...wine", so it only downloaded it to the temporary directory, which clears eventually.

---

### Post by ~LoKe on 2008-01-02
> **esva said:**
> are those bittorrent programs or for searching around the pc :S

Deluge is a bittorrent applications.

---

### Post by esva on 2008-01-02
oohh that might be it, cause I did check in that drive_c folder and didn't see it. I did saw some weird IE thing?  Anyway i think that's it. 
SORRY for this but how do you marked a thread as solved? Or I can't do that? I just don't want to leave threads abbandonned around

---

### Post by ~LoKe on 2008-01-02
> **esva said:**
> oohh that might be it, cause I did check in that drive_c folder and didn't see it. I did saw some weird IE thing?  Anyway i think that's it. 
SORRY for this but how do you marked a thread as solved? Or I can't do that? I just don't want to leave threads abbandonned around

Near the top there should be something called "Thread Tools".  Click that and choose "Mark thread as solved".

---

### Post by esva on 2008-01-02
LOL I never saw that I clicked on other parts  
Thanks all

---

### Post by ~LoKe on 2008-01-02
> **esva said:**
> LOL I never saw that I clicked on other parts  
Thanks all

No problem.  Another cool tool (but this one's new) is "thank".  It's this little icon: [img]http://ubuntuforums.org/images/uf/buttons/post_thanks.gif[/img] under a post.  It allows you to thank a user if they made a post that helps you.  Try to use it in future, eventually there will be a way to find only posts that have been thanked, which would be a good way to find a solution.

---

