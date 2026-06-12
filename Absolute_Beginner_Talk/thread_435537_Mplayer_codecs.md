---
title: "Mplayer codecs"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Psyclown on 2007-05-07
ANybody know where to put Mplayer codecs? im getting this error

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

im assuming that means i need codecs

---

### Post by teddybairs1 on 2007-05-07
Mplayer runs on the xine engine. Go to Synaptic, search for xine, and install any packages xine related. You could also check out the medibuntu repos at medibuntu.org. These will give you access to encrypted dvd support and win32 codecs.

---

### Post by powder on 2007-05-07
MPlayer doesn't use xine so that would be a waste of time.  You should install the w32codecs package as suggested and see if that solves the problem.

---

### Post by ubnewbie2 on 2007-05-07
> **Psyclown said:**
> ANybody know where to put Mplayer codecs? im getting this error

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

im assuming that means i need codecs



Here's the readme from the codecs you can download from mplayerhq. A few answers here...

```
These are binary codecs for use with MPlayer. They are useless for normal
Windows players (like WMP, QuickTime, RealPlayer, ...) as they only contain
the DLLs without installer and other fancy stuff needed to use them with
common Windows players.

Put the files contained in this archive in a directory where MPlayer will find
them. The default directory is /usr/local/lib/codecs/ ($prefix/lib/codecs/) if
you are compiling from source, but you can change that value by passing the
'--with-codecsdir' option to './configure'.

If you use a prebuilt MPlayer package it will most likely be /usr/lib/codecs,
see the documentation of your package for details.

In the past /usr/local/lib/win32 or /usr/lib/win32 was the default directory,
some packages as well as a few other Unix players like xine and avifile still
use it, refer to their documentation for further details.
```

---

### Post by kerry_s on 2007-05-07
I use this repo->

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main  

for the key->

sudo apt-get install debian-multimedia-keyring

or find it in synaptic and install.

---

### Post by Nythain on 2007-05-07
that woudl work i guess, but its usually better to use ubuntu repos as there are slight differences in the builds, and not all deb packages might work on ubunut machines... the best bet would be the medibuntu repo really

---

### Post by kerry_s on 2007-05-07
> **Nythain said:**
> that woudl work i guess, but its usually better to use ubuntu repos as there are slight differences in the builds, and not all deb packages might work on ubunut machines... the best bet would be the medibuntu repo really

I don't like the medi repo there not dependable enough yet. Ive used the debian ones since dapper with out problems, now using feisty. It should be no problem for the codecs and lbdvdcss2, Ive also had no problems with the media players.

---

### Post by teddybairs1 on 2007-05-07
My Mplayer keeps telling me it's using the xine engine.

In general you're right, it is better to use the Medibuntu repos than the ones for Etch; although Medibuntu can be maddeningly slow on the download. I've used some Etch .debs before without incident but Etch and Feisty although genetically similar do differ in points which can matter to a package. It would kind of be the difference between Neanderthal and Homo Sapiens. Yes they can interbreed, but it may or may not work to produce a result.

---

### Post by Bachstelze on 2007-05-07
Are you sure it's mplayer you're using and not someting else ? mplayer is an engine by itself so it using xine makes no sense...

---

### Post by teddybairs1 on 2007-05-07
It says Mplayer in the menu. I tried running a VCD with it and it told me the xine engine was having a problem. I have to assume it's running on xine given the error message.

---

### Post by Bachstelze on 2007-05-07
Isn't it rather *gmplayer* ? It's a GUI for mplayer but can also use other engines, like Xine.

---

### Post by Malta paul on 2007-05-07
Are you sure you don't mean Totem Movie Player ?
You could always use VLC player. It would get over your codec problems. :)

---

### Post by mahiyar on 2007-05-07
In the default menu there is no totem player or Xine player its just Movie player (see snapshot), that movie player is also known as totem movie player which runs on Xine engine. However Mplayer movie player also known as multimedia player is a world in itself with codecs and all as stated in the post above. So is the VLC player which is completely independent. So much for clarity. You will need to know this as by my experience if you need to ply all the formats you will need at least two players. In completeness mplayer is the most complete player. (i.e multimedia movie player)

---

### Post by teddybairs1 on 2007-05-07
Guys, I appreciate the help, but I didn't post and this isn't my thread. I don't want to hijack it from someone else who needs help. Yes, I know the difference between mplayer, totem, kaffeine, vlc, gxine, etc. I also know the difference between xine and gstreamer. As I said before this is someone else's thread, and the focus should be on his problem, not mine.

---

### Post by Psyclown on 2007-05-11
argh my computer is dying lately and i havnt been able to get on.. waht i did was download those binary codecs and throw them into a desktop folder then told xineplayer to access that folder. a bit roundabout but it worked

---

