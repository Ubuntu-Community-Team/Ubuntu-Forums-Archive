---
title: "camera not auto-detected"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by HarmonicaGoldfish on 2007-04-21
I had this problem with Edgy, and was hoping it would be resolved with an upgrade to Feisty, but it isn't...so here I am again.

I can import photos if I open up gthumbs and do a manual import, but my computer does not open the auto-import window when I plug the camera in, like it used to do with Dapper.

In System/Preferences/Removable Drives and Media/Camera - the import digital photos from camera option is ticked and the command is

gnome-volume-manager-gthumb %h

A friend of mine has suggested that I do a fresh install. That perhaps the code somehow got messed up during the original upgrade from dapper to edgy.

Any thoughts??

thanks!!

***I have posted this to [http://ubuntuforums.org/showthread.php?p=2507220#post2507220](http://ubuntuforums.org/showthread.php?p=2507220#post2507220) in multimedia and video subforum. I'm hoping that is  a more appropriate forum so I will get some answers! :)

---

### Post by phogy on 2007-04-25
I had this problem too and here's what I did:
```
rm -rf ~/.gconf/desktop/gnome/volume_manager
```
You might need to log out and back in again for it to take effect.
Also, I have no idea what side effects this might have...

---

### Post by HarmonicaGoldfish on 2007-04-26
thanks - I will give it a try. The next step is a fresh install of fesity, so it can't hurt!

---

### Post by HarmonicaGoldfish on 2007-04-26
Resolved! Thanks phogy!

---

