---
title: "daemon tools for ubuntu?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-12
Hi,

What is your preferred ubuntu program to serve as daemon tools, for mounting a bin, iso file?

Thanks.

---

### Post by gerbman on 2006-06-12
[QUOTE=u.b.u.n.t.u]Hi,

What is your preferred ubuntu program to serve as daemon tools, for mounting a bin, iso file?

Thanks.[/QUOTE]ISO files can be mounted like [this]("https://wiki.ubuntu.com/MountIso?highlight=%28iso%29%7C%28mount%29").

---

### Post by Xzallion on 2006-06-12
I believe all current incarnations of Linux, including Ubuntu can already mount iso files and such.  I have never tried before myself but a quick google along these lines "Mounting iso in ubuntu" should provide you with what you need.

Sorry I couldn't be of more help but at least you can check that until someone more knowledgable replies to your thread.

Edit:  Darn gerbman you beat me to it.

---

### Post by elemental666 on 2006-06-12
I've been wondering about this miyself, so I searched google for "daemon tools linux" w/o the quotes.  Here's some packages I found (not sure if they are in the repos though).

[CDemu]("http://cdemu.sourceforge.net/")
[mount-iso-image]("http://freshmeat.net/projects/mount-iso-image/") this handles bin/cue files as well.

In KDE you can convert bin/cue files to iso files with [kiso]("http://kiso.sourceforge.net/").

for isos you can just mount them:
```
mount -t iso9660 /path/to/file.iso /mnt/dir/for/iso -o loop
```

Freshmeat.net finds 78 packages when searching for: [bin/cue cue/bin]("http://freshmeat.net/search/?q=bin%2Fcue+cue%2Fbin&section=projects&Go.x=0&Go.y=0")

I'll work on this when I get home in the morning and see how well they play with ubuntu...

P.S. if you follow [this]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28RestrictedFormats%29") guide then mplayer or vlc can play .bin files.

---

### Post by u.b.u.n.t.u on 2006-06-12
Thank you elemental666.

A lot of helpful information in your post.

I have VLC and it plays the bin file, (a movie) - great! :D 

That saves having to mount the bin file.

I downloaded mount-iso-image from here:
[http://kde-apps.org/content/show.php?content=11577](http://kde-apps.org/content/show.php?content=11577)

It has 2 files, one a "install.sh", but I don't know how to install this.

mount-iso-image seems to be the closest Daemon Tools for Linux.

Thank you also for the freshmeat.net link. I have bookmarked it for future reference.

Thanks also gerbman and Xzallion.

---

### Post by elemental666 on 2006-06-12
No problem buddy, just trying to give back.

[QUOTE=u.b.u.n.t.u]It has 2 files, one a "install.sh", but I don't know how to install this.[/QUOTE]

cd to the directory containing that install.sh and type:
```
./install.sh
```

---

### Post by u.b.u.n.t.u on 2006-06-12
[QUOTE=elemental666]No problem buddy, just trying to give back.



cd to the directory containing that install.sh and type:
```
./install.sh
```[/QUOTE]

Thanks.

"- Mount-ISO v0.9.1 -
--------------------------------------------
Environment:

Couldn't find KDE config folder!
Type the full path here or press "Ctrl+C" to abort:"

I am using gnome, so I will this program a miss for now.

---

### Post by elemental666 on 2006-06-12
oops, didn't realize it was a KDE app... sorry

---

### Post by u.b.u.n.t.u on 2006-06-12
I appreciate your help.

Learning that VLC can play bin (movie) files is great!

---

### Post by elemental666 on 2006-06-12
out of curiosity can you skip around in VLC, like seek forward and backward?

I know that mplayer can, that's what I use most of the time.

---

### Post by u.b.u.n.t.u on 2006-06-12
I am unsure what VLC can do. I found the play, stop, full screen toggle and that is probably all I will ever need. I mainly used bsplayer the free version (the one before they snuck in the ads). Totem is excellent.

---

