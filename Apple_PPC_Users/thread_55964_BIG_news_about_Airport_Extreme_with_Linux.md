---
title: "BIG news about Airport Extreme with Linux"
date: 2005-08-10
forum: Apple PPC Users
---

### Post by Janfi on 2005-08-10
Hi,

Airport Extreme is not supported under Linux at this time, and it's a BIG problem for many users. Hard work is in progress in reverse engineering in hope to have a driver ([http://linux-bcom4301.sourceforge.net/go/progress)](http://linux-bcom4301.sourceforge.net/go/progress)). But not solution at this time.

But...look at this :
[http://forums.gentoo.org/viewtopic-t-365647.html](http://forums.gentoo.org/viewtopic-t-365647.html)

Airport Extreme seems to work on Gentoo with MacOnLinux !  \\:D/ 
This is a good solution while waiting a real driver for linux.

I'm not very experienced, so I need some help to make it work on Ubuntu Hoary (MOL hangs on my system at this point, with OSX 10.4)  :-| 

If anyone can help me (help us ?) with step by step instructions, or some informations I will be very grateful.
I think that I must downgrade OSX to 10.3 (MOL seems to have some problems with latest OSX). And I don't know (understand ?) how to realize the step 3 of the how-to for airport extreme.

To summarize, I need help :
- to have a functionnal MOL for Airport Extreme (ie : seems to be slightly different from standard installation)
- understanding and applying step 3 of the airport extreme how to on Gentoo (if it is the driver on the OSX partition, how to mount it and access it ?)

Thank you very much.


Yet another important link :
[http://www-user.rhrk.uni-kl.de/~nissler/mol/index.html](http://www-user.rhrk.uni-kl.de/~nissler/mol/index.html) for patches
[http://lists.maconlinux.org/pipermail/mol-general/2005-August/003841.html](http://lists.maconlinux.org/pipermail/mol-general/2005-August/003841.html) an interesting thread to solve the memory problem when launching MOL with OSX Tiger.


PS : Please excuse my english.

---

### Post by mdipi on 2005-08-12
[QUOTE=Janfi]Hi,

Airport Extreme is not supported under Linux at this time, and it's a BIG problem for many users. Hard work is in progress in reverse engineering in hope to have a driver ([http://linux-bcom4301.sourceforge.net/go/progress)](http://linux-bcom4301.sourceforge.net/go/progress)). But not solution at this time.

But...look at this :
[http://forums.gentoo.org/viewtopic-t-365647.html](http://forums.gentoo.org/viewtopic-t-365647.html)

Airport Extreme seems to work on Gentoo with MacOnLinux !  \\:D/ 
This is a good solution while waiting a real driver for linux.

I'm not very experienced, so I need some help to make it work on Ubuntu Hoary (MOL hangs on my system at this point, with OSX 10.4)  :-| 

If anyone can help me (help us ?) with step by step instructions, or some informations I will be very grateful.
I think that I must downgrade OSX to 10.3 (MOL seems to have some problems with latest OSX). And I don't know (understand ?) how to realize the step 3 of the how-to for airport extreme.

To summarize, I need help :
- to have a functionnal MOL for Airport Extreme (ie : seems to be slightly different from standard installation)
- understanding and applying step 3 of the airport extreme how to on Gentoo (if it is the driver on the OSX partition, how to mount it and access it ?)

Thank you very much.


Yet another important link :
[http://www-user.rhrk.uni-kl.de/~nissler/mol/index.html](http://www-user.rhrk.uni-kl.de/~nissler/mol/index.html) for patches
[http://lists.maconlinux.org/pipermail/mol-general/2005-August/003841.html](http://lists.maconlinux.org/pipermail/mol-general/2005-August/003841.html) an interesting thread to solve the memory problem when launching MOL with OSX Tiger.


PS : Please excuse my english.[/QUOTE]
 Janfi, thanks so much for this news, this has been bugging me for the longest time! 

I wish i could help but my limited knowladge wouldnt be of any good use :(. 

Good luck, it'd be an amazing help to so many.

-Mike

---

### Post by Janfi on 2005-08-12
OK...It was very late when I've posted the first message, so many of my problems are solved now.
First, by simplification, I decided to downgrade my MacOS installation. At this time, it's 10.3 on my system. With 10.3 and the standard installation of MacOnLinux from ubuntu package, MOL is functionnal (there is a patch to make it work with 10.4, but I decided to limit the number of problems to solve, my objective is to have Airport Extreme...).

Apply the patch to the Airport Extreme driver (step 3 of the howto) was painless. Download aepatch as indicated, make the patch executable with
```
chmod +x aepatch
``` 
The patch needs to modify the MacOS driver, so it's necessary to mount the MacOSX partition before applying it.
```
sudo mount /dev/hdaX /mnt/osx -t hfsplus
``` 
where X is the number of your MacOS partition, and /mnt/osx an exemple of mounting point that you create.
Don't forget to execute the patch with sudo, you need superuser privileges to acceed the MacOS partition.

After that, I can launch MOL, which is fonctionnal...but no airport Extreme  ](*,) 

I think that the problem is due to the MOL version which is too old and not include latest modifications necessary to make Airport Extreme works (pci_proxy ?).
So I tried to compile the rsync version of MOL, but there is many errors when compiling, and I'm unable to solve it at this point.

Hope it's help.

If anyone can investigate with me to make rsync version of MOL functionnal on ubuntu...please post here.

Thanks.

PS : I'm a newbie with ubuntu (used to use Mandriva on my x86  systems), so which is the version of MOL on Breezy ? It is possible to download only MOL from Breezy and if yes, how to ?

---

### Post by Janfi on 2005-08-12
Some news...

Breezy packages are not helping more...it's always MOL v0.9.70.
I tried to use the rsync version from [http://maconlinux.org/dev.html](http://maconlinux.org/dev.html) as indicated for the pci_proxy patch, but there is a lot of errors on compilation.

I decided to make a try with the developer's snapshot available here [http://maconlinux.org/downloads/mol-snapshot.tgz](http://maconlinux.org/downloads/mol-snapshot.tgz)

Once unpackaged, it is labelized as "0.9.71" version. so I try to patch it with the pci_proxying patch (from [http://www-user.rhrk.uni-kl.de/~nissler/mol/index.html](http://www-user.rhrk.uni-kl.de/~nissler/mol/index.html) )

The patch is applied without problem. \\:D/ 

Then, after launching the compilation process, the menu to customize compilation appears with the possibility to activate the pci_proxying. I select it, and unselect vnc server which causes errors...

But the compilation process stops when "entering Linux". Below, a cut of the console output :
```
    Linking libxkeyremap.a        : ok
+ Entering vconfig
    Compiling main.o              : ok
    Compiling vmodeparser.o       : ok
    Compiling modes-y.o           : ok
    Compiling modes-l.o           : ok
= Building molvconfig             : ok
+ Entering kmod
+ Entering Linux
In file included from /home/janfi/mol-0.9.71/obj-ppc/build/src/kmod/_fault.c:24:
/home/janfi/mol-0.9.71/obj-ppc/build/src/kmod/misc.h:81: error: redefinition of                                             `check_bit_mol'
/home/janfi/mol-0.9.71/obj-ppc/build/src/kmod/misc.h:73: error: `check_bit_mol'                                             previously defined here
make[6]: *** [/home/janfi/mol-0.9.71/obj-ppc/build/src/kmod/_fault.o] Erreur 1
make[5]: *** [_module_/home/janfi/mol-0.9.71/obj-ppc/build/src/kmod] Erreur 2
nm: '../../../obj-ppc/build/src/kmod/Linux//..//mol.ko': No such file
nm: '../../../obj-ppc/build/src/kmod/Linux//..//mol.ko': No such file
checker.pl failed
rm: ne peut enlever `../../../obj-ppc/build/src/kmod/Linux//..//mol.ko': Aucun f                                            ichier ou répertoire de ce type
make[4]: *** [all-local] Erreur 1
make[3]: *** [sub-Linux-all] Erreur 2
make[2]: *** [sub-kmod-all] Erreur 2
make[1]: *** [sub-src-all] Erreur 2
make: *** [auto-bootstrap] Erreur 2
``` 

I'm stucked with it, I don't know howto make it work. So close....  ](*,) 

Any ideas ?

---

### Post by stuporglue on 2005-09-22
Well, you're lucky then. :-) I'm not getting as far as you. 

After the first make failure, here's the whole output from my make:

```
stuporglue@moonie:~/mol-rsync$ make 
+ Entering lxdialog
+ Entering kconfig
    Compiling    mconf.o             
cc1: note: obsolete option -I- used, please use -iquote instead
mconf.c:91: error: static declaration of ‘current_menu’ follows non-static declaration
./lkc.h:63: error: previous declaration of ‘current_menu’ was here
make[2]: *** [../../obj-ppc/build/config/kconfig/mconf.o] Error 1
make[1]: *** [sub-kconfig-all] Error 2
make: *** [do-bootstrap] Error 2
stuporglue@moonie:~/mol-rsync$ 
```

---

### Post by refdoc on 2005-09-26
Same as stuporglue here. i have been hanging out tonight at #mol at freenode, but no one really answered there. On #ubuntu someone suggested to rebuold the source package using the breezy sourcepackag]e as a template, but I have no clue baout this either

---

### Post by refdoc on 2005-09-28
Now - maybe one step further.

Yellow Dog has rpm packages for 0.9.71. 

<i>sudo alien --to-deb [packagename] </i>

will transform them into debs. Install for mol works then fine - but for the modules which appear to be compiled with another kernel than breezy and hoary use. Compiling the modules source failed...

---

### Post by stuporglue on 2005-09-29
Can you post a link to the debs? I'll give a shot at compiling the modules once I get those. 

Thanks, 

Stuporglue

---

### Post by refdoc on 2005-10-02
[QUOTE=stuporglue]Can you post a link to the debs? I'll give a shot at compiling the modules once I get those. 
Thanks, 
Stuporglue[/QUOTE]

Sorry, I had been away for a few days.

The debs I made by using alien on YDL rpms

I found the rpms, I think on YDL's website, but rpm finder throws them up too:

[http://rpmfind.net/linux/RPM/yellowdog/releases/yellowdog-4.0/en/os/YellowDog/RPMS/mol-kmods-0.9.71-0.ydl.1.ppc.html]("http://rpmfind.net/linux/RPM/yellowdog/releases/yellowdog-4.0/en/os/YellowDog/RPMS/mol-kmods-0.9.71-0.ydl.1.ppc.html")

---

### Post by refdoc on 2005-10-06
Maybe a different compiler version required?

---

### Post by refdoc on 2005-10-07
OK I tried to compile again the rsynced version - it requires gcc 3.4 to compile, gcc4.0 does not do the job for one reason or another. It compiles fine up to a point - the kernel is compiled in 4.0 and here it clashes...

I am not sure what to do now...

---

### Post by fromtheflames on 2005-10-15
[Check this out](http://ubuntuforums.org/showpost.php?p=412981&postcount=2)

---

### Post by calcioguy9 on 2005-10-18
Does anyone know how close the driver is to being finished (or functional anyway)?

---

### Post by refdoc on 2005-10-29
Notice on page: **_This driver does not work, yet! If you are not a kernel hacker, go away and come back later, when this notice is removed, please._**

So if in the meantime someone get that Mol thingy to work...

---

### Post by Evil_Genius_From_Hell on 2005-11-17
Hey dudes! Yeahh, I did it!

Just:

apt-get install bison
apt-get install byacc
apt-get install libpng3-dev

** I'm not sure if this helped, but I did it as saw on the ./configure it checks for it **

and then use gcc-3.4

rm /usr/bin/gcc

ln -s /usr/bin/gcc-3.4

cd mol-rsync
make 

;-)

Hope it helped you!

---

### Post by Evil_Genius_From_Hell on 2005-11-17
To avoid the error compiling Linux (see upper) you have to apply the patch first:

[http://www-user.rhrk.uni-kl.de/~nissler/mol/mol_rsync_compile_fix.diff](http://www-user.rhrk.uni-kl.de/~nissler/mol/mol_rsync_compile_fix.diff)

Good Luck!

---

