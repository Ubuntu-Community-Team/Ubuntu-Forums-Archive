---
title: "installing a program"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by eng. on 2006-12-24
hi,
i have a program that i don't know how to install (it doesn't have any readme files),does anyone know how to install it? here is its directory structure:
bin
[INDENT]acroread
athena
atlas
clever
dbinternal
deckbuild
devedit
devedit3d
dngsetup
fastatlas
fastdevedit
fatlastool
getlicense
ghostprint
gunzip
gzip
maskviews
mcdb
memtest
mocasim
quest
rpc.sflmserverd
Save
sflm
sflm_monitord
showid
sman
smartspice
smartview
spicegui
spiceserver
ssuprem3
sysname
tonyplot
tonyplot3d
[/INDENT]
etc
[INDENT].04X4B876KPF
.057YFT1HR79
dbwork.ddl
deveditrc
gnu_license
manifest.999
s_admin
s_cleanup
s_getenv
s_install
s_install_oldkey
s_platform_specifics
s_process_opts
s_setup
s_setup_fonts
s_show_version
s_unpack
s_xvset_locale
SflmProductDisplayNames
SflmProductList
silvaco.cshrc
silvaco.profile
spdb_load
spdb_save
spdbadmin
[/INDENT]

lib
[INDENT]
acroread
athena
[INDENT]5.4.11.R[INDENT]common(Dir)
athena
athena.lib
athenakey
athenamod
athenamod.95
athenamod.96
athenamod.97
athenamod.prototype
athenares
cnetmod
userimp

i386-linux(Dir)
athena.exe
athenaukey
CompilationPlatform
keyread.exe


[/INDENT][/INDENT]
	
gzip
rpc.sflmserverd
s_install
[INDENT]
1.1.4.R
[INDENT]common(Dir)
config
install_defines
install_generic_procs
install_procs
install_tool
master04.dbd
spdb_data.dbd

i386-linux(Dir)
not_empty[/INDENT]
[/INDENT][/INDENT]


regards

---

### Post by Sef on 2006-12-24
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by eng. on 2006-12-24
i tried this steps under ( s_install-> 1.1.4.R -> common ) as there was a file named "config" and another one named "install_tool" but all of them failed

 ./configure ------------  bash: ./configure: No such file or directory
./config       ------------  ./config: System name not defined.
./config --help ----------  ./config: System name not defined.
install_tool   ------------  bash: install_tool: command not found
make config ------------  make: Nothing to be done for `config'.
make         --------------  make: *** No targets specified and no makefile found.  Stop.

when i renamed config to configure

./configure   ------------     ./configure: System name not defined.

---

### Post by taurus on 2006-12-24
That's not a program; that's a collections of binaries (bin), their libaries (lib), and config files (etc)...  Are those programs in bin even for Ubuntu???

---

### Post by eng. on 2006-12-24
i tried to compile them using

./configure
make
make install

but i receive the above errors

---

### Post by taurus on 2006-12-24
There is NO configure for you to ./configure so just forget about that.  You're supposed to unpack them from / so that the binaries will go into /bin, the config files will do into /etc, and the libaries will go into /lib.  However, before you do that, probably breaking your system in the meantime, where did you get that collections of files because some (if not most) of them are already on your machine???

---

### Post by eng. on 2006-12-24
this is a program that i have downloaded and the files are already divided in each directory in order , what about the error "./config: System name not defined." how to solve it? note that  i am using the live cd version of ubuntu.

---

### Post by taurus on 2006-12-24
What is it and where did you download it?  Again, there is no config file so if you want to install it (don't blame it on me later if it breaks your machine), save it to / and unpack it from there...

---

### Post by eng. on 2006-12-24
it is an electronics software, so how could i install it? and how to unpack it? i am new to linux 

regards

---

### Post by taurus on 2006-12-24
When you download it, it comes with a one big file, right!  What is the name of that file?

p.s.  When you said cracked, you mean illegal version???

---

### Post by eng. on 2006-12-24
its name was s11.tar

---

### Post by Frak on 2006-12-24
You are aware *cracked* software is *illegal*?!?!?

---

### Post by taurus on 2006-12-24
> **eng. said:**
> its name was s11.tar

Okay, you keep changing/modifying your posts because you don't want others to know the exact name and nature of it!!!  Therefore, it _has_ to be something illegal then...  If you can't prove otherwise, I will lock this thread since there is no illegal activity around here!!!  [-(

---

