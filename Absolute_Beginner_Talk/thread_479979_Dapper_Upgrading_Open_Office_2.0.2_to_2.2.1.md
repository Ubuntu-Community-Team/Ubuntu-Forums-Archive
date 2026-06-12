---
title: "Dapper: Upgrading Open Office 2.0.2 to 2.2.1"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by rodtempleton on 2007-06-20
Title pretty much says it all, but I just downloaded the 2.2.1 version of Open Office.  I'm presuming I need to remove 2.0.2 before installing it?

Any special instructions?  Any information that anyone could provide would be greatly appreciated.

Cheers,
Rod

---

### Post by ym4546 on 2007-06-20
> **rodtempleton said:**
> Title pretty much says it all, but I just downloaded the 2.2.1 version of Open Office.  I'm presuming I need to remove 2.0.2 before installing it?

Any special instructions?  Any information that anyone could provide would be greatly appreciated.

Cheers,
Rod
Where did you get Open Office 2.2.1?.. the repository version is only 2.0.2

I'm assuming this is from the openoffice.org website or a source tarball...
I think that you can just run sudo aptitude, find openoffice.org (press "/", type "openoffice.org", and press "n" until you find it), then press "-" to remove it. As far as I know, ubuntu-desktop only recommends it, it does not depend on this package, so removing it should be okay.

---

### Post by rodtempleton on 2007-06-20
> **ym4546 said:**
> Where did you get Open Office 2.2.1?.. the repository version is only 2.0.2

I'm assuming this is from the openoffice.org website or a source tarball...
I think that you can just run sudo aptitude, find openoffice.org (press "/", type "openoffice.org", and press "n" until you find it), then press "-" to remove it. As far as I know, ubuntu-desktop only recommends it, it does not depend on this package, so removing it should be okay.

Got it from th open office site.  I'll give this a try.  Thanks for the tip.

Cheers,
Rod

---

### Post by mtron on 2007-06-21
Hello!

Just installed the new OpenOffice 2.2.1 on dapper 2 day, and it's working much better now :)

i found deb packages [here]("http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.2.1/latest/") (download them with wget it's ~ 130 MB)
```
wget http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.2.1/latest/OOo_2.2.1_LinuxX86_install_en-US_deb.tar.gz
```

While it's downloading fire up synaptic and remove all installed OpenOffice packages.

After the download is finished, unpack the archive and cd in a terminal to the unpack folder (it's named "debs") inside the folder type
```
sudo dpkg -i *.deb
```

now all the debs in this folder will be installed. For the gnome-menu integration cd in the folder "desktop-integration" and install the deb file with
```
sudo dpkg -i openoffice.org-debian-menus_2.2-9161_all.deb
```

That's it. Enjoy a stable and much less buggy Openoffice.

---

### Post by L Campbell on 2007-06-21
> **mtron said:**
> Hello!

Just installed the new OpenOffice 2.2.1 on dapper 2 day, and it's working much better now :)

i found deb packages [here]("http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.2.1/latest/") (download them with wget it's ~ 130 MB)
```
wget http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.2.1/latest/OOo_2.2.1_LinuxX86_install_en-US_deb.tar.gz
```

While it's downloading fire up synaptic and remove all installed OpenOffice packages.

After the download is finished, unpack the archive and cd in a terminal to the unpack folder (it's named "debs") inside the folder type
```
sudo dpkg -i *.deb
```

now all the debs in this folder will be installed. For the gnome-menu integration cd in the folder "desktop-integration" and install the deb file with
```
sudo dpkg -i openoffice.org-debian-menus_2.2-9161_all.deb
```

That's it. Enjoy a stable and much less buggy Openoffice.

Thanks for sharing this.

Will this also work for Feisty, or would I have to change any of the code?

---

### Post by mtron on 2007-06-21
Can't be 100% sure but i would say Yes, it will work on feisty exactly like it's outlined here.

Could you report your test results from feisty please?

---

### Post by Hagar Delest on 2007-06-22
For information, in the future, if you want to upgrade without waiting for someone to produce .debs, you can do it yourself, see here : See this thread : [[Ubuntu] Installing OOo on Debian and Co.]("http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759")

---

