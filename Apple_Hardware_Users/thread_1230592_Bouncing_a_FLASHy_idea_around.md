---
title: "Bouncing a FLASHy idea around"
date: 2009-08-03
forum: Apple Hardware Users
---

### Post by sha.goyjo on 2009-08-03
I'm just bouncing an idea around, but is there any way we could code a wrapper, similar to ndiswrapper, but for ppc systems? Or does one already exist?

I'm wondering because I've been installing Ubuntu on more and more ppc systems of late, and their inability to play flash is frustrating a lot of people.

And yes, I know about gnash and swfdec, but gnash fails on a lot of pages, and swfdec uses up way too much processor (it's a known bug, where it uses one full processor core).

Does anybody have any input?

---

### Post by sha.goyjo on 2009-08-05
bump....nobody interested in the ppc flash problem?

---

### Post by MikeTheC on 2009-08-05
I don't think anything like NDISwrapper exists for Mac OS X software. As I'm not a coder, I've no idea what would be involved in getting such a thing to exist. However, my gut tells me it would be ***very*** non-trivial to do it. But I guess *in theory* you could take Adobe's PPC Flash Player for Mac OS X, wrap it, and use it in Linux.

However, even if such a thing existed, and even if you didn't take *any* performance hit in running it that way, ***and*** even *if* the one-legged man was standing in just the right position, the fact of the matter is G3 and G4 hardware is extremely sub-optimal for displaying Flash content, pretty much without regard to clock speed. I used to have a 1.67GHz G4 PowerBook (which is the fastest clock speed Apple ever had for a G4 in any system they made) and Flash *still* sucked on it.

So could it be done in theory? Probably. Is there a point? No, not really.

---

### Post by sha.goyjo on 2009-08-06
lol...please realize, this is for my fiancee's computer.... :-)

---

### Post by rjcalifornia on 2009-08-06
hmmm... This is impossible. The G3 Processor is way to slow to display flash content properly....


However, I am able to watch FLV videos....

---

### Post by gwydionwaters on 2009-09-24
> **RandyVanBuren said:**
> hmmm... This is impossible. The G3 Processor is way to slow to display flash content properly....


However, I am able to watch FLV videos....

with gnash? i have had a heck of a time trying to compile it. any tips?

---

### Post by rjcalifornia on 2009-09-25
> **gwydionwaters said:**
> with gnash? i have had a heck of a time trying to compile it. any tips?


wait... I download the flv videos and play them in xine ;)

---

### Post by sweetleaf on 2009-09-25
> **gwydionwaters said:**
> with gnash? i have had a heck of a time trying to compile it. any tips?

I've compiled gnash for Jaunty on a G3 PPC. It works much better than the deb in the repositories. 

References:
[http://www.getgnash.org/packages/snapshots/ubuntu/jaunty/]("http://www.getgnash.org/packages/snapshots/ubuntu/jaunty/")
[http://wiki.gnashdev.org/Building_on_Debian]("http://wiki.gnashdev.org/Building_on_Debian")
[http://www.gnu.org/software/gnash/manual/gnashref.html]("http://www.gnu.org/software/gnash/manual/gnashref.html")

Dependencies:
```
sudo aptitude install automake dejagnu gettext libagg-dev \
libavformat-dev libboost-dev libboost-thread-dev \
libcurl4-gnutls-dev libgif-dev libgtk2.0-dev libjpeg62-dev \
libming-dev libpng12-dev libsdl1.2-dev libtool libxml2-dev \
mtasc libswscale-dev libming-util swfmill
```

Configure options:
```
./configure --prefix=/usr --mandir=/share/man \
--infodir=/share/info --enable-gui=gtk --enable-media=ffmpeg \
--disable-glext --with-plugins-install=system \
--with-npapi-install=system \
--with-npapi-plugindir=/usr/lib/mozilla/plugins/
```

**Note** above that I specify the ffmpeg backend rather than gstreamer. Other multimedia packages (gstreamer, mplayer, vlc) seem to have problems on the G3, whether because they're compiled for Altivec processors, or for some other reason. Whatever the problem is, ffmpeg seems to have addressed it better than the others.

Also, my settings ended up in /usr/etc/ instead of in /etc/, where I'd rather have them. Tweaking one of the dir options should fix this.

```
make
checkinstall
```

With the npapi configure options above, there shouldn't be any need to run [FONT="Courier New"]make install-plugins[/FONT]. The name of the plugin is libgnashplugin.so, and for me the installer automatically dropped it into the mozilla directory.

The gnu page encourages you to run [FONT="Courier New"]make check[/FONT] to "test" gnash before installing it. I found that this ran a very long time, and seemed to fail in the end, but that gnash still ran fine once I installed it. So I would suggest that you skip that step.

Good luck!

---

### Post by gwydionwaters on 2009-09-26
thanks, this seems to have worked. except it did not follow the directory changes so  i'm not sure which file to link to the mozilla plugin directory.

---

### Post by sweetleaf on 2009-09-26
> **gwydionwaters said:**
> it did not follow the directory changes so  i'm not sure which file to link to the mozilla plugin directory.

Did you remove the repository version before installing your compiled version?

```
sudo aptitude remove mozilla-plugin-gnash gnash
```

Did the [FONT="Courier New"]make[/FONT] step produce a plugin file?

```
sudo updatedb; locate libgnashplugin.so
```

---

### Post by sha.goyjo on 2010-05-25
I like where this is going. I'd much rather have a good set of instructions on making Gnash actually work than wrapping flash (which would be slow as hell).

---

