---
title: "All &quot;Low Memory&quot; Threads missing the point"
date: 2008-12-17
forum: Apple Hardware Users
---

### Post by rtobyr on 2008-12-17
I have a system with 128MB. After weeks of following instructions on the many threads about low memory systems, I have come to the conclusion that--on contemporary versions of Ubuntu, Debian, or any distro, Xorg is not suitable for these systems. I've tried Openbox, Fluxbox, IceWM, and others, but it's always the Xorg process eating most of my memory. Openbox seems like the smallest WM, but even the old Debian Etch + Xorg + Openbox seems to want > 128MB.

Like I said, while looking at "top," I've seen that Xorg is using more memory than any other process. So I'd like to start a thread where people can give advice about Xorg alternatives on recent (Hardy or better) versions of Ubuntu. I've looked all over for information on TinyX, but I can't seem to figure it out. I would love to get instructions on Ubuntu Hardy or Intrepid + TinyX, fbdev, or some other Xorg alternative. Maybe even run the latest Ubuntu with Xorg or XFree86 from a much older release?

Yeah, I know I could just run Damn Small, Puppy, or one of those, but they're just not as slick as Ubuntu.

---

### Post by rtobyr on 2008-12-17
I have an iMac G3 with 128MB. After weeks of following instructions on the many threads about low memory systems, I have come to the conclusion that--on contemporary versions of Ubuntu, Debian, or any distro, Xorg is not suitable for these systems. I've tried Openbox, Fluxbox, IceWM, and others, but it's always the Xorg process eating most of my memory. Openbox seems like the smallest WM, but even the old Debian Etch + Xorg + Openbox seems to want > 128MB.

To make matters worse, none of the mini distros that I've found (Damn Small, Puppy, etc) both 1) have PowerPC builds and 2) don't use Xorg.

Like I said, while looking at "top," I've seen that Xorg is using more memory than any other process. So I'd like to start a thread where people can give advice about Xorg alternatives on recent (Hardy or better) versions of Ubuntu. I've looked all over for information on TinyX, but I can't seem to figure it out. I would love to get instructions on Ubuntu Hardy or Intrepid + TinyX, fbdev, or some other Xorg alternative. Maybe even run the latest Ubuntu with Xorg or XFree86 from a much older release?

---

