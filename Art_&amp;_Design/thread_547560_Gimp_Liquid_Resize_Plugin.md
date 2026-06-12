---
title: "Gimp Liquid Resize Plugin"
date: 2007-09-10
forum: Art &amp; Design
---

### Post by stuporglue on 2007-09-10
If you haven't seen it yet, check out this video on Content Aware Image Resizing / Retargeting / Liquid Resizing

[http://www.youtube.com/watch?v=c-SSu3tJ3ns]("http://www.youtube.com/watch?v=c-SSu3tJ3ns")

Ok. [Carlo Baldassi]("http://web.tiscali.it/carlobaldassi/") made a plugin for the Gimp and I made a Ubuntu package for the plugin. 

I made it on Ubuntu Gutsy, and haven't tested it elsewhere yet. I just made the package with checkinstall.

If anyone wants to try it, you can visit my liquid resize web page : [http://stuporglue.org/gimp-lqr.php](http://stuporglue.org/gimp-lqr.php)

Or download the plugin directly : [http://stuporglue.org/downloads/lqr/gimp-lqr-plugin_0.2.0-0.1.4_i386.deb](http://stuporglue.org/downloads/lqr/gimp-lqr-plugin_0.2.0-0.1.4_i386.deb)

Thanks, 
Michael

---

### Post by insane_alien on 2007-09-10
seems to work fine. though, in certain pictures there are a lot of artefacts.suppose that is to be expected with data removal though. works best on landscapes.

---

### Post by stuporglue on 2007-09-10
> **insane_alien said:**
> seems to work fine. though, in certain pictures there are a lot of artefacts.suppose that is to be expected with data removal though. works best on landscapes.

Thanks for testing that. 

Yes, this is to be expected until there is a way to add or remove weight from specific areas of the image. See the youtube video linked above, starting at time 3:23. Once that feature is available, you'll be able to define where the distortions should or shouldn't occur, and it should work a lot better with people and other objects which need specific proportions.

---

### Post by insane_alien on 2007-09-10
yeah. but for a landscape like  a forrest or a beach it works awesomely well. it's good work.

---

### Post by evissecx on 2007-09-10
I tried installing the plugin on a Kubuntu feisty fawn. It was not a success. I used the .deb file first, then tried the tar.gz file. The installation went well. But in gimp, I couldn't find the plugin. I checked in both gimp 2.2 and gimp 2.3. 

I would really like to try this out. It looks really cool. :D
Maybe it didn't work, or maybe i'm too blind to find it in gimp.

---

### Post by insane_alien on 2007-09-10
it's under the "image" menu on the window with the actual image, right at the bottom. i'm using it with GIMP 2.4.

---

### Post by evissecx on 2007-09-10
> **insane_alien said:**
> it's under the "image" menu on the window with the actual image, right at the bottom. i'm using it with GIMP 2.4.

Too bad then. I don't got it. :(
I'm getting curious about upgrading to gutsy if it works better.
But I remember when I tried Feisty before it's official release.
I could not get everything to work then. So I think I will wait for Gutsys release and not upgrade to it right now..

---

### Post by rsambuca on 2007-09-10
> **evissecx said:**
> Too bad then. I don't got it. :(
I'm getting curious about upgrading to gutsy if it works better.
But I remember when I tried Feisty before it's official release.
I could not get everything to work then. So I think I will wait for Gutsys release and not upgrade to it right now..

If you were having troubles with Feisty prior to it's official release, this will be not different.  Only a month to go!

---

### Post by rsambuca on 2007-09-10
Oh yeah, almost forgot what I was originally going to post!  This plugin looks really cool.  I don't have time to test it today, but I definitely will be as soon as I have time.

---

### Post by Steveway on 2007-09-10
I hope I'm allowed to say this but:
FSCK YEAH!!!
I was fearing that this will be again sold by one of those big Companys like Adobe or MS but this is awesome.
I'm gonna try this now.
Thank you very much.

EDIT: lol, I wasn't allowed to say it.
EDIT2: Yes, works fantastic, a little bit slow but works very good.

---

### Post by evissecx on 2007-09-10
> **Steveway said:**
> 
FSCK YEAH!!!


Yea, this plugin sure looks dreamy :D

---

### Post by exploder on 2007-09-10
I installed the plugin in LinuxMint (Feisty) no problems. Thanks for the heads up on this!

---

### Post by stuporglue on 2007-09-10
> **evissecx said:**
> Too bad then. I don't got it. :(
I'm getting curious about upgrading to gutsy if it works better.
But I remember when I tried Feisty before it's official release.
I could not get everything to work then. So I think I will wait for Gutsys release and not upgrade to it right now..

Evissecx, 

Compiling it isn't too dificult if you have basic command line skills. I haven't tried this with Gimp 2.2, but I think it should work. I don't think it uses anything special. 

You'll need to have at least the following packages installed (via apt-get on the command line, or via synaptic). This is probably it, but there is a possibility that I already had something installed that I needed. 

```
build-essential, intltool,  autoconf1.9, libgimp2.0-dev,  checkinstall
```

Download the source tarball from this website: [http://web.tiscali.it/carlobaldassi/](http://web.tiscali.it/carlobaldassi/) and extract it to somewhere handy. 

In a terminal navigate to that directory, and run the following: 
```

./configure
make
sudo checkinstall -D --pkgname="gimp-lqr-plugin" --pkgversion 0.2 --pkgrelease 0.1.4  --pkgsource "http://web.tiscali.it/carlobaldassi/GimpLqrPlugin/gimp-lqr-plugin-0.1.4.tar.gz"  --maintainer "Your@Email.com"  --strip --stripso
```

Doing it this way will give you an installed package which you'll be able to upgrade easily when you do a system upgrade to Gutsy.

---

### Post by mcduck on 2007-09-11
Doesn't seem to work for me (Running Feisty & Gimp 2.2). I just get this error when starting Gimp:
```
/usr/lib/gimp/2.0/plug-ins/gimp-lqr-plugin: error while loading shared libraries: libgimpconfig-2.0.so.0: cannot open shared object file: No such file or directory

(gimp:7761): LibGimpBase-WARNING **: gimp: wire_read(): error
```

I don't seem to find libgimpconfig-2.0 anywhere. Does anybody have any idea which package provides that file?

---

### Post by stuporglue on 2007-09-11
McDuck, 

Did you build from source or install the package? 

I built the package on Ubuntu Gutsy, so there is a definate possibility that it won't work on Feisty. You could see if there's a package named "libgimp2.0" available that isn't installed, that might fix it. 

Otherwise, check the post immediately before yours, I describe the build instructions there.

Hope that helps, 

Michael

---

### Post by bubbalouie on 2007-09-11
Thanks, this is spectacular, having just discovered the gimp plugin system and the few tools I missed I have new found respect for gimp.

I think I am sold on gimp from now on, this is incredible, I have much respect for people that create such things, to then make it free, you have my admiration, thank you very much.

As an aside I have tested this on a few different types of landscape images and it works beautifully.

Thanks again.

---

### Post by stuporglue on 2007-09-11
> **bubbalouie said:**
>  I have much respect for people that create such things, to then make it free, you have my admiration, thank you very much.

Carlo Baldassi is who wrote it. His site is here: [http://web.tiscali.it/carlobaldassi/](http://web.tiscali.it/carlobaldassi/)

I haven't seen his email posted publicly anywhere, so I won't post it here, but if you download the source tarball, it's in the AUTHORS file.

---

### Post by mcduck on 2007-09-11
> **stuporglue said:**
> McDuck, 

Did you build from source or install the package? 

I built the package on Ubuntu Gutsy, so there is a definate possibility that it won't work on Feisty. You could see if there's a package named "libgimp2.0" available that isn't installed, that might fix it. 

Otherwise, check the post immediately before yours, I describe the build instructions there.

Hope that helps, 

Michael

I tried the .deb, and also the gzipped precompiled file. Also I do have libgimp2.0 installed.

I'm not that exited about compiling the plugin myself as it would mean installing quite a lot of development stuff on my laptop, and in the end I would still miss that library file..

Well, Gutsy's release is so close that I suppose I can wait until that. :)

Anyway, thanks for telling about this great tool. Now I have one more thing to keep me exited about Gutsy and new Gimp version. :D

---

### Post by Darxus on 2007-09-16
Can you provide the deb src so I can try rebuilding it under edgy?  I'm also not seeing it in the gimp 2.2.13 menus.

---

### Post by stuporglue on 2007-09-16
You can grab the source here: [http://web.tiscali.it/carlobaldassi/](http://web.tiscali.it/carlobaldassi/)

I just used checkinstall to make the debs, and won't have time to make a new deb or learn how to make a source one for a couple of weeks. 

sorry

---

### Post by Darxus on 2007-09-16
Under feisty, put this source in your /etc/apt/sources.list file:

deb [http://svetlyak.ru/debian](http://svetlyak.ru/debian) etch main contrib non-free

Run: aptitude update && aptitude install gimp-lqr-plugin

I started off with an edgy system, added that source line, and substituted all instances of "edgy" with "feisty", ran aptitude dist-update, aptitude install gimp-lqr-plugin, restarted gimp, and it WORKED (without a reboot).

'NOTE: the plugin now installs under the "Layer" menu.'

This is all from the original author of the plugin, Carlo Baldassi, on this page:  [http://web.tiscali.it/carlobaldassi/](http://web.tiscali.it/carlobaldassi/)

Guess I should finish that upgrade now.

Thanks everybody.  I, too, have been looking forward to this.

BTW, if you do the install on an edgy system after changing the sources all to feisty, as I did, this is what happens:

The following NEW packages will be installed:
  gimp-lqr-plugin libdatrie0 libthai-data libthai0 
The following packages will be upgraded:
  fontconfig-config libc6 libc6-dev libc6-i686 libcairo2 libfontconfig1 libfontconfig1-dev libglib2.0-0 libglib2.0-dev libpango1.0-0 libpango1.0-common libpng12-0 libpng12-dev 

I'm sure it is more wise to go about upgrading to feisty in the recommended way first.

---

### Post by MetalMusicAddict on 2007-09-21
Here's a proper Gutsy .deb. Some of the others floating around are made with checkinstall.

---

### Post by exile on 2007-09-25
Worked great in Gutsy for me. Tested it on some various architectural photos from Rome. I was very impressed how it kept the ratios of the dominant features mostly unchanged and rescaled the least dominant ones first.

I will be keeping my eye on this plugins development.

Thanks for the original post.

---

### Post by hikaricore on 2007-09-25
This is an amazing plugin.

I'm curious however do the GIMP version have support for selecting items to keep/remove like in the video?

**Edit** Nevermind, found my answer: > There isn't currently a way to designate an area as more or less important, so results are somewhat humorous at times.

---

### Post by IYY on 2007-09-25
Amazing! I've been wanting to give this a try ever since I saw the video featured on Slashdot, but never hoped it to be this soon, and in The Gimp.

---

### Post by jaem on 2007-09-25
I think this link was already posted, but evidently people haven't been to it.  Go to [http://web.tiscali.it/carlobaldassi/](http://web.tiscali.it/carlobaldassi/) for source tarball, as well as packages for Feisty, Gutsy, Debian, Slackware, and Windoze.  And yes, it does support removing and preserving content now.  That's a quick piece of work on the part of the dev :).

Also note, as the website says, the command has been moved to the Layers menu.  As a further note, it operates on layers - preservation and removal masks can be created by lassoing the object and filling with white in a separate layer - but the active layer is the one that will be operated on.  So once you're done creating the masks, remember to flip back to the main layer before you run the plugin, or it won't work properly.

All in all, the most excellent thing I've seen in a while!  And even better that it's free/OSS!

~Jeffery

---

