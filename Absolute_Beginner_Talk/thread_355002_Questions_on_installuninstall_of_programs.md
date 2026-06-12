---
title: "Questions on install/uninstall of programs"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-02-06
Hi,

I don't quite understand how stuff is installed/uninstalled in Linux. It seems that programs get installed in various directories and I don't understand how this compares to "Program Files" in Windows. I'm trying to understand this and find a coherent way to manage things so here are a couple of questions:

- where do deb files get installed?
- when I compile a program from source using make where is it installed?
- when I install a package from synaptics, is it always a deb???
- when I download deb files from Internet, should I store them in a specific folder? I understand I can install deb from anywhere but is there just a coherent and clean way to do things on Linux?
- when I want ot compile a program from source (tar), should I store the tar file in a specific folder before running make??
- do I need to keep a deb file if I want to uninstall a program??? This is especially important for downloaded packages from Synaptics because their deb files are cached in var/apt/archives. I usually exclude this folder from my backups some when restoring the cache is empty. Does this mean I won't be able to uninstall packages that were installed with Synaptics???

Thanks

---

### Post by bodhi.zazen on 2007-02-06
> **kilou said:**
> Hi,

I don't quite understand how stuff is installed/uninstalled in Linux. It seems that programs get installed in various directories and I don't understand how this compares to "Program Files" in Windows. I'm trying to understand this and find a coherent way to manage things so here are a couple of questions:

Linux file system:

[http://ubuntuforums.org/showthread.php?&t=258611](http://ubuntuforums.org/showthread.php?&t=258611)

[http://doc.gwos.org/index.php/FileLocations](http://doc.gwos.org/index.php/FileLocations)


> - where do deb files get installed?

See above

> - when I compile a program from source using make where is it installed?

See above.

To find and installed package use:

```
whereis <program name>
``` or other location tools.

> - when I install a package from synaptics, is it always a deb???

Yes

> - when I download deb files from Internet, should I store them in a specific folder? I understand I can install deb from anywhere but is there just a coherent and clean way to do things on Linux?

See here: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Always install from the repositories to keep it easy. Install from source to learn.

> - when I want ot compile a program from source (tar), should I store the tar file in a specific folder before running make??

I make a file in ~ (~ = short hand for /home/user_name) called src.

Download the source code and extract to ~/src/<package_name>

Keep it for future reference.

use checkinstall if at all possible.

> - do I need to keep a deb file if I want to uninstall a program??? This is especially important for downloaded packages from Synaptics because their deb files are cached in var/apt/archives. I usually exclude this folder from my backups some when restoring the cache is empty. Does this mean I won't be able to uninstall packages that were installed with Synaptics???

Thanks

Depends on where you got the .deb from ... If from synaptic, no worries. Otherwise I would keep it in ~/src/<package_name>

HTH

---

### Post by ^rooker on 2007-02-06
That one's difficult to explain shortly.... Linux' folder/file structure is very different to the one used by Windows:

configuration, documentation, libraries and executables are kept separated - so a single application is literally scattered all across your system's folders.

There are plenty of resources where you can get deeper info about the *nix folder structure, and [here's one of them]("http://www.tuxfiles.org/linuxhelp/linuxdir.html").


The installation/removal of .deb packages themselves is handled by [Debian package management system]("http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html") - together with [its friend APT]("http://www.debian.org/doc/manuals/apt-howto/"). The information about which file goes where is stored within the package (That's what the package is mainly for).


In practice, you install programs from so called "repositories" - Large collections of .deb files for certain distros (you can configure those repository sources in /etc/apt/sources.list). If you want something you do:

# apt-cache search someapp

...and if you've found something matching "someapp", you can install it by issuing:

# apt-get install someapps-package-name

That's basically it. 
For a nicer overview (and for ones preferring GUIs), there's "Synaptic Package Manager" in System/Administration.



When you compile stuff from source, the destination directories are usually configured when you run "./configure" (some autoconfigure script which generates the final Makefile).
This "configure"-script is usually part of the source package you've downloaded.

In most cases the default paths will be fine, but you could choose a different directory for installation by e.g. running "./configure --prefix=/mnt/apps/myappfromsrc".

After unpacking some source tarball, change to the source's folder and run "./configure --help" in order to see all available options.

"make install" will usually take care of moving the compiled files to their so configured destinations. Unfortunately, you cannot remove appliations installed like that using the packaging system, because the package management system does not know about those "manually" installed files.

You should consider using "checkinstall" for this. It will create a package based on actions performed when running "make install" - You will end up with a .deb file and your system being aware of what you've just installed.
(You can get "[checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/")" by running "apt-get install checkinstall")


When you download source-tarballs, it doesn't really matter where you extract and compile them, since you can delete the source directory afterwards anyway.

---

### Post by bodhi.zazen on 2007-02-06
> **^rooker said:**
> When you download source-tarballs, it doesn't really matter where you extract and compile them, since you can delete the source directory afterwards anyway.

First nice post :p

I would not delete them (source-tarballs) but rather save them in the event you need to uninstall or update ...

As above, I save them in ~/src

Well that is my opinion at least ...

---

### Post by capdog on 2007-02-07
Hi everyone. I happened to have the exact same questions as above! :)

I understand how the unix filesystem works, but my question is still _why_ it is like that... I still don't get why it's easier to scatter a program than keep all it's files together (I know... I'm a wannabe philosopher)

The other question is how do I immediately discover what has happened after installing a .deb file. I would like to look at an apt-log or something similar that will tell me what files were added to my system, and what manual entries, etc.

Thanks for the speedy responses this forum rocks!

---

### Post by Maestro23 on 2007-02-07
> **capdog said:**
> Hi everyone. I happened to have the exact same questions as above! :)

I understand how the unix filesystem works, but my question is still _why_ it is like that... I still don't get why it's easier to scatter a program than keep all it's files together (I know... I'm a wannabe philosopher)

