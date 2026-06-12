---
title: "Need to remove nvidia drivers to install proper arch nvidia package"
date: 2008-10-08
forum: Arch and derivatives
---

### Post by roger99 on 2008-10-08
Hi all,

I switched to arch about a month ago from ubuntu, so far i'm loving it and having no problems, everythings setup exactly as I want it and my systems running smooth as silk.  Ubuntu gave me a good knowledge base to love setting up arch from scratch and now I know even more about linux, well arch in particular anyway.

One thing that hasn't set me in good stead from ubuntu though is nvidia drivers.  I'd gotten into a habit of allways installing the latest beta .pkg from nvidia's site as my 8600m didn't perform very well with the older drivers.  So naturally when I first installed arch when it came to the nvidia drivers I went straight to the nvida site, got the beta drivers and installed them just as I would have in ubuntu, this worked a treat and I havn't thought about it since.

Well, now I've truly realised that arch's repo's arn't frozen and kept upto date, i'd like to install the non beta nvidia driver - 177.80 - using pacman except ------

```
:: Retrieving packages from extra...
 nvidia-utils-177.80...     9.6M  127.6K/s 00:01:17 [#####################] 100%
 nvidia-177.80-1-x86_64     2.5M  134.3K/s 00:00:19 [#####################] 100%
checking package integrity...
(2/2) checking for file conflicts                   [#####################] 100%
error: could not prepare transaction
error: failed to commit transaction (conflicting files)
nvidia-utils: /usr/bin/nvidia-bug-report.sh exists in filesystem
nvidia-utils: /usr/bin/nvidia-settings exists in filesystem
nvidia-utils: /usr/bin/nvidia-xconfig exists in filesystem
nvidia-utils: /usr/lib/libGL.so.1 exists in filesystem
nvidia-utils: /usr/lib/libGLcore.so.1 exists in filesystem
nvidia-utils: /usr/lib/libXvMCNVIDIA.a exists in filesystem
nvidia-utils: /usr/lib/libXvMCNVIDIA_dynamic.so.1 exists in filesystem
nvidia-utils: /usr/lib/libcuda.so.1 exists in filesystem
nvidia-utils: /usr/lib/libnvidia-tls.so.1 exists in filesystem
nvidia-utils: /usr/lib/xorg/modules/drivers/nvidia_drv.so exists in filesystem
nvidia-utils: /usr/share/applications/nvidia-settings.desktop exists in filesystem
nvidia: /lib/modules/2.6.26-ARCH/kernel/drivers/video/nvidia.ko exists in filesystem
Errors occurred, no packages were upgraded.
```

So now to the real meat of my post, how do I go about removing the nvidia driver that was installed using nvidia's .pkg so that I can install the drivers using pacman.

I take it just deleting the above files is *NOT* a good idea.  Any advice here would be most welcome.

Thanks

---

### Post by roger99 on 2008-10-08
okay, so this was easily solved my running "nvidia-installer --uninstall"

---

### Post by mips on 2008-10-09
In future if you want to install the latest beta drivers just use Yaourt and install from AUR. yaourt -S nividia-beta, there are other packages as well so maybe do a search first

---

### Post by roger99 on 2008-10-13
Hi, bit of a slow reply but, thanks for the advice.  Still feeling my way round the arch system, and getting used to pacman and AUR etc. 

