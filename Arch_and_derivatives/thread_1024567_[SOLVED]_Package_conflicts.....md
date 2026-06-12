---
title: "[SOLVED] Package conflicts...."
date: 2008-12-29
forum: Arch and derivatives
---

### Post by gjoellee on 2008-12-29
Hi, I am trying to install KDEmod but i get some package conflicts:
```
(327/327) checking for file conflicts               [---------------------] 100%
error: could not prepare transaction
error: failed to commit transaction (conflicting files)
/usr/share/apps/cmake/modules/CTestTestfile.cmake exists in both 'kdemod-kdebase-runtime' and 'kdemod-kdebase-workspace'
/usr/share/apps/cmake/modules/cmake_install.cmake exists in both 'kdemod-kdebase-runtime' and 'kdemod-kdebase-workspace'
/usr/share/apps/kdevappwizard/templates/qmake_qt4guiapp.tar.bz2 exists in both 'kdemod-kdesdk-kapptemplate' and 'kdemod-kdevelop'
Errors occurred, no packages were upgraded.

```

does anyone know how to solve this?

---

### Post by mips on 2008-12-29
The last time that happened to me with kdemod I just forced (-f) it with no ill effects.

---

### Post by gjoellee on 2008-12-29
> **mips said:**
> The last time that happened to me with kdemod I just forced (-f) it with no ill effects.

thanks!
(NOTE: I have had a thread a long time in the Arch Linux forums, bt no answer...here I get an answer in a matter of minutes!)

---

### Post by handy on 2008-12-29
> **gjoellee said:**
> thanks!
(NOTE: I have had a thread a long time in the Arch Linux forums, bt no answer...here I get an answer in a matter of minutes!)

That is just due to the huge user population difference between the two forums.

---

### Post by mips on 2008-12-29
> **gjoellee said:**
> thanks!
(NOTE: I have had a thread a long time in the Arch Linux forums, bt no answer...here I get an answer in a matter of minutes!)

Well lets just say I'm paying it forward. I asked the very same question in the kdemod forums and funkyou told me to force it. So the answer has always been there ;) Enjoy!

Now if only someone would fix yaourt so it works with AUR again then I can continue with my fresh arch install on my desktop, need nvidia-beta...

---

### Post by Amranu on 2008-12-29
You can still install using yaourt, just can't search. You can also download the tarball of the file from [http://aur.archlinux.org](http://aur.archlinux.org) and then cd into the directory after extracting it, type: makepkg PKGBUILD, and then pacman -U <resulting package> to install

---

### Post by mips on 2008-12-29
> **Amranu said:**
> You can still install using yaourt, just can't search. You can also download the tarball of the file from [http://aur.archlinux.org](http://aur.archlinux.org) and then cd into the directory after extracting it, type: makepkg PKGBUILD, and then pacman -U <resulting package> to install

I downloaded a patched version of yaourt (on yaourt AUR page) which allows you to search but I'm getting conflicts with libgl when I try and install nvidia-beta & nvidia-utils-beta. I thought it was due to yaourt.

---

### Post by doorknob60 on 2008-12-30
> **mips said:**
> I downloaded a patched version of yaourt (on yaourt AUR page) which allows you to search but I'm getting conflicts with libgl when I try and install nvidia-beta & nvidia-utils-beta. I thought it was due to yaourt.

Force it. Use -f and -d. nvidia-usitl-beta provides libgl so after it's installed there shouldn't be any problems. THat's what I did and ti works fine.

---

### Post by mips on 2008-12-31
> **doorknob60 said:**
> Force it. Use -f and -d. nvidia-usitl-beta provides libgl so after it's installed there shouldn't be any problems. THat's what I did and ti works fine.

Tried that but no go. From the comments on the AUR page it looks like the package does not build with the new kernel. Will wait till it sorts itself out.

---

