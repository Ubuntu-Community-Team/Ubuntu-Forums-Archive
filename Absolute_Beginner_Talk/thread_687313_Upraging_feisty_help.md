---
title: "Upraging feisty help"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Vamp381 on 2008-02-04
Hi all. I downloaded alternate cd and when i want to update i get this error:

```
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
```

HELP ;-<


When i check for updates i get 

[http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg:](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg:) Could not resolve 'archive.ubuntustudio.org'
[http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2:](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntustudio.org'
[http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntustudio.org'
[http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://gandalfn.club.fr/ubuntu/dists/edgy/dev/binary-i386/Packages.gz:](http://gandalfn.club.fr/ubuntu/dists/edgy/dev/binary-i386/Packages.gz:) 404 Not Found

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181

---

### Post by spiderbatdad on 2008-02-04
looks like ubuntustudio.org may have been down.
As for TuxFamily. You  did not add the public key when you added the repo...or they changed it. You will have to contact their site to get the public key, and there should be instructions for adding their repo and public key. Or remove it from your sources list if you do not want it in there.

---

