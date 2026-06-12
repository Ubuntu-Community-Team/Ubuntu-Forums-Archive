---
title: "pacbuilder"
date: 2008-09-21
forum: Arch and derivatives
---

### Post by crimesaucer on 2008-09-21
Who uses pacbuilder? Any tips or suggestions.


I've edited my makepkg.conf with my proper CFLAGS and decided to re-compile my entire system. (sort of like gentoo, but with the ease of Arch)


I'm currently having difficulty with rebuilding some of packages.... but it seems like it worked for about 480 out of 580 of the packages on my computer. 


Once I'm finished with everything, I'll see it there is any noticable differences.

---

### Post by Pogeymanz on 2008-09-21
I'd be very interested in seeing how it works for you. I've been thinking of trying it myself, but I'd like to know if it's worth it first.

---

### Post by crimesaucer on 2008-09-22
> **Pogeymanz said:**
> I'd be very interested in seeing how it works for you. I've been thinking of trying it myself, but I'd like to know if it's worth it first.

I recompiled most of my computer..... I had more problems with gnome than I did with xfce4. I'm using pacbuilder as my first attempt to install any new apps, usually it works.


Basically, if it doesn't build correctly, it will list what failed and wasn't installed, then you can run the --deplist flag to see the dependencies that might not be building correctly, and then either figure it out or just do a lazy install of the deps using regular pacman, and then try to build the failed apps again with pacbuilder to get the important app to be customized.

```

-------------------------------
 PacBuilder, by Andrea Cimitan 
-------------------------------

A tool to massively recompile packages from sources
It currently fetches both ABS and AUR

USAGE:
  pacbuilder [options] package|repository

OPTIONS:
  General:
    --help                print this help
    --clean               remove previous log
    --gccinfo             print current compilation flags
    --nocolor             do not use any color
    --notitle             do not print the title
    --noresume            do not resume
  Install:
  (-S),    --install      build specified packages
  (-S) -b, --builddeps    build and install the dependencies
  (-S) -e, --edit         be verbose and edit PKGBUILD
  (-S) -f, --force        force install, overwrite conflicting files
  (-S) -k, --keepdeps     keep makedepends after install
  (-S) -u, --sysupgrade   build the updated packages
  (-S) -v, --verbose      print makepkg output
  Additional parameters:
    -p, --pretend         print the final list of packages to be installed
    -n, --noconfirm       do not ask for any confirmation
    -m, --match <regex>   only install packages matching <regex>
    -d, --deplist         recursively list all dependencies first
  Type:
    --world               recompile both deps and explicit
    --explicit            recompile explicitely installed packages
    --devel               recompile only installated devel packages
  Target repository:
    --core                recompile packages in core
    --extra               recompile packages in extra
    --testing             recompile packages in testing
    --community           recompile packages in community
    --aur                 recompile packages in aur


```


Right now I'm on a zen2 patched 2.6.26 kernel (custom CFLAGS,CXXFLAGS,MFLAGS) nice settings for a Desktop, with 1000HZ timing.


using the xfce4 desktop built from pacbuilder with these CFLAGS/CXXFLAGS for my AMD Turion 64X2 TL-60: -march=athlon64 -msse3 -O2 -pipe

and these MAKEFLAGS: -j3

I also used the Firefox-Optimized package from the AUR, and everything is SO FAST and solid.


I'm loving it.

---

### Post by K.Mandla on 2008-09-25
I've used it, but I felt like recompiling Arch was a step sideways, and if I was going to go through all that work, I might as well start with a source distro. Enter Crux. ...

---

### Post by crimesaucer on 2008-09-25
> **K.Mandla said:**
> I've used it, but I felt like recompiling Arch was a step sideways, and if I was going to go through all that work, I might as well start with a source distro. Enter Crux. ...

I tried a gentoo live cd install (twice), I screwed up the first install and realized it half way through it, then went back and did it the EXACT correct way as described in the AMD64 handbook..... I checked/rechecked every step and had no problems until I rebooted..... All that work, 2 days of working in console and most importantly the last day of knowing that I followed every step correctly..... and all I was left with was a grub screen that was unable to boot into either Gentoo or Vista.


