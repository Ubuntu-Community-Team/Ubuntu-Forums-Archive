---
title: "[SOLVED] Trying to install egoboo"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Silvain on 2007-12-13
Trying to install Linux version of game from here. [http://home.no.net/egoboo]("http://home.no.net/egoboo")
Well so far have the tar unzipped in /tmp and here is my paste from cl window.
tnt:/tmp/ego244b_linux$ ls
basicdat                 egoboo.exe             modules      SDL_mixer.dll
Changelog.txt            libSDL-1.2.so.0        msvcr71.dll  SDL_ttf.dll
controls.txt             libSDL_mixer-1.2.so.0  players      setup.txt
egoboo                   libSDL_ttf-2.0.so.0    Readme.txt   Uninstall.exe
Egoboo 2.4.4 Manual.pdf  License.pdf            SDL.dll      Uninstall.ini


Next trying to execute what I am guessing is install file, Maybe this is incorrect file ?

paste from resulting..
tnt:/tmp/ego244b_linux$ ./egoboo
./egoboo: error while loading shared libraries: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory

The earlier paste shows the file exist at least.  :grin: Can someone give me the benefit of their experience please ?

---

### Post by FuturePilot on 2007-12-14
It looks like you downloaded the one for Windows. The Linux one is here
[http://sourceforge.net/project/downloading.php?groupname=egoboo&filename=ego244b_linux.tar.gz&use_mirror=easynews]("http://sourceforge.net/project/downloading.php?groupname=egoboo&filename=ego244b_linux.tar.gz&use_mirror=easynews")

---

### Post by Silvain on 2007-12-14
Thanks for the link. Downloaded it, then on untar , I got this response...

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

Does this mean the file is bad ? Hmm what next ?:confused:

---

### Post by arochester on 2007-12-14
Egoboo is available from repositories.

---

### Post by Silvain on 2007-12-14
Went to System>Administration>Synaptic Package Manager. Then entered admin pass, then hit search button. Entered "egoboo", found a package ! Downloading it right now. 
This makes this solved I hope . :)

---

### Post by Jarramundi on 2008-04-18
Ok.. I have DLL'd egoboo from the repositories and I have discovered (from the egoboo forum) that it is an old buggy version 2.22 (all my characters etc are invisible). so I DLL v 2.7.4 linux port from the source, only when I unzip it, it appears to be a windows app. what's going on? All i want is some decent RPG action (other than bloody nethack) but it seems the universe is conspiring against me. Can someon please help me out? :confused:

---