The other question is how do I immediately discover what has happened after installing a .deb file. I would like to look at an apt-log or something similar that will tell me what files were added to my system, and what manual entries, etc.

Thanks for the speedy responses this forum rocks!

Log files in [COLOR="Red"]/var/log[/COLOR]

Ex: File called aptitude there.  Tells me what I have installed with the "aptitude" command by date. Lists dependencies as well.

---

### Post by rai4shu2 on 2007-02-07
Linux programs generally conform to the FSSTND standard.

[http://www.openaddict.com/documents/Linux-Filesystem-Hierarchy/](http://www.openaddict.com/documents/Linux-Filesystem-Hierarchy/)

This provides better interoperability than the Mac or Windows way of storing files.

---

### Post by bodhi.zazen on 2007-02-07
> **capdog said:**
> I understand how the unix filesystem works, but my question is still _why_ it is like that... I still don't get why it's easier to scatter a program than keep all it's files together (I know... I'm a wannabe philosopher)

Well, it is both more complex and simple at the same time.

The program itself is not scattered, there is a lot of additional (potential) information included then a binary.

For example man pages. Rather then having man pages scattered throughout some directory "program Files" each with a sub directory <program_name>, the man pages are consolidated.

The file system is quite logical an efficient, IMO at least ...

---

### Post by RomeReactor on 2007-02-07
Hi. I may come off as ignorant and this is just my opinion, but i don't think the way linux installs files is much different than windows, just more clear and efficient. Let me explain: When you install a program in windows, what you get in the Program Files directory are executables and sometimes, brief documentation. But when it comes to the actual amount of files the system installs (including the dreaded [DLL's]("http://en.wikipedia.org/wiki/Dynamic-link_library")) you'd be hard-pressed to find it's totality, especially since applications in windows tend to be much more obscure regarding their installation procedure and location than other OS's. In linux, there's a logical organization to files installed that's more easily accessible to the user (or less difficult, depending on your point of view). Plus, if you install packages from your distro's package manager, listing the total amount of files installed by a program and their location is just a couple of clicks away. Just my 2 cents...

