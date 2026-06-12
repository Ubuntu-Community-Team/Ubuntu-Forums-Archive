---
title: "[SOLVED] Thunar Starts Then Disappears"
date: 2008-11-09
forum: Apple Hardware Users
---

### Post by jorel314 on 2008-11-09
I just installed Xubuntu 8.10 PPC on my iBook G4.  Everything seemed to be working great, however, when I clicked "Places > File System" The Thunar file manager opened and then closed itself right away.

Same thing happens when I start Thunar directly from Applications menu.  I can't browse my files.

Also, the Desktop icons and wallpaper dissappeared just leaving a blue background.  Every other application runs fine when launched.

This is my third clean install attempt, and it acts like this every time.  When the system starts after a clean install, the icons and desktop image are there.  As soon as I launch Thunar, the desktop icons and image disappears and I can't manage my files. 

Any help would be much appreciated.  Thanks!

---

### Post by iloveyouimissyou on 2008-11-09
jorel314,

Just to let you know you are not the only one. I just installed Xubuntu 8.10 Intrepid (build from Oct. 30th, 2008) on my PPC iBook G4 (1.44GHz) and I'm having the same problem. I have reinstalled two times and the same thing happens. Double click on a folder or Hard Drive and the thunar file manager window for that item pops up for a quick blink of an eye and then it disappears.

I am typing this on my iBook with Xubuntu installed (the second time) and the icons on the desktop haven't disappeared yet... I'm sure they will soon, the previous install they disappeared rather quickly.

So anyways. I will post back here if I find out what is going on or if there is a solution.

Thanks,
Colin McArdell
[www.colinmcardell.com](www.colinmcardell.com)

---

### Post by melojo on 2008-11-09
open a terminal and type

```
thunar
```

See what it is complaining about

---

### Post by jorel314 on 2008-11-09
@Colin hopefully, we'll find a fix soon.

@melojo

Here is the message I get when I type Thunar from the command line:

(thunar:7513): Gtk-CRITICAL **: gtk_drag_source_set_icon_name: assertion `site != NULL' failed
Segmentation fault

Any thoughts?

---

### Post by iloveyouimissyou on 2008-11-10
I tried "thunar" in a terminal with the results:

```
colin@goober:~$ thunar
Segmentation fault
colin@goober:~$ 
```

Bizarre.
I tried reinstalling Thunar and all Thunar related things from the Synaptic Package Manager with no change.

Thanks for the response!

Cheers,
Colin McArdell
[www.colinmcardell.com](www.colinmcardell.com)

---

### Post by jorel314 on 2008-11-10
I haven't found a fix for Thunar, so in the meantime, I installed an alternative file manager called PCMan.

More info here:
[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

To install:
sudo apt-get install pcmanfm

It installs into:
Applications > System > PCMan File Manager"

After launching it, I went to: 
Edit > Preferences > Desktop > Manage the desktop and show file icons

It's my first time using it, and it looks to be a lean and fast temporary solution.

---

### Post by Leslie Viljoen on 2008-11-10
I also have this problem, on a PPC Mac Mini with Intrepid. Installation went fine after the "modprobe ide-scsi" and adding the "nosplash" option to yaboot.conf (or else I just get a black screen, which I have to try and bypass by hammering on ctrl-alt-f1 during boot).

Here's my kernel:

```
uname -a
Linux maclin 2.6.25-2-powerpc #1 Tue Sep 30 14:49:00 UTC 2008 ppc GNU/Linux
```

Running Thunar I get "Segmentation Fault" mostly, but also a large list of Gtk-XYZ assertions failing.

Since XFCE seems to use Thunar to manage icons on the desktop, these die randomly, and I have to go back to settings and "allow XFCE to manage my desktop" to get them back (temporarily).

Perhaps relatedly, Celestia dies with an "X system error", Egoboo just quits to the logon screen, Funguloids runs but the music is loud white noise (strangely, since it doesn't even install on a PC)...

The Mac Mini is such a fantastic little computer, I had high hopes that Intrepid would finally be a decent OS for it! So I'm sad! Wireless is at last working great, after years of waiting and relentless hacking at it.

Anyway, for Thunar I am trying to build from source and debug it myself but I am a newb at packaging. I have managed to apt-get source Thunar and use uscan to update it to 0.9.91 and got debuild to apply patches, but don't want to download half the internet with pbuilder so I'm trying just a "./configure --enable-debug=full" and "make" to try and debug with. I'll report if I make any progress, please jump in if you have any advice!

tags: PPC powerpc macmini xubuntu xfce thunar segmentation fault

---

### Post by Leslie Viljoen on 2008-11-10
Wow, the Thunar I built doesn't segfault at all. Now I think we need someone who knows more about packaging to help!

I had to download quite a lot to build it, and I doubt this is going to help anyone as-is, but here's what I did:

(I use wajig but you can use "sudo apt-get" instead) 

```