Yaourt confused me the first time I ran it I must admit, when it recommened that I edit the pkgbuild so I said yes and was left looking at something I didnt really understand :) Got the general jist but you know how it is when you first look at something new.:( Anyways, I've sussed now that you don't necessarily have to edit it even though it recommends that you do !! 

I'm loving Arch but having real problems with my nvidia drivers, spent the last few days pulling my hair out trying to work out why everything is so slow.  Going over all the google results I could find, posts on Arch's Wiki and forums, these forums etc  But to no avail.

I cannot get things to run quickly compared to ubuntu.  I know loads of people are gonna moan about these programs not being *real* benchmarks and everything but glxgears ( with pacman's nvidia package, or the .pkg.run from nvidias site - 177.80 ) only gets 80fps when running using a standalone compiz setup, and about 900fps under openbox, where as Gtkperf under compiz runs 100 iterations in about 160 secs and 1000 interations under openbox runs in about 85 secs.

Performance is terrible as to a Ubuntu setup 6 months ago when the nvidia drivers were supposedly worse.  This is after following all performance tweaks from the nvidia forum and from anywhere else that I can glean other tweaks.

I'm allmost at the point of giving up trying to run a standalone compiz and go back to good old openbox, which after a few weeks of configuring is setup to perfection now, but I would also like to solve the problem of why my graphics card is performing so badly under arch.

---

### Post by MisfitI38 on 2008-10-13
Besides glxgears, is performance poor? Have you tried any 3d games?

---

### Post by roger99 on 2008-10-13
I havnt tried any games yet no, I have xscreensaver running an opengl module and it's painful under compiz.  Not really much of a games player anymore, is there anything in arch repos that I could quickly install and test with?

All I know is I was getting much better performance under ubuntu.  Maybe its something that the ubuntu devs have patched maybe!?

Is anyone else with a similar setup seeing similar results? better? worse!:(

---

### Post by fwojciec on 2008-10-13
> **roger99 said:**
> I cannot get things to run quickly compared to ubuntu.  I know loads of people are gonna moan about these programs not being *real* benchmarks and everything but glxgears ( with pacman's nvidia package, or the .pkg.run from nvidias site - 177.80 ) only gets 80fps when running using a standalone compiz setup, and about 900fps under openbox, where as Gtkperf under compiz runs 100 iterations in about 160 secs and 1000 interations under openbox runs in about 85 secs.

This is very likely a configuration issue -- 80fps... Is your monitor vertical refresh rate 80Hz?  If so, the benchmark results are a result of "Sync to VBlank" setting enabled in nvidia settings.  You can disable it (in the "OpenGL settings" tab of nvidia-settings).  [This]("http://www.nvnews.net/vbulletin/showthread.php?t=106746") is also an interesting read, in particular post #13 describes well how to configure things to have Compiz work smoothly.

---

### Post by roger99 on 2008-10-14
> **fwojciec said:**
> This is very likely a configuration issue -- 80fps... Is your monitor vertical refresh rate 80Hz? 

Unfortunatly my monitor refreshes at 60Hz, so that rules that little idea out plus the frame rate in glxgears isn't rock solid, it can drop and rise (mostly drop though)  and I don't have any sync to vblank options enabled,  ( i've been through it all, on / off, on again, off again ](*,) )

One route I haven't been down yet is setting up the driver through modprobe options.  Currently trying to read up on which options I may be able to use.

Plus I've just created another issue for myself.


Execert from Nvidia's Readme.
```

The NVIDIA Accelerated Linux Graphics Driver consists of the following
components (filenames in parenthesis are the full names of the components
after installation; "x.y.z" denotes the current version. In these cases
appropriate symlinks are created during installation):

   o An X driver (/usr/X11R6/lib/modules/drivers/nvidia_drv.so); this driver
     is needed by the X server to use your NVIDIA hardware.

   o A GLX extension module for X
     (/usr/X11R6/lib/modules/extensions/libglx.so.x.y.z); this module is used
     by the X server to provide server-side GLX support.

   o An X module for wrapped software rendering
     (/usr/X11R6/lib/modules/libnvidia-wfb.so.x.y.z and optionally,
     /usr/X11R6/lib/modules/libwfb.so); this module is used by the X driver to
     perform software rendering on GeForce 8 series GPUs. If libwfb.so already
     exists, nvidia-installer will not overwrite it. Otherwise, it will create
     a symbolic link from libwfb.so to libnvidia-wfb.so.x.y.z.

   o An OpenGL library (/usr/lib/libGL.so.x.y.z); this library provides the
     API entry points for all OpenGL and GLX function calls. It is linked to
     at run-time by OpenGL applications.

   o An OpenGL core library (/usr/lib/libGLcore.so.x.y.z); this library is
     implicitly used by libGL and by libglx. It contains the core accelerated
     3D functionality. You should not explicitly load it in your X config file
     -- that is taken care of by libglx.

   o Two XvMC (X-Video Motion Compensation) libraries: a static library and a
     shared library (/usr/X11R6/lib/libXvMCNVIDIA.a,
     /usr/X11R6/lib/libXvMCNVIDIA.so.x.y.z); see Appendix G for details.

   o A kernel module (/lib/modules/`uname -r`/video/nvidia.o or
     /lib/modules/`uname -r`/kernel/drivers/video/nvidia.o); this kernel
     module provides low-level access to your NVIDIA hardware for all of the
     above components. It is generally loaded into the kernel when the X
     server is started, and is used by the X driver and OpenGL. nvidia.o
     consists of two pieces: the binary-only core, and a kernel interface that
     must be compiled specifically for your kernel version. Note that the
     Linux kernel does not have a consistent binary interface like the X
     server, so it is important that this kernel interface be matched with the
     version of the kernel that you are using. This can either be accomplished
     by compiling yourself, or using precompiled binaries provided for the
     kernels shipped with some of the more common Linux distributions.

   o OpenGL and GLX header files (/usr/include/GL/gl.h,
     /usr/include/GL/glext.h, /usr/include/GL/glx.h, and
     /usr/include/GL/glext.h); these are also installed in
     /usr/share/doc/NVIDIA_GLX-1.0/include/GL/. You can request that these
     files not be included in /usr/include/GL/ by passing the
     "--no-opengl-headers" option to the .run file during installation.

   o The nvidia-tls libraries (/usr/lib/libnvidia-tls.so.x.y.z and
     /usr/lib/tls/libnvidia-tls.so.x.y.z); these files provide thread local
     storage support for the NVIDIA OpenGL libraries (libGL, libGLcore, and
     libglx). Each nvidia-tls library provides support for a particular thread
     local storage model (such as ELF TLS), and the one appropriate for your
     system will be loaded at run time.

   o The application nvidia-installer (/usr/bin/nvidia-installer) is NVIDIA's
     tool for installing and updating NVIDIA drivers. See Chapter 4 for a more
     thorough description.


Problems will arise if applications use the wrong version of a library. This
can be the case if there are either old libGL libraries or stale symlinks left
lying around. If you think there may be something awry in your installation,
check that the following files are in place (these are all the files of the
NVIDIA Accelerated Linux Graphics Driver, as well as their symlinks):

    /usr/X11R6/lib/modules/drivers/nvidia_drv.so

    /usr/X11R6/lib/modules/extensions/libglx.so.x.y.z
    /usr/X11R6/lib/modules/extensions/libglx.so -> libglx.so.x.y.z

    (may also be in /usr/lib/modules or /usr/lib/xorg/modules)

    /usr/lib/libGL.so.x.y.z
    /usr/lib/libGL.so.x -> libGL.so.x.y.z
    /usr/lib/libGL.so -> libGL.so.x

    /usr/lib/libGLcore.so.x.y.z
    /usr/lib/libGLcore.so.x -> libGLcore.so.x.y.z

    /lib/modules/`uname -r`/video/nvidia.o, or
    /lib/modules/`uname -r`/kernel/drivers/video/nvidia.o

If there are other libraries whose "soname" conflicts with that of the NVIDIA
libraries, ldconfig may create the wrong symlinks. It is recommended that you
manually remove or rename conflicting libraries (be sure to rename clashing
libraries to something that ldconfig will not look at -- we have found that
prepending "XXX" to a library name generally does the trick), rerun
'ldconfig', and check that the correct symlinks were made. Some libraries that
often create conflicts are "/usr/X11R6/lib/libGL.so*" and
"/usr/X11R6/lib/libGLcore.so*".
```

So I removed the nvidia driver last night and went through my system renaming any possible conflicting files that are mentioned in the README.  Then re-installed the pacamn nvidia & nvidia-utils package hoping to start from a completly clean base.

However, this morning as I ran compiz I now get an error to do with not being able to find libGLU.so.  Which is not one the files I renamed so I presume it will be a symbolic link somewhere along the line,  Strangly compiz now claims that "This will not work, yet it works just as well as it did before, with the basic set of plugins that I use (basically just desktop wall and emerald, don't go in for too much fancy-ness but I am a bit partial to translucent title bars :) )  Although on further examination, ccsm won't allow me to select any fancier effects such as expo or animations, blur etc etc.

Anyway, i'm gonna carry on fiddling, to see wot else I can screw up just to get fluid eye-candy :)

---

### Post by kpkeerthi on 2008-10-15
There is nvidia-beta in AUR

---