---

### Post by mcduck on 2007-02-07
> **capdog said:**
> 
I understand how the unix filesystem works, but my question is still _why_ it is like that... I still don't get why it's easier to scatter a program than keep all it's files together (I know... I'm a wannabe philosopher)
This way you'll always find files of the same type from one place. Now, whenever I need to find the executable file for a program I don't need to look around my file system, as executables for all apps I install are in /usr/share/bin. If I need to find programs icon, I'll almost always find it from /usr/share/pixmaps or /usr/share/icons.. Do you need apps documentation? /usr/share/doc contains docs for all your apps. System settings? /etc has them all..

---

### Post by capdog on 2007-02-07
> **RomeReactor said:**
> Plus, if you install packages from your distro's package manager, listing the total amount of files installed by a program and their location is just a couple of clicks away. Just my 2 cents...

Thanks, that little tidbit has given me the clue I needed ... in synaptic, right click a package and choose properties. There is a list of installed files! Just what I wanted! Thanks everyone.:guitar:

---

### Post by kilou on 2007-02-07
Thanks for the comprehensive replies, especially to bodhi.zazen! I'll have a look at all this :)

---

### Post by kilou on 2007-02-08
OK I checked some of the litterature but there is still something I couldn't understand. For instance I downloaded a game in a tarball. This archive is not a source code, it's just the game in a compressed archive so that all I have to do is to untar the archive and launch the game for it to work. Of course I can launch the game from anywhere but is there a "right linux way" to run this game? Should I untar the archive in /opt, in my home directory or somewhere else to do it properly? I'd like to learn what is the correct way to do things in linux so that I can install other programs correctly in the future.

---

### Post by shareMenaPeace on 2007-02-08
Thansk for the infos, 
i like to add i think it is basicly really fundamental how you organize your /home/user/ folder and other devices.

So my /home/user/ folder looks like this

BACKUPS/system/      
BACKUPS/profiles
BACKUPS/themes

GRAFIC/Wallpaper
GRAFIC/GTK

TEMP
INCOMING 
VIDEO/music_videos
VIDEO/Tutorials



Well you get the idea so to me i liek it when the /home/user folder is clean.
Additional i partitioned another ext3 device where i save all my MP3 and such.

CHeers

---

### Post by bodhi.zazen on 2007-02-09
> **kilou said:**
> OK I checked some of the litterature but there is still something I couldn't understand. For instance I downloaded a game in a tarball. This archive is not a source code, it's just the game in a compressed archive so that all I have to do is to untar the archive and launch the game for it to work. Of course I can launch the game from anywhere but is there a "right linux way" to run this game? Should I untar the archive in /opt, in my home directory or somewhere else to do it properly? I'd like to learn what is the correct way to do things in linux so that I can install other programs correctly in the future.

The best way is what ever works.

IMO the best place is in your home directory

/home/user_name/bin/program_name

Other options include :

/local/bin/program_name

/opt and /usr are also optins

Best be consistent

---

### Post by mcduck on 2007-02-09
> **kilou said:**
> OK I checked some of the litterature but there is still something I couldn't understand. For instance I downloaded a game in a tarball. This archive is not a source code, it's just the game in a compressed archive so that all I have to do is to untar the archive and launch the game for it to work. Of course I can launch the game from anywhere but is there a "right linux way" to run this game? Should I untar the archive in /opt, in my home directory or somewhere else to do it properly? I'd like to learn what is the correct way to do things in linux so that I can install other programs correctly in the future.
I think the most correct place for extra software coming from 'unofficial' sources would be in /home if you want it for only one user, or in /opt for all users.

Of course /usr could also be OK place if you want to install for all users.

---

