---
title: "Problem upgrading to 7.04"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by cledezma on 2007-04-07
Hi everyone:

I am newbie running Ubuntu 6.10. Today I tried to upgrade to version 7.04 (beta) and I got the following message:

"Error during update: A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry."

And then I see a list like this:

Failed to fetch [http://ubuntu2.lupine.me.uk/dists/edgy/Release.gpg](http://ubuntu2.lupine.me.uk/dists/edgy/Release.gpg) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu2.lupine.me.uk/dists/edgy/main/i18n/Translation-en_US.bz2](http://ubuntu2.lupine.me.uk/dists/edgy/main/i18n/Translation-en_US.bz2) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/Release.gpg](http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/Release.gpg) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/|/i18n/Translation-en_US.bz2 Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/sudo/i18n/Translation-en_US.bz2](http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/sudo/i18n/Translation-en_US.bz2) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/apt-key/i18n/Translation-en_US.bz2](http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/apt-key/i18n/Translation-en_US.bz2) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/add/i18n/Translation-en_US.bz2](http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/add/i18n/Translation-en_US.bz2) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/-/i18n/Translation-en_US.bz2](http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/-/i18n/Translation-en_US.bz2) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu2.lupine.me.uk/dists/edgy/main/binary-i386/Packages.gz](http://ubuntu2.lupine.me.uk/dists/edgy/main/binary-i386/Packages.gz) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://media.blutkind.org/xgl/dists/dapper/main/binary-i386/Packages.gz](http://media.blutkind.org/xgl/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/|/binary-i386/Packages.gz Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/sudo/binary-i386/Packages.gz](http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/sudo/binary-i386/Packages.gz) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/apt-key/binary-i386/Packages.gz](http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/apt-key/binary-i386/Packages.gz) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://media.blutkind.org/xgl/dists/dapper/aiglx/binary-i386/Packages.gz](http://media.blutkind.org/xgl/dists/dapper/aiglx/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/add/binary-i386/Packages.gz](http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/add/binary-i386/Packages.gz) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/-/binary-i386/Packages.gz](http://ubuntu2.lupine.me.uk/1609B551.gpg/dists/-O-/-/binary-i386/Packages.gz) Could not resolve 'ubuntu2.lupine.me.uk'
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main-edgy/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/edgy/main-edgy/binary-i386/Packages.gz) 404 Not Found [IP: 195.114.19.35 80]

Do you have any idea of what is going on?

Thanks!

---

### Post by userundefine on 2007-04-07
Looks like [http://ubuntu2.lupine.me.uk/](http://ubuntu2.lupine.me.uk/) is offline.  I can't hit it from my browser either.  That's not an official repo, though, where'd you get it?

---

