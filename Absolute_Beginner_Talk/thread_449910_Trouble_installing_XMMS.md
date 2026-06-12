---
title: "Trouble installing XMMS"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2007-05-20
Okay, I have acquired a magazine DVD with a variety of programs. I have tried to compile XMMS media player, but it comes up with an error saying that it needs Glib 1.2.2 or later, but i supposedly to installed Glib 2.2.1? 

Do I have to have some special place on the file system to put it? It also says that if Glib was installed in PREFIX make sure Prefix/bin is in your path or set GLIB_CONFIG enviroment variable to the full path glib config.

---

### Post by starcraft.man on 2007-05-20
Ummm, is there a particular reason you want to compile xmms? There is a perfectly functional (and I think uptodate) version in the repos. Just go:

```
sudo aptitude install xmms
```

That of course needs to be run in the terminal (Applications > Accessories > Terminal).

You can also list all the plugins by entering this in the terminal:

```
sudo aptitude search xmms
```

Or alternatively open Synaptic (or even add remove I suppose), Synaptic is in System > Administration > Synaptic Package Manager. Push the search button on the panel and type in "xmms" That should list the same things as the terminal, you can then install it as you like.

Compiling really doesn't need to be done unless you have a specific reason.

---

### Post by Belliinator on 2007-05-20
I have a dial up connection, how long would it take to download it that way?

---

### Post by starcraft.man on 2007-05-20
> **Belliinator said:**
> I have a dial up connection, how long would it take to download it that way?

The main xmms download is only 813kb you should be able to manage that, I think. Other plugins additionally may be a bit more. It not as big a program as inkscape though so however much you install with it, it won't be too large.

---

### Post by Belliinator on 2007-05-20
Cool, thanks. Will it play Mp3 files or do I have download some patch

---

### Post by starcraft.man on 2007-05-20
> **Belliinator said:**
> Cool, thanks. Will it play Mp3 files or do I have download some patch

I believe you'll need a separate codec for that, not certain. I think the only player that natively plays everything is VLC.

Follow this [guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") to install Feisty's extra repos (I assume you have feisty right?)

This [guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs") will detail how to get the codecs, don't install the w32 codecs I think they are fairly large and since your on limited connection I guess you can wait for that.

This code in the terminal will get you all the restricted codecs:
```

sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

Only paste it in after you copy and replace your sources list with the one listed there, make sure to follow it carefully please :).

That should be it, then you will have xmms and all the restricted codecs (minus, windows codecs).

Oh and the download is less than 50 k for the codec packages.

Edit: Wuups, your listed as Dapper... if your using that, the guide for dapper [here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories") and then paste this into the terminal.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

Double Edit: So first set is for Feisty, second set (after first edit, is if your on dapper) Hope that is clear enough :).

---

