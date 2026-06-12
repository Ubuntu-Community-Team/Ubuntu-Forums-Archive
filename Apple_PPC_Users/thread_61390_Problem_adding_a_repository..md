---
title: "Problem adding a repository."
date: 2005-08-31
forum: Apple PPC Users
---

### Post by RIVE on 2005-08-31
I have a problem adding this repository to my sources.list

deb [http://honk.physik.uni-konstanz.de/...nux-ppc/debian/](http://honk.physik.uni-konstanz.de/...nux-ppc/debian/) mplayer/

after saving sources.list with that repository I get this fail massage:

W: Can't get the list of packages [http://honk.physik.uni-konstanz.de](http://honk.physik.uni-konstanz.de) mplayer/ Packages /var/lib/apt/lists/honk.physik.uni-konstanz.de_...nux-ppc_debian_mplayer_Packages) - stat (2 File or directory doesn't exist)

I need that repository to install transcode and dvdrip

I read about that repository in [http://ubuntuforums.org/showthread.php?t=58765&highlight=libdvdcss2+ppc](http://ubuntuforums.org/showthread.php?t=58765&highlight=libdvdcss2+ppc)

I already install libdvdcss2 :) all i need is trancode and dvdrip

Thanks in advance.

---

### Post by izmaelis on 2005-08-31
[QUOTE=RIVE]
I need that repository to install transcode and dvdrip
[/QUOTE]
You can find a tip on how to install **dvd::rip** [here](http://ubuntuguide.org/#dvdrip) in the Unofficial Ubuntu 5.04 Starter Guide. **transcode** will be installed side by side with **dvd::rip**.

---

### Post by RIVE on 2005-09-01
I tried again following the instructions in [http://powerpc.ubuntuguide.org/#extrarepositories](http://powerpc.ubuntuguide.org/#extrarepositories) and it gave me this error:

W: GPG error: [http://honk.physik.uni-konstanz.de](http://honk.physik.uni-konstanz.de) mplayer/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BDCE3370C88CEDF6

I need to have that repository to easely install transcode and DVD:RIP.

Any help?

Thanks in advance

---

### Post by pvz on 2005-09-01
I ended up compiling them from source, transcode compiled on my G4 with --disable-altivec. I suppose you could download the needed packages from [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/mplayer/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/mplayer/) and install them and any dependencies with dpkg -i. If all else fails, I can put my handrolled transcode and dvd:rip .debs online, without any guarantees of course.

---

