---
title: "cyrillic in nautilus"
date: 2005-05-29
forum: Absolute Beginner Talk
---

### Post by pravit on 2005-05-29
I have followed all the instructions in the Russian localization HOWTO and I am able to type in Russian and read it correctly in most programs such as GAIM, Firefox, email and so on. However in the Nautilus file viewer, I get only ??? marks. I've seen some packages for Russian language support, but the thing is, I don't want to translate my entire OS to Russian, I just want to be able to display filenames written in Russian correctly. In my /etc/fstab I have my FAT32 partition(where my files with Russian titles are) set up as such:
/dev/hda4	/mnt/share/	vfat	noauto,users,exec,nls=utf8,umask=000	0	0

I have also downloaded the Russian font pack for X servers.

Thanks for any help.

---

### Post by jobezone on 2005-05-29
[QUOTE=pravit]I have followed all the instructions in the Russian localization HOWTO and I am able to type in Russian and read it correctly in most programs such as GAIM, Firefox, email and so on. However in the Nautilus file viewer, I get only ??? marks. I've seen some packages for Russian language support, but the thing is, I don't want to translate my entire OS to Russian, I just want to be able to display filenames written in Russian correctly. In my /etc/fstab I have my FAT32 partition(where my files with Russian titles are) set up as such:
/dev/hda4	/mnt/share/	vfat	noauto,users,exec,nls=utf8,umask=000	0	0

I have also downloaded the Russian font pack for X servers.

Thanks for any help.[/QUOTE]
 Perhaps the Nautilus font you're using doesn't have the caracters you need?
The package "language-support-ru" doesn't translate your desktop. Here is its description:
> 
metapackage for Russian language support
This metapackage depends on all packages that provide native language
support for the various applications in Ubuntu (like various spell
checkers, dictionaries, OpenOffice and Mozilla locale packages,
etc.).

If you also want your applications and the desktop to be translated,
please additionally install language-pack-ru.

Language: Russian


---

### Post by pravit on 2005-05-29
Well, OK, I went and installed language-support-ru, but everything's still displayed as "???". Where can I change the Nautilus fonts?

---

### Post by jobezone on 2005-05-30
System->Preferences->Font

One of these font configuration is used by Nautilus.

---

