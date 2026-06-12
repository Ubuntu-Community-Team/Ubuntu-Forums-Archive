---
title: "envy install problem"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by lillypilly on 2007-03-31
When trying to install Envy using Mozilla Firefox 2.0.0.3 from Edgy Eft (fully updated)

from the site [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) when I click on the deb file for the latest version of the file and the download page comes up asking what Firefox should do with the file I select to use "Gdebi Package Installer (default)
The file is downloaded but then I get the following error message from the Package Installer "Error: Dependency is not satisfiable: module-assistant

I also tried on another computer using the 7.04 beta and got the same result

---

### Post by Maestro23 on 2007-03-31
It's telling you it needs "module-assistant".  You need to install it first.

In terminal type:

> sudo aptitude install module-assistant.

I would d/l that .deb pkg and use the command:

> sudo dpkg -i .....

---

### Post by lillypilly on 2007-03-31
Thanks for your reply
I did what you suggested and this is what happened

sudo aptitude install module-assistant.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "module-assistant."
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

It would appear that nothing happened.

---

### Post by joshbax on 2007-03-31
try enabling extra repositories.

find that here [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by Maestro23 on 2007-03-31
> **joshbax said:**
> try enabling extra repositories.

find that here [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Beat me to it.:guitar:

---

### Post by lillypilly on 2007-03-31
You are very quick. Thanks very much

A very steep learning curve going here. Old Dos through to XP user but brand new to Linux 4 days ago.

The groups are very helpful and I have been doing a lot of reading.

Thanks once again for your prompt help

---

### Post by Maestro23 on 2007-03-31
> **lillypilly said:**
> You are very quick. Thanks very much

A very steep learning curve going here. Old Dos through to XP user but brand new to Linux 4 days ago.

The groups are very helpful and I have been doing a lot of reading.

Thanks once again for your prompt help

Hang in there.  

Some Ubuntu Links to get you started:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by joshbax on 2007-03-31
i am sort of new to linux too; been running it on my laptop sans xp for about a week, after playing with varios distro's on various machines for the past year.

welcome!

---

