---
title: "Home Media Player Questions"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Shawn Dineley on 2007-02-05
Hello 

       I'm looking for a program like Mythtv. So I can watch programs and dvds on my system. From across the room (lying in bed). Using a remote to control it all. But I don't need to record tv or any PVR functions. I just what to watch shows I all ready have on linux box.  Right now I just do it with totem and mplayer on full screen. But I have to get up to change shows and volume. But I don't have my Ir receiver yet (should get it this week). 

      Can I do this with Mythtv or is there another program better suited for this?

      Mythtv looks more like a (DE) then a program. Or am I wrong about that?

      Can Totem, Mplayer, or other media player be setup to use a Remote Control, via plugin or something?

Any help would be great!! Thanks.

---

### Post by david_2001 on 2007-02-05
Lirc plus a compatible remote control is what you need.  I use my Microsoft MCE remote to control kaffeine (via irkick), xine and gxine.  Mplayer and totem should also work without any addons but I've never tried to set them up.  MythTV can also be remote controlled.

For instructions on setting up lirc, take a look at [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy) and also [http://gentoo-wiki.com/HOWTO_LIRC](http://gentoo-wiki.com/HOWTO_LIRC) (I know it's for Gentoo but it has useful information on setting up lirc to work with specific applications).

---

### Post by Shawn Dineley on 2007-02-05
Thanks 

     Are there any good guildes for Lirc on Dapper? I've been playing with it for a couple of hours now and I'm not getting very far.

Got my receiver in the mail today.

---

### Post by david_2001 on 2007-02-06
Well, what I've read in the past few minutes tells me that the lirc-modules-source package in dapper is broken and won't be fixed.  However, what I also read is that there is a working version in the dapper backports repository.  If you don't have the backports repository in your sources.list file then you will need to add the following:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
All things being equal - no guarantees because I don't have a dapper installation to use as a testbed - you should then be able to follow the Install Lirc Edgy installation guide.  What remote control do you have?

---

### Post by Shawn Dineley on 2007-02-06
tivo series2 remote

---

### Post by david_2001 on 2007-02-07
That model has apparently been supported by lirc for some time and there's a configuration file [here]("http://lirc.sourceforge.net/remotes/tivo/TIVO_Series_2").  Just a matter of setting up lirc to recognise the IR receiver you're using.

---

