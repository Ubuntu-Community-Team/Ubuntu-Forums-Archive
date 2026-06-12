---
title: "Iceweasel(Firefox) rendering problem with Gnome3?"
date: 2011-11-13
forum: Any Other OS
---

### Post by deepclutch on 2011-11-13
Update:
[B][COLOR=#FF0000]People facing this issue with image rendering in browser and other applications, Kindly register with [http://www.nvnews.net/vbulletin/](http://www.nvnews.net/vbulletin/) and Help the Nvidia developer Hopefully fix this bug ASAP. Nvidia Developer is Listening.
[COLOR=DarkRed]link:[/COLOR]
[/COLOR][/B][http://www.nvnews.net/vbulletin/showpos ... stcount=27]("http://www.nvnews.net/vbulletin/showpost.php?p=2550776&postcount=27")

[B]We may need more people who faces this bug to give more inputs. Note  that irrespective of distro this issue is prevalent. be it Ubuntu,Fedora  or Debian.
[/B]


using Debian testing and Ubuntu 12.04 . upgraded to Gnome3. with Gnome3, Chromium browser works fine. video/graphics acceleration everything fine. except firefox(iceweasel).

iceweasel-7.0.1(Firefox), when scrolling through long pages shows misaligned page like this:
[IMG]http://i39.tinypic.com/29wa3wl.png[/IMG]
[http://upl0ad.org/images/iceweasel.png](http://upl0ad.org/images/iceweasel.png)

after going through bulldconfig, I doubt if Iceweasel needs "--enable-default-toolkit=cairo-gtk3" used to compile? is cairo-gtk3 as default toolkit can be passed through any environment variable before invoking iceweasel? 
I tried with vanilla 64-bit firefox-aurora downloaded from mozilla. it also showed artifacts or say misalignment in webpages.

What is the reason for this, I am confused. More info here: [http://forums.debian.net/viewtopic.php?f=6&t=72358](http://forums.debian.net/viewtopic.php?f=6&t=72358)

TIA+


buildconfig:

```
about:buildconfig
Build platform
target
x86_64-pc-linux-gnu
Build tools
Compiler    Version    Compiler flags
gcc     gcc version 4.6.1 (Debian 4.6.1-15)    -Wall -W -Wno-unused  -Wpointer-arith -Wdeclaration-after-statement -Wcast-align -W  -fno-strict-aliasing -ffunction-sections -fdata-sections -pthread -pipe  -DNDEBUG -DTRIMMED -g -Os -freorder-blocks -fomit-frame-pointer
g++     gcc version 4.6.1 (Debian 4.6.1-15)    -fno-rtti -fno-exceptions -Wall  -Wpointer-arith -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy  -Wno-non-virtual-dtor -Wcast-align -Wno-invalid-offsetof  -Wno-variadic-macros -Werror=return-type -ffunction-sections  -fdata-sections -fno-strict-aliasing -std=gnu++0x -pthread -pipe  -DNDEBUG -DTRIMMED -g -Os -freorder-blocks -fomit-frame-pointer
Configure arguments

--enable-application=xulrunner  --prefix=/usr --enable-default-toolkit=cairo-gtk2 --enable-pango  --enable-system-cairo --with-system-jpeg --with-system-zlib  --with-system-bz2 --with-system-nspr --with-system-nss --enable-svg  --enable-mathml --disable-pedantic --disable-long-long-warning  --disable-gnomevfs --disable-gconf --enable-gio --enable-gnomeui  --disable-mochitest --disable-debug --enable-canvas --enable-readline  --disable-installer --disable-javaxpcom --disable-elf-dynstr-gc  --enable-system-hunspell --disable-crashreporter --enable-system-sqlite  --disable-strip --disable-install-strip --enable-url-classifier  --enable-startup-notification --enable-system-ffi --with-system-libevent  --with-system-libvpx --enable-shared-js --host=x86_64-linux-gnu  --build=x86_64-linux-gnu --prefix=/usr  --with-default-mozilla-five-home=/usr/lib/xulrunner-7.0 
```

---

### Post by LinuxFan999 on 2011-11-15
Have you tried Google Chrome/Chromium?

---

### Post by deepclutch on 2011-11-16
> **LinuxFan999 said:**
> Have you tried Google Chrome/Chromium?
Chromium browser works fine. no other applications faces this. I am clueless. I even tried firefox-64-bit to check. still the ugly artifacts like thing happens. :(

---

### Post by LinuxFan999 on 2011-11-16
Could you please post screen shots showing the rendering differences between Chrome and Firefox?

---

### Post by deepclutch on 2011-11-16
font rendering everything is fine(anti aliasing etc).
The issue is misalignment of pages when You scroll Up or Down.
the screenshot is attached of iceweasel/firefox in first post.

google chromium works fine.

---

### Post by cbowman57 on 2011-11-16
Pretty sure Firefox/Iceweasel use hardware acceleration by default, try disabling that & see what happens.

[http://support.mozilla.com/en-US/questions/796757](http://support.mozilla.com/en-US/questions/796757)

---

### Post by deepclutch on 2011-11-17
> **cbowman57 said:**
> Pretty sure Firefox/Iceweasel use hardware acceleration by default, try disabling that & see what happens.

[http://support.mozilla.com/en-US/questions/796757](http://support.mozilla.com/en-US/questions/796757)
Yes. it helped a little. 


EDIT: Still the Problem persists. it is not a page rendering issue. instead, it is page getting stuck or say garbled looking for few seconds and return to correct rendering later.

Thank You.

---

### Post by cbowman57 on 2011-11-17
Glad it helped some.

Is it happening with all versions or just the current release?

---

### Post by deepclutch on 2011-11-17
@cbowman57: **Now the issue is not alone with Iceweasel**! In Gnome3 Shell Env, applications like Eye of Gnome viewer etc also loads image as if video acceleration is not working like it should.

glxinfo,glxgear et al shows nvidia drivers are working fine. In Gnome3 Fallback(and Compiz), there is absolutely no issue!. So, it is a bug with Gnome3 compositing manager? Can I switch Gnome3-Shell to 2D ?

Below is a screenshot with eog loading a image,  when I tried zoom out  the image. Look at the word "Haq" which is rendered garbled :
[IMG]http://i42.tinypic.com/dpetg9.png[/IMG]

Thanks

---

### Post by cbowman57 on 2011-11-17
There is no 2D version of Gnome shell yet.

I'd try some other versions of the Nvidia driver.

Is this on a laptop?

---

### Post by deepclutch on 2011-11-17
No. it is on Desktop. 64-bit nvidia 7300GT card. driver:290.06 . works perfectly fine in Gnome3 fallback.

possibly a issue with nvidia driver and xorg ?

---

### Post by cbowman57 on 2011-11-17
> **deepclutch said:**
> No. it is on Desktop. 64-bit nvidia 7300GT card. driver:290.06 . works perfectly fine in Gnome3 fallback.

possibly a issue with nvidia driver and xorg ?

Quite possible, I'd drop back to the 285 series & see if the problem goes away.  I've run into similar issues before, sometimes the newest isn't the best. :)

Try running this in a terminal & see if it helps.

```
export CLUTTER_VBLANK=none
```If it clears it up add that line to your ~/.profile

---

### Post by deepclutch on 2011-11-17
Actually I have upgraded to the latest available nvidia driver hoping to resolve this issue!:p 

and Yes. the above variable seems to be helpful with the issue. now, if I zoom in or zoom out images in EOG, it does not get stuck like before. 
In nvidia-settings, I have "sync to vblank" enabled on most options. is that a cause. 

yet, pages are sluggish to load although lot much improved.

I'll add to ~/.profile and will update this thread after next reboot.

---

### Post by cbowman57 on 2011-11-17
Not certain but I disable the sync to vblank option out of habit & haven't had any problems.

Hopefully this resolves the problem. :)

---

### Post by deepclutch on 2011-11-21
> **cbowman57 said:**
> Not certain but I disable the sync to vblank option out of habit & haven't had any problems.

Hopefully this resolves the problem. :)
Not Resolved. :(
But, The problem is almost confirmed to be of mutter or clutter the window manager and open gl library .

I have upgraded mutter to 3.2.x from 3.0 and it has slightly helped(will confirm if it is real or placebo effect). 
```
 
libmutter0:
  Installed: 3.2.1-2
*** 3.2.1-2 0
        300 http://ftp.debian.org/debian/ unstable/main amd64 Packages
        100 /var/lib/dpkg/status
     3.0.2.1-4 0
        990 http://ftp.debian.org/debian/ testing/main amd64 Packages

```

---

### Post by deepclutch on 2012-05-13
[B][COLOR=#FF0000]People facing this issue with image rendering in browser and other applications, Kindly register with [http://www.nvnews.net/vbulletin/](http://www.nvnews.net/vbulletin/) and Help the Nvidia developer Hopefully fix this bug ASAP. Nvidia Developer is Listening.
[COLOR=DarkRed]link:[/COLOR]
[/COLOR][/B][http://www.nvnews.net/vbulletin/showpos ... stcount=27]("http://www.nvnews.net/vbulletin/showpost.php?p=2550776&postcount=27")

[B]We may need more people who faces this bug to give more inputs. Note that irrespective of distro this issue is prevalent. be it Ubuntu,Fedora or Debian.
[/B]

---

