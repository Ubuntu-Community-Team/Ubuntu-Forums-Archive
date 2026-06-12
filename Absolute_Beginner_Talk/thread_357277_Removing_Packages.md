---
title: "Removing Packages"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-02-09
I have just installed Xubuntu Edgy Eft 6.10. And L'm very happy with it so far.

I was wondering how I can remove some packages making sure that I have removed all the dependency's

EG

```
sudo aptitude purge xubuntu-desktop gaim gxine ...
```

If I do so I know there are left over packages, eg gaim-data.

If I had installed them as: ```
sudo aptitude install gaim
``` Then when I did ```
sudo aptitude purge gaim
``` It would also remove other packages.

What do I do?

---

### Post by konst88 on 2007-02-09
If you install it with aptitude, all the dependencies will be removed.
If it is pre installed or installed with apt-get, you just need to search in synaptic or aptitude for the package name, and remove it by yourself.

---

### Post by guysmiley25 on 2007-02-09
The problem is how do you know what packages are dependencies of what packages?

---

### Post by ahaslam on 2007-02-09
[http://packages.ubuntu.com/edgy/](http://packages.ubuntu.com/edgy/)

;)

---

### Post by guysmiley25 on 2007-02-10
Awesome dude, cheers for that.

So after a fresh install of Xubuntu Edgy Eft 6.10, I enabled multi-verse and added a couple more sources.

Then I did a update and a upgrade

```

sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade

```

Then to remove gaim I when to [http://packages.ubuntu.com/edgy/net/gaim]("http://packages.ubuntu.com/edgy/net/gaim")  to find all the dependences, and tried removing them one at a time.

EG

```

sudo aptitude purge xubuntu-desktop
sudo aptitude purge xubuntu-desktop gaim
sudo aptitude purge xubuntu-desktop gaim gaim-data
sudo aptitude purge xubuntu-desktop gaim gaim-data libao2
...
sudo aptitude pugre xubuntu-desktop gaim gaim-data libao2 libaspell15 .....

```

Then every time it complained about dependency issues with other package I would then not remove that package.

Here was my end result:
```

sudo aptitude purge xubuntu-desktop gaim gaim-data libao2 libaudiofile0 libgadu3 libgtkspell0 libmeanwhile1

```

Is this really the best I can do? If I installed my system and built it up from a command line system and installed gaim with aptitude then would removing with aptitude have the same effect as what I have done?

Also what I have done was quite a systematic and therefore shouldn't be able to be done with a application?

Any help will be awesome, but for now I guess I have to do this the hard way. :(

---

### Post by guysmiley25 on 2007-02-10
Just another thought, what about dependencies of dependencies?

---

### Post by guysmiley25 on 2007-02-10
Anyone wish to comment?

---

### Post by ahaslam on 2007-02-10
Have you heard of deborphan/gtkorphan (something like that)? It will identify orphaned packages (unused dep's) and allow you to remove them. 

Tony.

---