### Post by kellemes on 2008-12-17
[https://help.ubuntu.com/community/InstallingUbuntuLite]("https://help.ubuntu.com/community/InstallingUbuntuLite")

For more info on getting a xvesa or tinyx-server running on Ubuntu keep an eye on [this place]("http://groups.google.com/group/ubuntulite").

Hope it helps.

Edit: Another interesting thread.. [http://www.linuxquestions.org/questions/linux-newbie-8/debian-xvesa-directfb-xfbdev-base-install....without-x-midrange-machine-643443/]("http://www.linuxquestions.org/questions/linux-newbie-8/debian-xvesa-directfb-xfbdev-base-install....without-x-midrange-machine-643443/")

By the way, after removing xorx you may wonder if Ubuntu still is that slick. ;-)
Personally for low spec systems I find nothing more slick as Puppy.

---

### Post by Bakerconspiracy on 2008-12-17
Hate to say it, but I think Xorg coupled with X11 is almost essential to running a nice GUI. I would be very interested in some alternatives though - if you run into any.

---

### Post by paul_mcl on 2008-12-18
>> To make matters worse, none of the mini distros that I've found (Damn Small, Puppy, etc) both 1) have PowerPC builds and 2) don't use Xorg.

You can try Finnix LiveCD ([http://www.finnix.org](http://www.finnix.org)), direct download link for powerpc iso:
[http://www.finnix.org/releases/92.1/finnix-ppc-92.1.iso](http://www.finnix.org/releases/92.1/finnix-ppc-92.1.iso)

---

### Post by bapoumba on 2008-12-18
Threads merged.

---

### Post by kerry_s on 2008-12-18
no way xorg is using 128mb memory!
you must be talking over all memory use?

i use a custom debian lenny install on 450mhz 256mb ram.

---

### Post by jdong on 2008-12-18
You guys do realize a lot of application resource usage gets "blamed" on X.org, right? i.e. another application displaying a large graphical resource could show up as X.org.

---

### Post by rtobyr on 2008-12-18
First of all, Xorg is not using 128MB. But Xorg + everything else that Linux needs to run IS using > 128MB.

Okay, so here's what I've found out:

[LIST=1]
[*]Xorg doesn't use as much memory depending on the window manager.
[*]It's possible to run Xorg WITHOUT a window manager. In this scenario, you'll have 50-60 MB free with Xorg running. You get a terminal window, and you can type in commands, such as "firefox," and it'll run, but without window borders or minimize/maximize controls.
[*]There *is* a smaller WM than OpenBox: Matchbox (it's supposed to be for embedded devices). I just discovered Matchbox, and found that with the Matchbox WM, I still have 30MB free. It's in the repos, so you can apt-get it.
[/LIST]

---

### Post by kerry_s on 2008-12-18
> **rtobyr said:**
> First of all, Xorg is not using 128MB. But Xorg + everything else that Linux needs to run IS using > 128MB.

Okay, so here's what I've found out:

[LIST=1]
[*]Xorg doesn't use as much memory depending on the window manager.
[*]It's possible to run Xorg WITHOUT a window manager. In this scenario, you'll have 50-60 MB free with Xorg running. You get a terminal window, and you can type in commands, such as "firefox," and it'll run, but without window borders or minimize/maximize controls.
[*]There *is* a smaller WM than OpenBox: Matchbox (it's supposed to be for embedded devices). I just discovered Matchbox, and found that with the Matchbox WM, I still have 30MB free. It's in the repos, so you can apt-get it.
[/LIST]

now are you talking custom install or full install than modified?

if you start from the base and build up you'll have more control of whats used.
as a example compare your pstree to mine:

---

### Post by jdong on 2008-12-18
> **kerry_s said:**
> now are you talking custom install or full install than modified?

if you start from the base and build up you'll have more control of whats used.
as a example compare your pstree to mine:

No, I'm talking about **ANY** use of X11. Have an app use an X11 API call to put a 1GB pixmap on screen. You'll notice Xorg's process takes the 1GB consumption hit. Don't rely too much on the RAM consumption figures that are given by various process monitors -- on a shared-resource operating system like all modern operating systems, measuring memory consumption of processes is an extremely tricky task and there's few tools that do it right. there are a set of kernel patches from a while ago that do a fairly good job of this, and were used in the GNOME vs KDE memory usage benchmarks. Even then, it sparked a long lkml thread between experienced kernel developers on whether or not the methodology was correct.

---

### Post by stream303 on 2008-12-19
Jdong and the others are right - even though you may get your desktop environment or window manager down to using less ram, as soon as you bring up a gui app of any significance, you are going to be thrashing the disk again.

This is why I cringe when I see the recommendation to just run Xubuntu for 64 or 128mb machines.  It isn't a panacea, even though your desktop might be a bit faster.

In the end, to make up for minimal ram, there is nothing like the commandline, OR possibly apps that use ncurses like nano, mc, etc.  Run the default TWM window manager if you like, but you'll still have to find the proper balance between your "desktop" and the ram that an app uses once launched and running.  It all depends on your needs.

You could run these inside a minimal X environment from within xterm, or some other terminal application.  Need just a bit more gui?  How about using "leafpad" as your editor.  Don't like xterm or their equivalents?  Perhaps xfce4-terminal will do.  Does Brasero eat up too much ram?  Use wodim in a terminal.

Getting Ubuntu (or any flavor of Linux) running a low-mem ppc box might mean disappointment for quite a few unless they look at the box from a different viewpoint - the low memory will force you to become familiar with commandline apps and setup to make your ram usage the most efficient.

This alone is a GREAT purpose for low-mem machines if you want to learn the cli.  There just aren't that many other useful gui distractions to keep you from hitting the books. :)

I don't want to start a cli-thread, since that has been covered elsewhere, but from a practical point of view, that is where one is headed with low-memory.  I look at it as a positive thing really, but the cli isn't everyone's cup of tea.

There are a few threads about everyone's favorite cli-apps around - oops forgot another one for music:  Aside from my favorite ogg123 inside vorbis-tools, many like MOC since it is an ncurses-gui.  There are many others.  Elinks might be useful for web-browsing, but if it is too sparse, it and even Lynx make for nice ncurses-based minimal local file managers, ie with *lynx /usr/share/doc* etc.  Oh, forget Gimp with 64mb.  Try installing imagemagick, and then looking at your jpgs with *display wedding.jpg* ...

I could go on, but there is a whole world of ncurses based apps one can run in a gui terminal if they are adverse to a raw commandline.

...just some thoughts....

---

### Post by jdong on 2008-12-19
stream303 has a great point -- I have a 64MiB RAM system that runs a slightly modified Ubuntu and X.org, but all it uses the GUI is to use a minimalist WM to tile a few xterms more conveniently/intuitively than screen can do it, not to mention show more characters per page.

Unfortunately these days the average Linux desktop apps are not designed to work on systems with 128MB RAM; there have been design decisions to use more RAM for the sake of performance or programming convenience, and nobody has been showing real interest in changing that.

With that said there are embedded GTK devices like the Maemo platform that run just fine on limited RAM, even using a Gecko based browser, so I wouldnt rule anything out... just use a smaller screen to reduce pixmap sizes ;-)

---

### Post by rtobyr on 2008-12-19
> In the end, to make up for minimal ram, there is nothing like the commandline, OR possibly apps that use ncurses like nano, mc, etc.

I have mixed feelings about that. Sure, running CLI apps when I can is fine, but Lynx just doesn't do it for me. Now, if Firefox could run without X, using only the framebuffer to render HTML as it was meant to be seen, then that would be great.

Look at the mini distros, like DSL, and DSL-N. DSL-N runs a modern (2.6) kernel, and can show me a GUI desktop using less than 24MB total RAM. The problem there is that they don't make DSL, DSL-N, or any of those other cool little distros for PPC.  But my point is this: if DSL, DSL-N, Puppy Linux, Slitaz, and others can run fine on <64MB, then why can't any of the many posts you can find here about recommendations for low memory systems show us how to configure Ubuntu or Debian to do the same?

Well, I'm working on changing that. Already I've found that by using Matchbox as my WM, I only use about 100MB. And yes, I know that if I launch a huge app, or many apps, then I'll be thrashing my disks. But at least I can run Firefox, and maybe a couple of others (but not concurrently).

---

### Post by cyberdork33 on 2008-12-19
I like the framebuffer. There are a lot of apps that can use it for image display, web browsing, etc. It can even make your commandline terminal look pretty.

---

### Post by rtobyr on 2008-12-19
IMO, it would be cool if Firefox were its own OS. Just add some hardware drivers, support for some filesystem, and a utility to manage files. Then I can do the rest of my computing in the cloud. Yay for Google Docs. OK, I know it wouldn't be simple or easy, but it would be very cool, and a boon for people trying to revive old computers.

---

### Post by cb951303 on 2008-12-19
@OP: Luckily for you, there is a more lightweight X server implementation on the way coded by a Red Hat programmer.

[http://www.phoronix.com/vr.php?view=13065](http://www.phoronix.com/vr.php?view=13065)

---

### Post by stream303 on 2008-12-19
> **rtobyr said:**
> Now, if Firefox could run without X, using only the framebuffer to render HTML as it was meant to be seen, then that would be great.

I see what you're saying. :)

Although lynx doesn't do it for you, a step up might be elinks, although it gets closer to the ideal, it just isn't in the same league.  A step up from that is dillo, but it could use some work.  I understand that there are some new improvements, but of course it can't hold a candle to the big-guns.  I'd love to see improvements there.  One could also try using Epiphany-browser since it uses the same gecko engine as Firefox (soon to be webkit for an engine), but it starts creeping up the ram scale too.

Currently the only framebuffer environment I know of is FreeDos, and the Arachne browser.  Check it out:

[http://linuxhelp.blogspot.com/2006/09/concise-guide-to-installing-and-using.html](http://linuxhelp.blogspot.com/2006/09/concise-guide-to-installing-and-using.html)

Although it doesn't work on ppc, but it might be inspirational.

One last cheer for the cli - for the most part, it has been working nearly the same way for 40 years, and will most likely be working the same way for 40 more.  Desktop environments will come and go, but if you are into *nix for the long haul, the cli is an investment in yourself that transcends hardware and desktop software improvements.  I spend a lot of time learning how to configure gnome, kde and whatnot, but that knowledge is only applicable for perhaps 5 years before it changes again.  "ls" in the cli is something I don't think about anymore. :)

I think I know where you are coming from.  Perhaps a nice project would be to get the arachne browser working natively under Linux!

---

### Post by kerry_s on 2008-12-19
> **rtobyr said:**
> IMO, it would be cool if Firefox were its own OS. Just add some hardware drivers, support for some filesystem, and a utility to manage files. Then I can do the rest of my computing in the cloud. Yay for Google Docs. OK, I know it wouldn't be simple or easy, but it would be very cool, and a boon for people trying to revive old computers.

:lolflag:
[http://pyrodesktop.org/Main_Page](http://pyrodesktop.org/Main_Page)

---

### Post by cyberdork33 on 2008-12-19
> **stream303 said:**
> I see what you're saying. :)

Although lynx doesn't do it for you, a step up might be elinks, although it gets closer to the ideal, it just isn't in the same league. 
links2 -g

---

### Post by stream303 on 2008-12-20
Now that's cool!  I didn't know about links -g !

(on my opensuse box for now, and can't find links2 yet)

That didn't even tickle the ram that much either.  Nice!

---

### Post by cyberdork33 on 2008-12-22
> **stream303 said:**
> Now that's cool!  I didn't know about links -g !

(on my opensuse box for now, and can't find links2 yet)

That didn't even tickle the ram that much either.  Nice!

you can even set it to use different drivers. svgalib, framebuffer, etc

---