wajig source thunar
wajig install libexo-0.3-dev dpkg-dev libdbus-glib-1-dev fakeroot
wajig install debhelper devscripts

cd thunar-0.9.0
uscan
debuild -S -us -uc
./configure --enable-debug=all
make
cd thunar
./Thunar
[no segfault!]

```

Now the built Thunar's "about" menu shows version 0.9.0, so I don't really know if uscan changed the directory I was building in, or just created the Thunar-0.9.91.tar.bz2 file in the higher directory. So I don't know what version I compiled. 

Trying to extract that 0.9.91 archive and run ./configure told me my libexo was too old, so I was perhaps just building 0.9.0 again - in which case, why didn't it segfault? Perhaps because of --enable-debug=full?
Well I have just rebuilt it again without that option, and it works too!

Doing the following seems to have now fixed Thunar for me:

```

mv /usr/bin/Thunar /usr/bin/Thunar.orig
cp ./Thunar /usr/bin

```

I can only imagine the bundled Thunar wasn't built properly. But perhaps you should give me a little time to try and reduce the above process to fewer steps (or post the binary) before you do it all.

---

### Post by Leslie Viljoen on 2008-11-10
Hmm, turns out the desktop icons disappearing aren't related to Thunar. That's xfdesktop segfaulting.

There must be some basic system incompatibility here. Perhaps all these apps were built on an older kernel and this kernel is causing them to segfault? Anyone wiser than me care to take a guess?

---

### Post by Leslie Viljoen on 2008-11-10
Ok, for Thunar you can skip the uscan. This seems to work:

```

apt-get install wajig
wajig install libexo-0.3-dev dpkg-dev libdbus-glib-1-dev fakeroot
wajig install debhelper devscripts
wajig source thunar

cd thunar-0.9.0
./configure
make
sudo make install

```

Now hide your system-installed Thunar:
```

sudo mv /usr/bin/Thunar /usr/bin/Thunar.orig

```
...and Thunar should work. I know it's a lot to download, I'd provide a proper package if I knew how to. I'll start reading about it.

For now though, I'm trying to build xfdesktop. It looks like the iso was another screw-up. Not that I'm ungrateful, this is a breeze compared to OSX and macports!

---

### Post by Leslie Viljoen on 2008-11-10
No such luck rebuilding xfdesktop. To reproduce the crash I just put an SWF file on the desktop and then try to right-click it. Crashes immediately.

Here's the backtrace:

```

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x4803ced0 (LWP 5428)]
0x0eea61a8 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
(gdb) backtrace
#0  0x0eea61a8 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
#1  0x0eea68e0 in g_slice_alloc0 () from /usr/lib/libglib-2.0.so.0
#2  0x0ef47a94 in g_object_freeze_notify () from /usr/lib/libgobject-2.0.so.0
#3  0x0f9da128 in gtk_label_set_markup () from /usr/lib/libgtk-x11-2.0.so.0
#4  0x0fae8cfc in gtk_tooltip_set_markup () from /usr/lib/libgtk-x11-2.0.so.0
#5  0x0fae8dbc in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#6  0x0fae98a0 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#7  0x0f9e9b08 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#8  0x0f804038 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#9  0x0ee7edbc in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#10 0x0ee83588 in ?? () from /usr/lib/libglib-2.0.so.0
#11 0x0ee83cc4 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#12 0x0f9ea1c4 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x1000d7a4 in main (argc=1, argv=0xbfbdf634) at main.c:394

