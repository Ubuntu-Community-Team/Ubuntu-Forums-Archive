---
title: "We loose Firefox support here"
date: 2016-10-17
forum: Apple Hardware Users
---

### Post by luigiburdo on 2016-10-17
Hi guys looklike we dont have any more the new release of firefox on canonical ubuntu/powerpc ...
last working version is the 47.0 ... after stop
on other powerpc distros it is present 48 and now 49... why this?

---

### Post by vasa1 on 2016-10-17
What is your version number of Ubuntu? And which version of Firefox do you have?

---

### Post by luigiburdo on 2016-10-17
> **vasa1 said:**
> What is your version number of Ubuntu? And which version of Firefox do you have?
Hi
Ubuntu Mate 16.10 , Firefox 47.0 ... i been check there isnt firefox up to 47 available on ppc in canonical

---

### Post by ernsteiswuerfel on 2016-10-17
Yep. In Yakkety Yak, Firefox vanished from the iso a few days before the release. In Xenial FF 47 is still here and working.
All versions > 44 stopped working on PPC, see [Bug 1583849]("https://bugs.launchpad.net/firefox/+bug/1583849"). I am curious how the Ubuntu Team managed it to get Firefox 47 running nevertheless?

On Gentoo PPC I got *Otter* running, which seems a pretty decent browser. The last one left, since FF has the same problems on Gentoo either and qupzilla-2.0.x won't work on PPC since it depends on qtwebengine-5.6.x which does not support PPC at all (qt-[Bug]("https://bugreports.qt.io/browse/QTBUG-56465")).

---

### Post by luigiburdo on 2016-10-17
> **ernsteiswuerfel said:**
> Yep. In Yakkety Yak, Firefox vanished from the iso a few days before the release. In Xenial FF 47 is still here and working.
All versions > 44 stopped working on PPC, see [Bug 1583849]("https://bugs.launchpad.net/firefox/+bug/1583849"). I am curious how the Ubuntu Team managed it to get Firefox 47 running nevertheless?

On Gentoo PPC I got *Otter* running, which seems a pretty decent browser. The last one left, since FF has the same problems on Gentoo either and qupzilla-2.0.x won't work on PPC since it depends on qtwebengine-5.6.x which does not support PPC at all (qt-[Bug]("https://bugreports.qt.io/browse/QTBUG-56465")).

Hi Ernest,
firefox 49.1 ppc is present on:
-Debian
-Fedora
-Suse
and like you write on gentoo...
only here isnt present.
ah forget there are present qt 5.6 full working too.

---

### Post by ernsteiswuerfel on 2016-10-17
Hmm, interesting... Does Firefox work on Debian ppc?

Never tried Fedora PPC or openSUSE (Tumbleweed) because they are both 64bit distros and I can't use them on all of my PPC hardware.

---

### Post by luigiburdo on 2016-10-17
[QUOTE=ernsteiswuerfel;13558276]Hmm, interesting... Does Firefox work on Debian ppc?/QUOTE]

yes it have 
[https://packages.debian.org/sid/firefox](https://packages.debian.org/sid/firefox)

---

### Post by rican-linux on 2016-10-17
I have debian sid on my iBook and FF working fine there. My G5 is on lubuntu 16.10 and I needed to install midori to get a browser.

---

### Post by luigiburdo on 2016-10-18
> [COLOR=#000000]My G5 is on lubuntu 16.10 and I needed to install midori to get a browser[/COLOR]
why not fireforx 47?

---

### Post by ernsteiswuerfel on 2016-10-18
Just for fun I tried to install FF 49 from the Debian repository. The only missing dep is [libvpx-1.6.0]("https://packages.debian.org/sid/libvpx4"). Installation worked, FF 49 is able to start but crashes shortly afterwards.

---

### Post by luigiburdo on 2016-10-18
umm ... did you see why it crashes? gdb ?

---

### Post by luigiburdo on 2016-10-18
in any way you can install it on 16.10
[https://launchpad.net/ubuntu/+source/firefox/47.0+build3-0ubuntu0.16.04.1](https://launchpad.net/ubuntu/+source/firefox/47.0+build3-0ubuntu0.16.04.1) 
im using it from first release ... hope will have 49 or better 50 full working again

---

### Post by luigiburdo on 2016-10-19
Made firefox 49 run on 16.10
installed the sid deb , installed the vpx4 installed the XOM ... builded vpx 1.0 .. and run.
is pretty unstable with some website i think js engine have some endianess. example github crash

---

### Post by ernsteiswuerfel on 2016-10-19
Nice you got it running! Yes, very simple websites work but anything a little more modern crashes sooner or later.

But rican-linux mentioned FF 49 is running ok on Debian. Which means hopefully there are some Debian patches flying around to make it work properly?

---

### Post by rican-linux on 2016-10-20
Yes FF 49 is available in Debian Sid for PPC 47 for PPC64

[https://packages.debian.org/search?suite=sid&section=all&arch=any&searchon=names&keywords=firefox](https://packages.debian.org/search?suite=sid&section=all&arch=any&searchon=names&keywords=firefox)

---

### Post by apple-apple on 2016-10-22
Well guys, I've been attempting to compile firefox from source for the last day on my G5. Progress is slow. I keep getting hung up on what appears to be a bunch of POSIX calls. I have bash and I thought that would take care of it. As I re-re-read the literature though I think that maybe I had an incompatible autoconf. I thought I had an acceptable version installed, but I'll go ahead and build what mozilla recomends and see what happens. If I'm eventually successful (and if the darn thing works) I'll try to make a deb package of it and link it somewhere.

---

### Post by apple-apple on 2016-10-22
Wait... Hows the Debian SID package working out? Before I started trying to compile for our platform I installed the Debian version but it was crashy. Is that not the case anymore? For what its worth other ubuntu based distro's version of FF is crashy as well. It seems that others have got around the problem by installing the Ubuntu version by way of synaptic.

---

### Post by rican-linux on 2016-10-22
I am browsing the web right now on FF 49 in Debian. So far no issues.

---

### Post by apple-apple on 2016-10-22
I'm envious. I've tried on 16.04 and 16.10 Both crash a bunch.

Also, I cant get past an error while trying to compile. It keeps on saying that I don't have some x11 packages installed. It's looking for xcb, x11, x this and that... but I've got them all installed. Guess I won't be compiling on my system after all.

---

### Post by xeno74 on 2016-10-23
> **apple-apple said:**
> I'm envious. I've tried on 16.04 and 16.10 Both crash a bunch.

Also, I cant get past an error while trying to compile. It keeps on saying that I don't have some x11 packages installed. It's looking for xcb, x11, x this and that... but I've got them all installed. Guess I won't be compiling on my system after all.

You need to install the dev packages of xcb, x11, x etc etc.

E.g. libx11-xcb-dev

---

### Post by ernsteiswuerfel on 2016-10-24
> **apple-apple said:**
> Also, I cant get past an error while trying to compile. It keeps on saying that I don't have some x11 packages installed. It's looking for xcb, x11, x this and that... but I've got them all installed. Guess I won't be compiling on my system after all.
Keep us updated! I wonder how this turns out.

---

### Post by apple-apple on 2016-10-24
Ah well. It may be a moot point. My g5 has done some wonky things over the years and ever since I got it the power supply has been real loud. Anywho, it wouldn't turn on this morning at all. I think it finally bought the farm.

---

### Post by ernsteiswuerfel on 2016-10-25
That's too bad! :sad:

But maybe it could be a special stroke of destiny you should get an AmigaOne X5000 (if you want to stay on PPC). ;)

---

