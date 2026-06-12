---
title: "libdvdcss2, avi and other multimedia files for ppc64."
date: 2009-10-20
forum: Apple Hardware Users
---

### Post by casbahdk on 2009-10-20
I am trying to migrate from OS X to Ubuntu PPC64 on my Apple G5, as my only OS. I have installed the ubuntu restricted package, but still lack libdvdcss2, .avi support and diverse other media files. What do I need to do to get these packages?

I would also like to be able to use YouTube and am wondering what solution is doable when there is no flash player for ppc linux...

All advice is welcome.

---

### Post by Bachstelze on 2009-10-20
libdvdcss2 is easy to compile from source. For .avi files, it's a matter of what codec the video streams are encoded in (AVI is just a container), so you will have to investigate on a case-by-case basis. For Youtube, I guess you're out of luck.

---

### Post by oswaldkelso on 2009-10-20
youtube works fine with a little work.

[http://ubuntuforums.org/showthread.php?t=1269122&](http://ubuntuforums.org/showthread.php?t=1269122&)

There is also abby now for a gui on youtube. It has the advantage of listing all video links on the page making it easy to grab multiple videos.

---

### Post by casbahdk on 2009-10-21
> **oswaldkelso said:**
> youtube works fine with a little work.

[http://ubuntuforums.org/showthread.php?t=1269122&](http://ubuntuforums.org/showthread.php?t=1269122&)

There is also abby now for a gui on youtube. It has the advantage of listing all video links on the page making it easy to grab multiple videos.

Cheers. The Firefox add-ons plus VLC seem to work best for me (so far), with regards to YouTube et.al.

clive and abby seem to be AWOL in the Ubuntu PPC repositories.

---

### Post by casbahdk on 2009-10-21
> **Bachstelze said:**
> libdvdcss2 is easy to compile from source. For .avi files, it's a matter of what codec the video streams are encoded in (AVI is just a container), so you will have to investigate on a case-by-case basis. For Youtube, I guess you're out of luck.

Thanks for the quick reply. Does Medibuntu contain PPC and PPC64 packages? Do PPC users add Medibuntu using the normal procedure as listed [here]("https://help.ubuntu.com/community/Medibuntu")? Does Medibuntu have a PPC version of libdvdcss2 in the repository?

I am nervous about compiling from source as I have extremely limited experience. If something goes wrong with this lib, it can destabilize the system. I have tried this with Debian Lenny PPC.

---

### Post by oswaldkelso on 2009-10-21
> I am nervous about compiling from source as I have extremely limited experience. If something goes wrong with this lib, it can destabilize the system. I have tried this with Debian Lenny PPC.

There is no need to compile much if anything on Debian Lenny PPC for normal desktop use. To get multimedia working just add the Debian multimedia repos to your sources.list. Add the multimedia key and update.


deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) lenny main 
deb-src [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) lenny main 

deb [ftp://ftp.debian-multimedia.org/](ftp://ftp.debian-multimedia.org/) lenny main 
deb-src [ftp://ftp.debian-multimedia.org/](ftp://ftp.debian-multimedia.org/) lenny main 

This repo holds "patent encumbered software" i.e. software that may or may not be free but has patent problems in USA where Debian is based. In other countries there may not be an issue and they maybe be perfectly legal. Many codecs that are needed in say mplayer are not included in mplayer version in a main repo, but are compiled in the version on Debian multimedia.e.g. K9copy in Debian main won't rip encoded DVD's. k9copy in Debian  multimedia does.

No need for contrib or non-free of whatever the Ubuntu versions are called. I can watch rip DVD's etc and not compiled a bean on this computer. Debian multimedia does not separate out contrib and non-free so if like me you want a "free system" you need to install vrms to keep an eye on your system.

ok@debian1333:~$ vrms
No non-free or contrib packages installed on debian1333!  rms would be proud.

ok@debian1333:~$ uname -r
2.6.26-libre2-2-powerpc
ok@debian1333:~$

Although it would be possible to add this repo to Ubuntu. And for small programmes you may get away with it (I run undvd from an Ubuntu deb, but know it's a simple python script).As a rule DON'T mix Debian and Ubuntu It will break your system eventually. Run one or the other.

---

### Post by casbahdk on 2009-10-21
Thanks for the advice. The Medibuntu repo seems to work without any problem. It goes over to a "ports" source automatically for PPC. I downloaded libdvdcss2 and so far no problems :)

---