```

---

### Post by iloveyouimissyou on 2008-11-10
Hey Leslie,

Wow,

Ok. I basically was in the same boat. I am a newbie when it comes to package and compile and source and blah blah blah... I grab a bunch of dev packages with Synaptic and got exo-0.3.0 something... (I know I'm being vague, sorry) compiled Thunar and ran it from the command line with great success, for about a minute. Then it continued doing the same thing it had been doing.

I would probably take a stab at the idea you are talking about with Xfce (xubuntu-desktop package?) having issues and segfaulting... Recompiling xubuntu-desktop maybe? I'm really lost when it comes to this, although I am definitely learning fast. Google is our friend!

Thanks everyone for the community and help! This is awesome!

Cheers,
Colin McArdell
[www.colinmcardell.com](www.colinmcardell.com)

---

### Post by jorel314 on 2008-11-10
@Leslie

Thanks for all your hard work.  I wish I knew more about Linux to help out too.

---

### Post by Leslie Viljoen on 2008-11-10
Instead of "./configure" and "make" and "make install", you can get the packager to build a new .deb package for you and it will put the files in the right places, instead of /usr/local/bin/thunar. 

If you followed my earlier instructions, you can go back to the source directory and type "sudo make uninstall" to get rid of the installed Thunar. Then type dpkg-buildpackage. Use the '-d' option if it wants you to install more dependencies - you shouldn't need to.

Once it has done its work, you can install the packages it built with:

```
cd ..
wajig install *deb
```

Perhaps that will work, since dpkg-buildpackage applies some ubuntu-specific patches. Mine is still going strong, no problems!

This approach will also allow you to reverse your changes - you'll see the original packages will show up as "updates", so if you update them you'll get the old broken packages back!

---

### Post by iloveyouimissyou on 2008-11-10
Hey!,

So I followed your steps Leslie! It's working great!

Thanks so much!

Cheers,
Colin McArdell
[www.colinmcardell.com](www.colinmcardell.com)

---

### Post by Leslie Viljoen on 2008-11-11
Yeeeehaaaa! That's great!

I found another program that crashes, with the exact same error that xfdesktop was crashing with:

```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 22132 error_code 2 request_code 134 minor_code 1)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

...and in other news, it seems that this morning, after a reboot, my rebuilt xfdesktop is not crashing any more!

Now if you have installed pcmanfm, you can set it to "manage the desktop" in its preferences and your icons will stop disappearing, or you can recompile xfdesktop using the same process as for thunar.

The pcmanfm option is less hassle though, and it seems to be even faster than Thunar. You can remove the "places" icon from your panel and add a "Launcher". Then you choose a filing cabinet icon and put "pcmanfm" in the "Command" box.

Now I wonder if there's a way to make everything work without recompiling it all!

---

### Post by Leslie Viljoen on 2008-11-11
Ok, I recompiled Totem and it still crashes when trying to go to fullscreen, even after a reboot. So don't bother trying that.

---

### Post by Leslie Viljoen on 2008-11-11
The good news is that VLC seems to work very nicely, fullscreen or not.

```
sudo apt-get install vlc
```

---

### Post by Leslie Viljoen on 2008-11-11
The "Passwords and encryption keys" program has also crashed on me. All these programs must have something in common, like a system library.

---

### Post by xobmo on 2008-11-12
Hey there, I am new, but having the same problems. Trying to work through it here, too...

---

### Post by Leslie Viljoen on 2008-11-12
Since this rebuilding is work, and takes time, and means you have to download a whole lot of -dev packages, I am going to try and rebuild and upload some of these packages. This should make things easier for everyone.

Here's the improved process for fixing Thunar, if you are having this segmentation fault problem:

[LIST=1]
[*]Click [here]("http://www.mediafire.com/?sharekey=e7c9553d17fe2396ab1eab3e9fa335cac612ab8569c87d0c") to download the packages, all to the same directory
[*]In a console, in the download directory, do:
[/LIST]

```
sudo dpkg -i *.deb
```

You may need to reboot after the install. These packages will take precedence over the ones in the repository until new versions come out - then those new versions will replace these custom ones.

---

### Post by Leslie Viljoen on 2008-11-12
jorel314: can you try my packages, and if you are happy that Thunar is working now, use the "Thread Tools" to mark this thread solved? This will help people searching on this problem.

---

### Post by jorel314 on 2008-11-13
I downloaded the .deb files you provided and Thunar seems to be working great.  Thanks for your hard work!

---

### Post by pxwpxw on 2008-11-13
> **Leslie Viljoen said:**
> Since this rebuilding is work, and takes time, and means you have to download a whole lot of -dev packages, I am going to try and rebuild and upload some of these packages. This should make things easier for everyone.

Here's the improved process for fixing Thunar, if you are having this segmentation fault problem:

[LIST=1]
[*]Click [here]("http://www.mediafire.com/?sharekey=e7c9553d17fe2396ab1eab3e9fa335cac612ab8569c87d0c") to download the packages, all to the same directory
[*]In a console, in the download directory, do:
[/LIST]

```
sudo dpkg -i *.deb
```

You may need to reboot after the install. These packages will take precedence over the ones in the repository until new versions come out - then those new versions will replace these custom ones.


All fine on my G5 - thunar, desktop,  prefs  ..., all now working at last as expected for xfce/xubuntu. Great stuff.

(I have a few local dependency issues for libthunar-vfs-1-dev, see attached, but all working so far). 

