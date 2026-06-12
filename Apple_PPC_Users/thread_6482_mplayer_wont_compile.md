---
title: "mplayer wont compile"
date: 2004-11-29
forum: Apple PPC Users
---

### Post by eggie on 2004-11-29
followed the ubuntu multimedia tutorial and downloaded everything got make and started to get incompatible pointer typ error. Wont make  any ideas?

---

### Post by joemafia on 2004-11-29
same here  ](*,)

---

### Post by adbak on 2004-11-29
I don't know what you have to do if you really want to compile...but I do know how you can get mplayer installed on your computer.

Simply add ```
deb ftp://ftp.nerim.net/debian-marillat/ testing main
``` to your ```
/etc/apt/sources.list
``` using whatever editor you want.  You may have seen this source before, but you probably saw it with *stable* instead of *testing*.  Refresh your sources and install mplayer.

Serve with mpegs and enjoy.  :)

---

### Post by adamward on 2004-11-29
[QUOTE=adbak]I don't know what you have to do if you really want to compile...but I do know how you can get mplayer installed on your computer.

Simply add ```
deb ftp://ftp.nerim.net/debian-marillat/ testing main
``` to your ```
/etc/apt/sources.list
``` using whatever editor you want.  You may have seen this source before, but you probably saw it with *stable* instead of *testing*.  Refresh your sources and install mplayer.

Serve with mpegs and enjoy.  :)[/QUOTE]
 I have added the above code to my sources.list file, and I get the following error:
Get:1 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
  Unable to fetch file, server said '/debian-marillat/dists/testing/main/binary-powerpc/Packages.gz: No such file or directory  '

as well as:

Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-powerpc/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-powerpc/Packages.gz)  Unable to fetch file, server said '/debian-marillat/dists/testing/main/binary-powerpc/Packages.gz: No such file or directory  '
Reading Package Lists... Done
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


I'm not sure what is the problem, but browsing the web to this site shows i86 files, but no PPC files.  Am I missing something?

--adam

---

### Post by SyL on 2004-12-01
It's because : [ftp://ftp.nerim.net/debian-marillat]("ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-powerpc/Packages.gz") is not a mirror for ppc
 
 Try this :
 deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/
 
 marillat blog : [http://gda.utp.edu.co/pub/debian/](http://gda.utp.edu.co/pub/debian/)
 
 :)

---

### Post by adamward on 2004-12-01
[QUOTE=SyL]It's because : [ftp://ftp.nerim.net/debian-marillat]("ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-powerpc/Packages.gz") is not a mirror for ppc
 
 Try this :
 deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/
 
 marillat blog : [http://gda.utp.edu.co/pub/debian/](http://gda.utp.edu.co/pub/debian/)
 
 :)[/QUOTE]

That would make sense!  Thanks for the update, I'll add that to my sources.list file tonight when I get home!

--adam

---

