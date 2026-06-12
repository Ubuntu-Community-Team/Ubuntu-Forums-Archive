---
title: "[SOLVED] VirtualBox in 64Bit Gusty"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-10-31
I have been to the VirtualBox website and done the automated download and install [VirtualBox Downloads]("http://www.virtualbox.org/wiki/Downloads")

I add the [HTML] deb http://www.virtualbox.org/debian gutsy non-free[/HTML] fine but I get a error when I reload it, this is the error I get:

[HTML]W: GPG error: http://www.virtualbox.org gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73[/HTML]

So I go click on the link to save the key (innotek.asc) and save it to my Desktop, the I open up Terminal and type:
[HTML]apt-key add innotek.asc[/HTML] and I get this error
[HTML]ian@ian-desktop:~$ cd Desktop
ian@ian-desktop:~/Desktop$ apt-key add innotek.asc
gpg: no writable keyring found: eof
gpg: error reading `innotek.asc': general error
gpg: import from `innotek.asc' failed: general error
ian@ian-desktop:~/Desktop$[/HTML]

Any ideas whats going wrong??

---

### Post by overdrank on 2007-10-31
Hi I just installed it on my system and I had to add the key via software sources. System, administration, software sources and the authentication tab and import a key and direct it to the key saved on your desktop. Hope this helps and good luck!

---

### Post by ianb72 on 2007-10-31
Thank that seemed to do the job :)

---

