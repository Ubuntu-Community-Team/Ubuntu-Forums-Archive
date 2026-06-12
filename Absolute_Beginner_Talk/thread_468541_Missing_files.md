---
title: "Missing files"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by spookyct on 2007-06-09
I am running, KDE and I just delted a bunch of files...  but there was some sort of error.  They did not go to the trash.

When I click on trash, it says it is empty, and the files I deleted are no longer in their original position?  I also did not free up any disk space by deleting them.  Any idea on where the files are?  I am down to 435kb of disk space.

---

### Post by yurimxpxman on 2007-06-09
> **spookyct said:**
> I am running, KDE and I just delted a bunch of files...  but there was some sort of error.  They did not go to the trash.

When I click on trash, it says it is empty, and the files I deleted are no longer in their original position?  I also did not free up any disk space by deleting them.  Any idea on where the files are?  I am down to 435kb of disk space.
Open a terminal in that directory and type this:

```
ls -a | kate -i
```

Let us know if the files show up there.

---

### Post by spookyct on 2007-06-09
```
.
..
103_7018.JPG
2007-06-03--01.14.07
.aptitude
.bash_history
.bash_logout
.bash_profile
.bashrc
.comments
.config
Desktop
.dmrc
.emacs.d
.esd_auth
.evolution
Examples
Firefox_wallpaper.png
.fonts
.fonts.cache-1
.fonts.conf
.gaim
.gconf
.gconfd
.gftp
.gimp-2.2
.gksu.lock
.gnome
.gnome2
.gnome2_private
.gstreamer-0.10
.gtkrc-1.2-gnome2
.ICEauthority
.icons
.kde
.kderc
.lesshst
.local
.macromedia
.mcop
.mcoprc
.metacity
.mozilla
.mplayer
.nautilus
.openoffice.org2
Person.cpp
Person.cpp~
.qt
.recently-used
.recently-used.xbel
.sok
.ssh
.subversion
.sudo_as_admin_successful
.themes
.thumbnails
.Trash
.tsclient
.update-manager
.update-notifier
.vlc
.Xauthority
.xine
.xsession-errors
```


I delted a bunch of pictures...  60 MB...  they do not show up on there

---

### Post by yurimxpxman on 2007-06-09
> **spookyct said:**
> I delted a bunch of pictures...  60 MB...  they do not show up on there

Well, they couldn't have gone any further than your home directory (unless you were root), so have no fear! :D

It sounds to me like you just need to refresh the view of how much space you have left. If that doesn't work, then try doing a search for the files you tried to delete. Note that they may be in a hidden directory.

---

### Post by spookyct on 2007-06-09
still can't find them.  i want them deleted....  i need disk space.

i also get this error when i try to delete stuff

---

### Post by yurimxpxman on 2007-06-09
> **spookyct said:**
> still can't find them.  i want them deleted....  i need disk space.

i also get this error when i try to delete stuff
Ahah! You just need to run the command as root, like this:

```
sudo rm -R dirname
```

---

