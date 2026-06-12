---
title: "Making default current language"
date: 2012-12-02
forum: Any Other OS
---

### Post by ifiaanri on 2012-12-02
Hey guys,

    The story is the following: I'm editing a LiveCD based on Ubuntu 12.04 (Pinguy) following[ LiveCDCustomization tutorial]("https://help.ubuntu.com/community/LiveCDCustomization") and I am setting the locale to ro_RO, the problem is that this being a LiveCD upon automatic login a dialog always asks to Update the names or not (screenshot -> [here]("http://img163.imageshack.us/img163/5270/updatelocale.png")).

    How can I setup as default the language in order for the names to be automatically updated?

    I've used from the tutorial, the following:

**# cat /usr/share/i18n/SUPPORTED | grep ro_**
```

ro_RO.UTF-8 UTF-8
ro_RO ISO-8859-2

```
```

locale-gen ro_RO 
update-locale LANG=ro_RO LANGUAGE=ro_RO LC_ALL=ro_RO

``````

make DEFAULT_LANG=ro sudo cp -af boot/* ../extract-cd/isolinux/

```**#** **cat /etc/default/locale** ```

LANG=ro_RO.UTF-8
LANGUAGE=ro_RO.UTF-8
LC_ALL=ro_RO.UTF-8
```Sorry if this is not the appropiate section since I am talking about a "modified" version of Ubuntu.

Thanks!

Later edit:

I've tried [this]("http://askubuntu.com/questions/83880/how-can-i-edit-etc-skel-while-keeping-the-default-folders-on-live-cd"), but so far no luck (everything seems right). Output:
```

/etc/skel# ls -a | grep . | awk -F: "{print $1}" | xargs stat --format="%a %n"
755 .
755 ..
644 .bash_logout
600 .bashrc
600 .bashrc.dpkg-old
775 .compiz
[COLOR=Red]**777 .config**[/COLOR]
600 .conkyForecast.config
600 .conky_grey.lua
600 .conkyrc
600 .conkyrc.default
600 .conkyrc.gray
600 .draw_bg.lua
[COLOR=Red]**777 .gconf**[/COLOR]
777 .gnome2
775 .imdb-thumbnailer
777 .local
775 .mozilla
644 .profile
775 .themes
775 .thunderbird
775 .wine
775 Desktop
777 Documents
777 Downloads
777 Music
777 Pictures
777 Public
775 Templates
777 Videos
644 examples.desktop

```By the way, the user is automatically created when booting the LiveCD, it is not present in /etc/passwd when I'm in chroot and editing the filesystem. Any ideas?

---

### Post by ifiaanri on 2012-12-02
Ok. So I've found a workaround, but the problem is that the file gets rewritten when user logs in and some folder are not displayed in "Places", though this is quite fine with me.

What I did is boot into the LiveCD and see the file user-dirs.dirs from .config/ folder. See [here]("https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs/+bug/209513/comments/12") for more details.

I've copied the files "user-dirs.dirs" and "user-dirs.locale" from the LiveCD into the chrooted /etc/skel/.config (from external terminal not in chroot).

```

**root@machine:/etc/skel/.config# ls -l user***
-rwxr-xr-x 1 root root 632 Dec  2 22:05 user-dirs.dirs
-rwxr-xr-x 1 root root 632 Dec  2 21:47 user-dirs.dirs_bak
-rwxr-xr-x 1 root root   5 Dec  2 22:05 user-dirs.locale
-rwxr-xr-x 1 root root   5 Dec  2 21:47 user-dirs.locale_bak
[B]
root@machine:/etc/skel/.config# cat user-dirs.dirs[/B]
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desc&#259;rc&#259;ri"
XDG_TEMPLATES_DIR="$HOME/&#536;abloane"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documente"
XDG_MUSIC_DIR="$HOME/Muzic&#259;"
XDG_PICTURES_DIR="$HOME/Poze"
XDG_VIDEOS_DIR="$HOME/Video"

**root@machine:/etc/skel/.config# cat user-dirs.locale**
ro_RO


```See the result [here]("http://img705.imageshack.us/img705/5996/userdirs.png").

Any idea how to setup them accordingly?

---

