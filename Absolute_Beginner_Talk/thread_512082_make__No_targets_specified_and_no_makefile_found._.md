---
title: "make: *** No targets specified and no makefile found.  Stop."
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-28
i have read a bunch of ppl's problems with this but as usual it seems mine is unique haha  I know make works as i just installed GLib from source using ./configure,make,make install and everything went fine!  but when i cd to the gaim-vv- folder ./ configure gives me this i'm not sure what to do, even though there are instructions haha  if i run make it gives me the error but in the source folder there are the make files and everything.  i'm just puzzled because i thought it would be fixed by installing the latest GLIB but now it's telling me weird stuff.  here's a bunch of output for u guys/girls to check out, i feel like a total noob haha not sure exactly wat the deal is here.
ps. the reason i'm installing gaim from source is cause i want to try out the video/audio version and see how well it works, and from what i saw it wasn't in synaptic.

Universe is enabled, gnusim8085 is installed.
> 
checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.12.0, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).



so i got GLIB 2.12.11 and installed it from source with ./configure,  make, make install and it worked fine!

why won't gaim be nice haha any help would be greatly appreciated and detailed posts would be beneficial as i'm still learning! 

Thanks, Alain

---

### Post by Kingsley on 2007-07-28
Why not try 
```
sudo apt-get build-dep gaim
```

And then try to configure, make, and install gaim. 

Can you link me to the audio/video version of gaim?

---

### Post by S15_88 on 2007-07-28
i'm running the command u gave me so far so good, we;ll see how she finishes, here's the link to the vv version,
[http://sourceforge.net/projects/gaim-vv/]("http://sourceforge.net/projects/gaim-vv/")

thanks, Alain

---

### Post by S15_88 on 2007-07-28
that command just updated the version of gaim i have installed, but i still can't get the video.audio one to make.  this is pissing me off cause amsn doesn't work well with my theme and it needs a plugin that it can't find!  does anyone know of other IM programs that support web cam!!!!

---

