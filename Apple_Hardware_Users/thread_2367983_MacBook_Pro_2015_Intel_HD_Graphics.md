---
title: "MacBook Pro 2015 Intel HD Graphics"
date: 2017-08-05
forum: Apple Hardware Users
---

### Post by Donnut on 2017-08-05
Hi all. Is there a good tutorial on how to upgrade the Intel HD graphics on Ubuntu? My gaming performance is pretty bad and I have no 3D acceleration in VMware.

---

### Post by Donnut on 2017-08-05
So, I downloaded the update tool, but it gives me this error and I'm not sure how to fix it.
```
Finished : W:GPG error: https://download.01.org/gfx/ubuntu/17.04/main zesty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 611B903CAB97EA77, E:The repository 'https://download.01.org/gfx/ubuntu/17.04/main zesty InRelease' is not signed., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://ppa.launchpad.net/killhellokitty/themes.ppa/ubuntu zesty Release' does not have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://ppa.launchpad.net/tualatrix/next/ubuntu zesty Release' does not have a Release file.  [  ] &#9702;
src/main-window.c/on_transaction_finished: Package transaction finished with an error

```

---

### Post by Donnut on 2017-08-05
So, I downloaded the update tool, but it gives me this error and I'm not sure how to fix it.
```
Finished : W:GPG error: https://download.01.org/gfx/ubuntu/17.04/main zesty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY
 611B903CAB97EA77, E:The repository 'https://download.01.org/gfx/ubuntu/17.04/main zesty InRelease' is not signed., W:Updating from such a repository can't be done securely, and is therefore 
disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://ppa.launchpad.net/killhellokitty/themes.ppa/ubuntu zesty Release' 
does not have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user 
configuration details., E:The repository 'http://ppa.launchpad.net/tualatrix/next/ubuntu zesty Release' does not have a Release file.  [  ] &#9702;
src/main-window.c/on_transaction_finished: Package transaction finished with an error

```

---

### Post by miqrojamie on 2017-08-08
For VMWare just put this into your .vmware/preferences file:

mks.gl.allowBlacklistedDrivers = "TRUE"

Should fix the 3D acceleration and virtual acceleration problem.

---

