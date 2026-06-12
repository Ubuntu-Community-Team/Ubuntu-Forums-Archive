---
title: "Errors when installing Fuse"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-04-18
I'm trying to install Fuse so that I can install  Siefs to access my Siemens mobile phone, but I'm getting these error messages when I run "make install":

make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/fuse" || mkdir -p -- "/usr/local/include/fuse"
mkdir: cannot create directory `/usr/local/include/fuse': Permission denied
make[2]: *** [install-fuseincludeHEADERS] Error 1
make[2]: Leaving directory `/home/dianne/fuse/include'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/dianne/fuse/include'
make: *** [install-recursive] Error 1

Do I need to use Sudo to get the permissions for mkdir?

TIA

---

### Post by joft on 2007-04-19
Why do you want to install fuse "by hand"? I assume you use dapper, at least your profile says that. Dapper has fuse packages: libfuse2, fuse-utils for normal "use" and libfuse-dev, if you want to compile a fuse based filesystem application such as siefs. Use e.g. synaptic or aptitude to install theses packages. Then build siefs (siefs isn't in the repositories, so this one you have to build on your own).

Regarding your question: Yes, you need sudo. /usr/local is a directory which has now write permission for normal users. In general, you have to call "make install" as "sudo make install".

---

