---
title: "Cannot install Firefox on Debian"
date: 2011-08-31
forum: Any Other OS
---

### Post by stamatiou on 2011-08-31
Hey guys, I wanted to install Firefox on Debian so I downloaded and extracted the bz2 file from Mozilla.org but when I run the ./firefox or ./firefox-bin it tells me:
```
/firefox-bin: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

```

---

### Post by Zill on 2011-08-31
My understanding is that the [Debian project]("http://en.wikipedia.org/wiki/Mozilla_Corporation_software_rebranded_by_the_Debian_project") prefers to use [Iceweasel]("http://wiki.debian.org/Iceweasel") rather than Firefox.  Iceweasel is functionally identical to Firefox and can easily be installed with the following command:
```
apt-get install iceweasel (as root)
```
or
```
sudo apt-get install iceweasel (as user)

```

---

### Post by snowpine on 2011-08-31
A quick google shows me this error is often caused by trying to install 32-bit Firefox on a 64-bit system, for example: [http://forums.debian.net/viewtopic.php?f=10&t=66639](http://forums.debian.net/viewtopic.php?f=10&t=66639)

Of course, you could just use Iceweasel, which is the Debian name for Firefox. :)

---

### Post by Sef on 2011-08-31
Moved to other OS Talk.

---

### Post by bug67 on 2011-08-31
Might give this a shot.  Haven't tried it myself...

[http://forums.debian.net/viewtopic.php?f=16&t=62113](http://forums.debian.net/viewtopic.php?f=16&t=62113)

---

### Post by NightwishFan on 2011-09-01
Iceweasel is exactly the same as Firefox. You can get builds of it here:
[http://mozilla.debian.net/](http://mozilla.debian.net/)

---

### Post by stamatiou on 2011-09-01
I wanted to install firefox because on Ubuntu I had Firefox sync on and would like to synd my  bookmarks between my os changes. Is that possible? Also does Iceweasel being update as sonn as Firefox is because as for the look it looks like old versions of firefox.
Finally why does Debian have Iceweasel and not Firefox?

---

### Post by NightwishFan on 2011-09-01
> I wanted to install firefox because on Ubuntu I had Firefox sync on and would like to synd my  bookmarks between my os changes. Is that possible?
Iceweasel is Firefox as I said, so I do not see why not. Just upgrade to the newest version. This is take from Iceweasel 6 on my Debian 6 system:
[IMG]http://img21.imageshack.us/img21/1544/firefoxua.png[/IMG]


> Also does Iceweasel being update as sonn as Firefox is because as for the look it looks like old versions of firefox.
Debian does not have a newer version in it's main repository because it is not Debian's policy to constantly upgrade software that is proven to work. That is why the current release is branded 'Stable'. The software does not change often except for security upgrades.

Follow these instructions here to install the latest firefox/iceweasel on Debian. Please ask if you need help. :)
[http://mozilla.debian.net/](http://mozilla.debian.net/)


> Finally why does Debian have Iceweasel and not Firefox?
Simple. Debian supports a version of Firefox for a longer period than Mozilla does. Mozilla asked if Debian works on a version of Firefox that Mozilla has abandoned to not use the Firefox name and logo. That is the only difference. I heard the Debian Iceweasel maintainer actually works for Mozilla also.

[https://secure.wikimedia.org/wikipedia/en/wiki/Mozilla_software_rebranding](https://secure.wikimedia.org/wikipedia/en/wiki/Mozilla_software_rebranding)
[http://raphaelhertzog.com/2011/02/03/people-behind-debian-mike-hommey-firefox-iceweasel-maintainer/](http://raphaelhertzog.com/2011/02/03/people-behind-debian-mike-hommey-firefox-iceweasel-maintainer/)

---

