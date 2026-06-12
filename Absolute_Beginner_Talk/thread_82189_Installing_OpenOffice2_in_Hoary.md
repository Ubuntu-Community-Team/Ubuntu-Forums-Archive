---
title: "Installing OpenOffice2 in Hoary"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by gandalf458 on 2005-10-26
I've downloaded Open Office 2 (to my desktop) and expanded the compressed file (also to the desktop) but now I'm stuck. The instructions say:
> Installation Steps

   1. Unpack the downloaded image into a directory. For example, currently, the following command would unpack into the current directory:
   2. tar xvzf OOo_2.0.0_LinuxIntel_install.tar.gz
   3. Su to root, if necessary.
   4. cd into the directory with the unpacked image. This could be RPMS.
   5. Delete any rpm files that do not apply to your system. For example, on a Fedora Core 3 system, delete any rpms specific to another distribution such as openofficeorg-suse-menus-1.9.79-1.noarch.rpm.
   6. Then execute rpm -Uvih *rpm.

so I guess I've done 1 & 2. Can anyone advise me please?

---

### Post by CyiPherX on 2005-10-26
Have you tried just letting the "Synaptic Package manager" install it for you, makes it alot easier, although you would, i guess have to download it again.

CyiPherX

---

### Post by gandalf458 on 2005-10-26
No, I haven't, thanks. However Synaptic Package Manager doesn't seem to consider OOo 2.0 a new version of OOo but it seems to be a new package. Will it handle a new package? I can't figure how to add a new package to SPM.

---

### Post by aysiu on 2005-10-26
You don't add packages to Synaptic--you use Synaptic to install packages (see the second link in my sig for how it works). If you want to use the terminal, you can install OpenOffice 2.0 with a simple command ```
sudo apt-get install openoffice.org2
``` That's it. It'll download, unpack, and install it for you. **You do not need to download anything separately**. That one command does everything.

---

### Post by gandalf458 on 2005-10-26
The command line looks easiest but I've bookmarked your software install page for future reference. Thanks G :)

---

### Post by gandalf458 on 2005-10-27
sudo apt-get install openoffice.org2

doesn't work. It says Couldn't find package openoffice.org2

I also tried your Software Installation instructions using Synaptic but searching name and description for open office does not find OpenOffice.org v2.

I guess I'm doing something wrong but I can't figure out what.

---

### Post by aysiu on 2005-10-27
Are you using Hoary (Ubuntu 5.04)? That could be the problem. OpenOffice2 is available in the regular Breezy repositories for Breezy (Ubuntu 5.10), but, according to [this search](http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=openoffice.org2&searchon=names), you may have to [enable the Universe repositories](http://www.psychocats.net/sources.html) in Hoary to get OpenOffice.org2.

---

### Post by gandalf458 on 2005-10-27
Yes, I'm using Ubuntu 5.04. As I'm still getting the hang of Linux it may take me a while to get to grips with updating the repositories. If I download 5.10 can I install it over 5.04 without overwriting my data? Thanks G :)

---

### Post by aysiu on 2005-10-27
Don't upgrade to 5.10 *just* to get OpenOffice2. In fact, I'd advise against upgrading to 5.10 (if you want to upgrade--maybe wait until Dapper 6.04). Follow the instructions I linked to above (enabling the hoary universe repositories--don't follow the breezy instructions). Then type this in a terminal ```
sudo apt-get update
sudo apt-get install openoffice.org2
```

---

### Post by gandalf458 on 2005-10-27
Many thanks for the advice. G :)

It's downloading now...

---

### Post by gandalf458 on 2005-10-28
It seems to have all installed - very impressive. One query though - it has installed v 1.9.? rather than the latest 2.0. Is that because the Universe Repository takes a while to get updated?

---

