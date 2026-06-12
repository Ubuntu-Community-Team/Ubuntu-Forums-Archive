---
title: "can't execute new version firefox on linx mint v15"
date: 2014-01-25
forum: Any Other OS
---

### Post by bw2 on 2014-01-25
/home/<usr>/firefox26/firefox: No such file or directory
~/firefox26/firefox: No such file or directory
./firefox: No such file or directory

i downloaded a new version of firefox, untarred it into its own dir in my home dir. but when i try to execute it either from a terminal or file manager i get the above error. i'm the owner and it is marked executable. os is linux mint 15

what am i missing here?

---

### Post by vasa1 on 2014-01-25
> **bw2 said:**
> /home/<usr>/firefox26/firefox: No such file or directory
~/firefox26/firefox: No such file or directory
./firefox: No such file or directory

i downloaded a new version of firefox, untarred it into its own dir in my home dir. but when i try to execute it either from a terminal or file manager i get the above error. i'm the owner and it is marked executable. os is linux mint 15

what am i missing here?
Did you by chance download Firefox 32-bit and is your Mint 64-bit?

---

### Post by Impavidus on 2014-01-25
What about ~/firefox/firefox? The package contains the firefox executable inside the firefox directory, which you say you unpacked in your home directory.

But as you use mint 15, which, if I'm correct, uses the still (just) supported Ubuntu 13.04 repository, you should have got Firefox 26 automatically. Or am I mistaken?

(Edit: Oh, wait, I just read there is a debian edition too. That one may be different, but it should still be possible to upgrade to the latest firefox using the package manager.)

---

### Post by bw2 on 2014-01-25
> **vasa1 said:**
> Did you by chance download Firefox 32-bit and is your Mint 64-bit?

oops, yep i sure did dl a 32-bit ver on this x86_64 mint. 

thanks for catching that!

---

### Post by bw2 on 2014-01-25
> **Impavidus said:**
> What about ~/firefox/firefox? The package contains the firefox executable inside the firefox directory, which you say you unpacked in your home directory.

But as you use mint 15, which, if I'm correct, uses the still (just) supported Ubuntu 13.04 repository, you should have got Firefox 26 automatically. Or am I mistaken?

(Edit: Oh, wait, I just read there is a debian edition too. That one may be different, but it should still be possible to upgrade to the latest firefox using the package manager.)

the script in /usr/bin/firefox is starting up v25 currently.

yeah, i was experimenting about with a few firefox upgrades. looks like i dl'd i686/32bit versions and not x86_64. as "vasa1" replied, more than likely my error there. 

appreciate your help

---

### Post by oldos2er on 2014-01-25
Moved to Other OS/Distro Support.

---

