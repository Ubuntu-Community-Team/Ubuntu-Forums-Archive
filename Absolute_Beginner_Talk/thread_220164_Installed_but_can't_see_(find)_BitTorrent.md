---
title: "Installed but can't see (find) BitTorrent"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-07-21
I'm usuing Xubuntu 6.06 and I installed BitTorrent from the repositories.
I can't find it in any of my menus and I don't know where packages are downloaded to.

Can someone please advise me?

Cheers

---

### Post by OU812 on 2006-07-21
I had a similar problem when installing streamtuner. I did applications>accessories>alacarte menu editor. I clicked the sound & video icon and streamtuner was in the list. And its box was checked, so it should have shown up. So, I unchecked, rechecked it, saved it, and it appeared. Who knows, this may work for you.

john

---

### Post by n00b@linux on 2006-07-21
Thanks, but I forgot to mention that I'm using Xfce.

---

### Post by OU812 on 2006-07-21
This is from another post I wrote.

> To edit the menu look in

/usr/share/applications

you'll see a bunch of files: name.desktop. Open one of those in an editor. Study it. Then if you want to add a program that doesn't put itself in the menu, edit one of the *.desktop files (I suggest one for a similar app or program category).

To add an icon, when I was using xfce I would put them in /usr/share/pixmaps.


BTW: If the entry doesn't show up right away - open preferences and click on desktop. Find the button for editing the menu (it's in the first or second tab - I don't run xfce anymore, so just look for it). Then check any box. Uncheck it. Choose save. This should "reset" the menu and your entry should be there.

john

---

### Post by n00b@linux on 2006-07-21
Excellent.  Thanks.  Just one more question:  where will I find BitTorrent?  I'm kinda new to linux, as you can tell, and I don't know where Synaptic puts the files it downloads from the respositories.  I presume it puts them all in one place.  I looked in /opt but it's completely empty.

---

### Post by OU812 on 2006-07-21
Most of the time the "executable" ends up in /usr/bin. Sometimes other places like /usr/share/bin. So mostly look in /usr.

john

---

### Post by stricevics on 2006-07-21
> **n00b@linux said:**
> I'm usuing Xubuntu 6.06 and I installed BitTorrent from the repositories.
I can't find it in any of my menus and I don't know where packages are downloaded to.

Can someone please advise me?

Cheers

From the terminal try: ```
/usr/bin/bittorrent
```

If that works, exit the bittorrent and create a link on your desktop and point it to that location.

If it doesn't, try running: ```
locate bittorrent
```

Hopefully, that will supply you with information where executable is located so that you can use it to point the desktop link to it.

Hope this helps.

---