Nice work.:guitar:

---

### Post by KamiCrazy on 2008-11-13
just run sudo apt-get -f install and it will install all dependencies needed.

Then run the dpkg -i *.deb command again so that it can configure the package correctly.

---

### Post by Leslie Viljoen on 2008-11-13
Still wondering what's causing all the segfaults, I got objdump to list the dynamic symbols it finds in each file. I see the working binaries have these symbols:

__fprintf_chk
__printf_chk

The non-working ones have:

fprintf
printf



Sorted diff of working, broken:

                  > dcgettext
< __fprintf_chk
                  > fprintf
< g_dgettext
< __printf_chk
                   > printf


Perhaps they were compiled with an older libglib or something? Does this ring any bells for anyone?

Les

---

### Post by pxwpxw on 2008-11-13
> **Leslie Viljoen said:**
> Still wondering what's causing all the segfaults, I got objdump to list the dynamic symbols it finds in each file. I see the working binaries have these symbols:

__fprintf_chk
__printf_chk

The non-working ones have:

fprintf
printf



Sorted diff of working, broken:

                  > dcgettext
< __fprintf_chk
                  > fprintf
< g_dgettext
< __printf_chk
                   > printf


Perhaps they were compiled with an older libglib or something? Does this ring any bells for anyone?

Les

Beyond me, but I think you have enough info on the bug and your findings, for a launchpad bug report.
There are quite a number about thunar, and there was one about the disappearing trick for an earlier release, but I cant find it now. It needs to be fixed for powerpc releases.

---

### Post by Leslie Viljoen on 2008-11-14
Done last night:
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/297842](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/297842)

Hopefully this will get rebuilt packages into the apt repos. Then we can all just apt-get upgrade.

BTW: It would be good to know exactly which systems this is happening on. Is it all PPC machines? ie. G5 machines, and PS3?
Is it happening in Ubuntu too, or just Xubuntu?

---

### Post by pxwpxw on 2008-11-14
```

pxw@g5:~$ cat /proc/cpuinfo 
processor	: 0
cpu		: PPC970, altivec supported
clock		: 1600.000000MHz
revision	: 2.2 (pvr 0039 0202)
timebase	: 33333333
platform	: PowerMac
machine		: PowerMac7,2
motherboard	: PowerMac7,2 MacRISC4 Power Macintosh
detected as	: 336 (PowerMac G5)
pmac flags	: 00000000
L2 cache	: 512K unified
pmac-generation	: NewWorld

```

This bug is not happening in gnome-core for me, just xubuntu-desktop. 

I added my support to the launchpad bug report. 

**[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/297842](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/297842)**

Other xubuntu powerpc people please do like-wise if you want it fixed.

---

### Post by Leslie Viljoen on 2008-11-14
Fixed xfdesktop packages uploaded here:
[http://www.mediafire.com/?sharekey=e7c9553d17fe2396ab1eab3e9fa335ca14ae01059dac3289](http://www.mediafire.com/?sharekey=e7c9553d17fe2396ab1eab3e9fa335ca14ae01059dac3289)


These should stop your icons disappearing. Installation instructions here:
[http://ubuntuforums.org/showthread.php?p=6179319#post6179319](http://ubuntuforums.org/showthread.php?p=6179319#post6179319)

- Les

---

### Post by daniel-linux on 2008-12-01
thx les,

your precompiled packages worked for thunar

i just ran into the same segfault issue with epiphany browser

did u encounter that as well?

would u happen to have some deb package that works?

the one in repos seems to be giving the same error as thunar did until now

(see attach.)

daniel

---

### Post by Leslie Viljoen on 2008-12-01
> **daniel-linux said:**
> thx les,
your precompiled packages worked for thunar
i just ran into the same segfault issue with epiphany browser
did u encounter that as well?
would u happen to have some deb package that works?
the one in repos seems to be giving the same error as thunar did until now
(see attach.)
daniel

Sorry Daniel, I didn't try Epiphany so I didn't see the segfault and didn't try rebuilding.
I did get the impression that many more apps were going to give this problem because
I'm sure they were all built with some faulty library.

You can rebuild it yourself pretty easily. If you want to try, I can give you the instructions and if your rebuilt package works you can upload it with the others!

BTW: Are you running Xubuntu 8.10?

---

### Post by ph0b0s34 on 2009-04-07
Hey guys, I am running Xubuntu 8.10 on a ps3 I did everything leslie said and I am still getting segmentation fault.  This is on my PS3.  I ran all three files and then logged out logged in no matter what i do I still get the windows that disappear and my desktop icons the whole works... so this did not fix it for me.  Help!

---

