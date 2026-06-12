---
title: "Deleted my /etc/xdg folder..."
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by glotz on 2006-06-13
Hi there!

I was fooling around with Xfce when I managed somehow to zero out the menus. (I think I just clicked on "edit menus" and up came some editor showing me an empty file...) Trying to fix this in a random frenzy of madness I to deleted my /etc/xdg. (I was thinking maybe this would return things to default state, well it didn't!) Now as a result, I seem to have lost all my menu entries in GNOME! I'd very much like them back, how do I do it? Did I lose something else too? EDIT: Looks like my box didn't lock itself when left alone for a long time (=hours)... Not good! (The screen had went black but it asked no password when I moved my mouse) Maybe this is another effect thanks to doing it.

Thanks a lot for reading this. 

Sometimes you really feel yourself brilliant... On the other hand, this is how one learns, by poking around and when one has made all the mistakes one can make, one surely knows a lot more. <insert a crunchy smiley>

PS. I think that this could be fixed if one of you guys with a rather virginal install of Ubuntu (on GNOME) would zip his folder and attach it to a reply. I'd really appreciate it. (I don't know if that has any privacy implications but I'm sure if it does, somebody will comment this.)

EDIT: the 'not locking itself' issue probably had to do with my messing around with the screen saver rather than this folder deletion business FWIW

---

### Post by glotz on 2006-06-13
Bump! Pleeez!

---

### Post by josys36 on 2006-07-26
I did the same thing and have lost all my menus.

I would really hate to have to fix this by a reinstall. So if you find out what has happend here please let me know.

Jason

---

### Post by trent dillman on 2006-07-26
I poked around in that directory on my box...try:

```
sudo apt-get install --reinstall gnome-menus
```

Also, add kdelibs-data and xubuntu-default-settings if you want kde and xfce menus as well.

---

### Post by josys36 on 2006-07-27
I tried your suggestions but the Gnome menus are still missing.

This may be one of those reload your system type mistakes. 

Jason

---

### Post by trent dillman on 2006-07-27
...

---

### Post by glotz on 2006-07-28
Sorry to report in that I fixed it only by reinstall the whole shebang... I didn't experiment very much though.

BTW, why did you delete it? I somehow lost the (right click?) menu in Xfce and tried to restore it by deleting "my settings". Obviously that's not the correct folder to mess with...

---

### Post by DougC on 2006-07-28
Hi,

Quick tip, although a bit late now. You should rename a system file/folder first rather than just deleting it, that way you can just rename it back agin if you get in trouble.

I've had similar problems myself. :)

---

### Post by glotz on 2006-07-28
That's very good advice. I must have gone into zombie mode... First selecting that folder and then deleting it instead of renaming... OMG :lol:

---