Then using the Arch live FTP cd, and the FTP install method, I had a fully operational computer in less than an hour. Then I uploaded my AMD64 zen2 kernel which I had saved on my Vista partition (another 5 minutes of editing /boot/grub/menu.lst).....  Then another 5 minutes to install my nvidia-beta, and then about a Full 24 hours of:

```
sudo pacbuilder --builddeps --keepdeps --verbose --noconfirm --world"
```


..... which did a recompile of my entire computer (about 500 apps) and all of their deps/makedeps....


About 125 apps failed, so then I checked them out individually and was able to fix 25 of them by using regular pacman to install the binary dependencies that wouldn't compile correctly so that the actual package could compile and install using pacbuilder.....


All in all, it took about 2 days of installing/recompiling/and then recompiling the failed packages again (and I still had a completely working computer through all of it so I was able to browse the Internet and fix all of my configurations).... 


Now my laptop is completely optimized for my AMD Turion 64x2 TL-60, with just a few apps/libs using the generic binaries. Everything is very, very fast (I'm using xfce4 as my Desktop). I had estimated that it would of took this long using Gentoo..... and the Arch install is so much easier plus nvidia actually works out-the-box with the nvidia and nvidia-utils package.


Plus, now all I have to do is use pacbuilder for my updates and new packages..... unless I see one of my apps that can't compile correctly, then I'll update with regular pacman..... if anything goes wrong or if I need an app on the fly, I can just use pacman to quickly install the binary and then recompile it later.....

---

### Post by fwojciec on 2008-09-25
> **crimesaucer said:**
> Now my laptop is completely optimized for my AMD Turion 64x2 TL-60, with just a few apps/libs using the generic binaries. Everything is very, very fast (I'm using xfce4 as my Desktop).

It would be just as fast with generic kernel and standard packages :P

---

### Post by crimesaucer on 2008-09-25
> **fwojciec said:**
> It would be just as fast with generic kernel and standard packages :P

I've used Arch with xfce4 for over a year..... this is faster. I've used the generic kernel, the generic kernel with the timer up to 1000HZ, the zenmm kernels both generic and AMD64, and now my own vanilla AMD64 kernel with the zen2 patch. I've also messed with different preemption settings.... and of course the zen cflags and nice options.


I've monitored the dmesg for every one and fixed a few things that were errors in the generic kernel26. 


Using the AMD64 kernel instead of generic x86_64 fixed my broken high resolution error as well as lapic error on my dmesg. I've seen on google that others have had issues with this and that it is supposedly bad for the life of the battery (?) as well some other things.


So why not go the whole distance and try to make all of my other apps match my AMD64 kernel rather than just generic? Gentoo users swear by this.


It might only be a slight improvement, but it is an improvement, and now it's over, all I have to do is maintain..... it only took 2 days. People don't have to do this if they don't want too, but some of us enjoy it. Arch gives the opportunity to use both source and binary. Why not take advantage of the ABS/AUR and pacbuilder if it exists?

---

### Post by crimesaucer on 2008-09-25
[http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-07/msg02543.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-07/msg02543.html)

From the old generic x86_64

```
Clockevents: could not switch to one-shot mode: lapic is not functional.
Could not switch to high resolution mode on CPU 0
Clockevents: could not switch to one-shot mode: lapic is not functional.
Could not switch to high resolution mode on CPU 1

```

From zen2 AMD64:

```
Switched to high resolution mode on CPU 0
Switched to high resolution mode on CPU 1

```

---

### Post by MisfitI38 on 2008-09-25
There is no harm in ricing, as long as you end up with a usable system. :)

---

### Post by crimesaucer on 2008-09-26
> **MisfitI38 said:**
> There is no harm in ricing, as long as you end up with a usable system. :)

Everything works for me except for suspend/hibernate..... I think the "-ARCH" patch has something to do with that, because when I build a vanilla kernel without the -ARCH patch, and follow the same steps for pm-suspend, it never will come out of a suspended state.


I've tried tuxonice and uswsusp and neither way will work, and regular pm-suspend will only work with the -ARCH kernel.

---

