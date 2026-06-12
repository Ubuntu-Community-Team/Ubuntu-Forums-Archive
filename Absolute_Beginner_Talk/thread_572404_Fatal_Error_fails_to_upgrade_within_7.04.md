---
title: "Fatal Error: fails to upgrade within 7.04"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by nraney on 2007-10-10
Hey guys,
my fiesty fawn wont upgrade to gutsy, which is fine, I can wait for the release.  The only thing is I think there is something else going on; in automatix when I try add wine it fails reporting:

fatal error: wine
an apt-based error occurred and installation was unsuccessful

this also happens after the command 'sudo apt-get update' reporting errors:
err [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty release.gpg
err [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main packages
could not resolve 'wine.lowvoice.nl'
failed to fetch..

this also happens during the upgrade to 7.10:
could not initiate dbus (yeah this happens to alot of other people i know)

but then,
could not download repository indexes,
[http://wine.lowvoice.nl/aptdists/feisty/release.gpg:](http://wine.lowvoice.nl/aptdists/feisty/release.gpg:) could not resolve 'wine.lowvoice.nl'
and some other errors that are still wine but for other files.

I dont need wine for anything I just dont have any idea what is happening.

thanks,
NRaney

---

### Post by philinux on 2007-10-10
I believe your troubles are caused by automatix. It would have been better to uninstall automatix first and then did the upgrade.

As it is now someone may chime in with a solution. I suppose you could press esc at grub and pick and older kernel to get you going.

---

### Post by nraney on 2007-10-10
well that didnt make much sense to me. grub? kernal? yippie.
you really think i should be uninstalling automatix? will that mess up the prog i have installed with it?

---

### Post by zvacet on 2007-10-10
Uninstalling Automatix will not mess programs installed with it.You can also remove every line in your source list refering to Automatix.You can do the same with wine repos lines.You have wine in synaptic,but if you want to add repo 

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

Save the file and 

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by nraney on 2007-10-11
the quick answer to this problem was to disable the third party repositories.  after that everything worked fine.  until i got gutsy and then everything went out the window.. all good now, my linux buddy got it going.

---

