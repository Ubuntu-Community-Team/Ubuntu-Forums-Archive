---
title: "GStreamer - The Root of All 7.10 Evils?"
date: 2007-12-10
forum: Apple PPC Users
---

### Post by MonkeyChewToy on 2007-12-10
I've noticed that all my problems with Gutsy seem to stem from a problem with GStreamer. Gnome Settings Daemon? Gstreamer error. Gnash won't work? GStreamer. Exaile? Gstreamer. It seems everything depends on Gstreamer, and so everything fails.

This is the precise error that seems to be tagged on the end of everything:
[quote="Program error"]Could not initialize GStreamer: Error re-scanning registry , child terminated by signal[/quote]

If we can fix this, then I suspect mine and many others' Ubuntu 7.10 experiences will be a whole lot more pleasant.

Me, I don't know diddly about this kinda stuff. I just know it'd be really nice if everything would work the way it's supposed to.

---

### Post by umwelt on 2007-12-10
Amen, brother.

GStreamer needs a kick in the nuts

---

### Post by stmiller on 2007-12-11
Try installing totem-gstreamer. This should remove the xine backend for gstreamer which was problematic for me. This is only a hunch, so no promises. :)

---

### Post by A + on 2007-12-11
I've just installed gstreamer (I think! - a youtube download was looking for it).  Is VLC different or what?

---

### Post by MonkeyChewToy on 2007-12-12
Thanks for the tip, stmiller, but no dice. Gstreamer is still terminating its children like a frightned mother hamster. All because of some error re-scanning the registry.

It's tragic, really.

---

### Post by MonkeyChewToy on 2007-12-15
So, does anyone have any other leads here? Children continue to be terminated while we sit around waiting for answers.

*Think of the children!*

---

### Post by cuvtixo on 2007-12-16
I'm a confused newbie: Is GStreamer is primarily, or even just originally,  a Gnome application?   Would the latest Kubuntu release be a better alternative in this case?  Does Kubuntu have as many, or  even more Gstreamer dependent apps?

---

### Post by kelvin spratt on 2007-12-16
Mplayer setup properly does the lot with no problems Youtube, Movie trailers etc, and in full screen

---

### Post by MonkeyChewToy on 2007-12-31
Okay. Well, it's been a couple weeks. I've been using Xubuntu to avoid that "gnome-settings-daemon" error, but I'm not all that better off. There's still a ton of programs that just won't work without gstreamer. So, any word? Has progress been made? I understand that the PPC dev team is working as best they can, but I haven't found any indication that this problem in particular is being solved.

Thanks for the help.

---

### Post by mrgnash on 2007-12-31
Gstreamer is awesome.

---

### Post by MonkeyChewToy on 2008-01-14
That was, um, helpful? Okay.

Perhaps the title of this thread is a little alarmist, but this is a serious problem and I'm somewhat irritated that it's not even in the "Known PPC Issues" article.

I've been running 7.10 for a month like this. It's not pleasant. Is there someone here who can help me solve this? Please?

---

