---
title: "Save for Web GIMP plugin Linux installation"
date: 2011-11-02
forum: Art &amp; Design
---

### Post by Bucic on 2011-11-02
[http://registry.gimp.org/node/33](http://registry.gimp.org/node/33)

I was trying to follow the following instructions
> 
1. Unzip the .tar.gz in ~/.gimp-2.6/plug-ins/ 
2. $ sudo apt-get install libgimp2.0-dev (if not installed packs for compile) 
3. $ cd ~/.gimp-2.7/plug-ins/gimp-save-for-web-0.29.3/ 
4. $ ./configure make 
5. $ sudo make install 
6. Restart Gimp 
7. A new option is created at File>Save for web 
-- Sergio Laprea sergio [at] klosma.net

The first time I got **Intltool not found** so I've installed it like this [http://www.linuxfromscratch.org/blfs/view/cvs/general/intltool.html](http://www.linuxfromscratch.org/blfs/view/cvs/general/intltool.html)
The second time I tried to issue the ./configure make command I got 
```

.
.
.
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  ca es fr ja it ko pt_BR ru sk sv
checking for bind_textdomain_codeset... (cached) yes
checking if GTK+ is version 2.7.0 or newer... yes
checking if GIMP is version 2.3.0 or newer... yes
checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/bash ./config.sub make failed

```

EDIT:
The proper procedure is:
> 1. Unzip the .tar.gz in ~/.gimp-2.6/plug-ins/ 
2. $ sudo apt-get install libgimp2.0-dev (if not installed packs for compile) 
3. $ cd ~/.gimp-2.7/plug-ins/gimp-save-for-web-0.29.3/ 
4. $ ./configure
5 $ make 
6. $ sudo make install 
7. Restart Gimp 
8. A new option is created at File>Save for web 
-- Sergio Laprea sergio [at] klosma.net
If you get an error **Intltool not found** or similar, install it as per [http://www.linuxfromscratch.org/blfs/view/cvs/general/intltool.html](http://www.linuxfromscratch.org/blfs/view/cvs/general/intltool.html)

---

### Post by hailtothethief on 2011-11-02
try

```
./configure
make
```

as two separate commands ;)

---

### Post by robert shearer on 2011-11-02
Why are you trying to build it when it is available through the Ubuntu repos...?

```
sudo apt-get install gimp-plugin-registry
```

This has, amongst several other nifty plugins, the 'save for web' plugin.

Just install, restart Gimp and find it in the drop-downs from the 'File' menu.

---

### Post by prokoudine on 2011-11-02
> **Bucic said:**
> 
The second time I tried to issue the ./configure make command I 

If you really, REALLY want to install anything from source code, use 'sudo apt-get build-dep PACKAGE' command. In this case it would be 'sudo apt-get build-dep gimp'. But as already pointed out by Robert Shearer, the plug-in is in PPA.

---

### Post by Bucic on 2011-11-03
> **hailtothethief said:**
> try

```
./configure
make
```

as two separate commands ;)
It worked! Thanks! :D
The procedure in the original post revised.

---

### Post by Bucic on 2011-11-03
> **robert shearer said:**
> Why are you trying to build it when it is available through the Ubuntu repos...?

```
sudo apt-get install gimp-plugin-registry
```

This has, amongst several other nifty plugins, the 'save for web' plugin.

Just install, restart Gimp and find it in the drop-downs from the 'File' menu.
The plugin registry from the software center wouldn't install as I use GIMP 2.7 beta.


> **prokoudine said:**
> If you really, REALLY want to install anything from source code, use 'sudo apt-get build-dep PACKAGE' command. In this case it would be '**sudo apt-get build-dep gim**'. 
Would that single command replace the whole procedure of building from source?

---

### Post by SeijiSensei on 2011-11-03
> **Bucic said:**
> Would that single command replace the whole procedure of building from source?

No, the build-dep option downloads and installs any needed libraries or header files on which the compilation depends.  After running 'sudo apt-get build-dep packagename' you still need to run ./configure and make, but you shouldn't see errors for missing dependencies.

---

### Post by Bucic on 2011-11-04
> **SeijiSensei said:**
> No, the build-dep option downloads and installs any needed libraries or header files on which the compilation depends.  After running 'sudo apt-get build-dep packagename' you still need to run ./configure and make, but you shouldn't see errors for missing dependencies.
Extremely useful, thanks! Sorry for not digging deeper into building from source but I thought I was getting some kind of package-specific error.

BTW, too bad no one will port the far superrior RIOT plugin [http://luci.criosweb.ro/riot/](http://luci.criosweb.ro/riot/)

---

### Post by Bucic on 2012-04-15
Have anyone managed to install Save for Web plugin for GIMP 2.8 RC1 (or later) on Ubuntu 11.10 or, preferably, 12.04?

---

### Post by briggsosaurus on 2012-04-21
> **robert shearer said:**
> Why are you trying to build it when it is available through the Ubuntu repos...?

```
sudo apt-get install gimp-plugin-registry
```

This has, amongst several other nifty plugins, the 'save for web' plugin.

Just install, restart Gimp and find it in the drop-downs from the 'File' menu.

WORKED PERFECTLY thank you robert shearer just typed that one command in and restarted gimp and it worked! thank you

---

### Post by robert shearer on 2012-04-24
> **briggsosaurus said:**
> WORKED PERFECTLY thank you robert shearer just typed that one command in and restarted gimp and it worked! thank you

Good work following the command. Now take a look at all the other super-uber-goober effects that you got with that plugin.....
Like FXFoundry>Photo>Effects
Explore and have fun   :-)

---

