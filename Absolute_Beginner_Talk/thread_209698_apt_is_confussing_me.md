---
title: "apt is confussing me"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by ikex on 2006-07-05
i was just wondering if there is a way to make apt think it removed a package or installed it even know the package failed to install. I'm asking this because of,

```
Preparing to replace gtk-engines-xenophilia 0.8-3 (using .../gtk-engines-xenophilia_0.8-3_i386.deb) ...
Unpacking replacement gtk-engines-xenophilia ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: error processing /var/cache/apt/archives/gtk-engines-xenophilia_0.8-3_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/gtk-engines-xenophilia_0.8-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i keep getting that i can't remove it , i can't install it , and i can't install / upgrade anything else. 

ive tried apt-get -f remove gtk-engines-xenophilia , dpkg --force-all --remove gtk-engines-xenophilia

and im lost on what else i could do, any help would be greatly appreciated. :D

---

### Post by LKRaider on 2006-07-05
Try to contact the author of the package about this, as it is a bug on the packaging.
He should repackage and release a working one, so you can install over correctly.

---

### Post by ikex on 2006-07-05
Ok thanks, i think i may have caused it to happen tho, i modified my sources list for Edgy Eft and did a apt-get update before apt-get dist-upgrade, i wasn't thinking, ill try and contact the author anyway. so there would be no way for me to 'trick' dpkg into thinking it's install while i finish dist-upgrade then try and retry it or get dpkg to think its removed since it hasn't actually installed anything yet afaik. :(

Edit: 
I fixed it for the moment by installing an older version and continuing with the update.

---

