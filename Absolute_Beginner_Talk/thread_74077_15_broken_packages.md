---
title: "15 broken packages"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by jeffjanzen on 2005-10-10
i wanted to install vlc, so i downloaded the deb package and typed "dpkg -i vlc_0.8.4-svn20050920-3_i386.deb" at the root terminal, which yielded a list of dependencies:
[INDENT]dpkg: dependency problems prevent configuration of vlc:
 vlc depends on libaa1 (>= 1.2); however:
  Package libaa1 is not configured yet.
 vlc depends on libc6 (>= 2.3.5-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
 vlc depends on libdvbpsi4; however:
  Package libdvbpsi4 is not configured yet.
 vlc depends on libflac7; however:
  Package libflac7 is not configured yet.
 vlc depends on libgcc1 (>= 1:4.0.1); however:
  Package libgcc1 is not configured yet.
 vlc depends on libgpg-error0 (>= 1.1); however:
  Package libgpg-error0 is not configured yet.
 vlc depends on libmodplug0c2 (>= 1:0.7-4.1); however:
  Package libmodplug0c2 is not installed.
 vlc depends on libmpeg2-4; however:
  Package libmpeg2-4 is not configured yet.
 vlc depends on libncurses5 (>= 5.4-5); however:
  Package libncurses5 is not configured yet.
 vlc depends on libslang2 (>= 2.0.1-1); however:
  Package libslang2 is not configured yet.
 vlc depends on libstdc++6 (>= 4.0.1); however:
  Package libstdc++6 is not configured yet.
 vlc depends on libtar; however:
  Package libtar is not configured yet.
 vlc depends on libxml2 (>= 2.6.21); however:
  Package libxml2 is not configured yet.
 vlc depends on wxvlc; however:
  Package wxvlc is not configured yet.
dpkg: error processing vlc (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vlc[/INDENT]
i found all of these packages at the vlc website (.deb packages) and installed them ("dpkg -i ./*").  (there were no error messages.  everything seemed to go smoothly.)
NOW, trying to install the vlc deb package gives me the *same* error messages, and synaptic package manager warns me that "you have 15 broken packages on your system!"  the big problem is that synaptic will not remove the *broken* packages without also removing *essential* packages like bash and dpkg.
can i fix these broken packages so i don't have to remove them?  or can i just remove the damaged packages, if i avoid synaptic package manager?  why didn't this method of installation of new packages work?  why are these packages damaged after a seemingly seamless installation routine?  where did i go wrong?

---

### Post by Kyral on 2005-10-10
Because you are supposed to install VLC from the Ubuntu Repos (Like Synaptic).

Fire up the console and try

```
sudo apt-get -f install
```

That SHOULD fix it...I hope..

---

### Post by Leif on 2005-10-10
please remove all the broken packages, enable universe and multiverse as detailed in ubuntuguide.org, and simply install vlc from the repositories

---

### Post by jeffjanzen on 2005-10-10
is it safe to remove the ESSENTIAL packages? (apt, bash, dpkg, ncurses-bin, sysvinit, and util-linux will all be removed.)  this is the only condition under which synaptic will let me remove the broken packages.

---

### Post by Leif on 2005-10-10
god no, don't remove apt or bash or such. try enabling the repositories I suggested before, and upgrade. maybe that'll sort things out. also, try what kyral said

---

### Post by jeffjanzen on 2005-10-10
(i have added extra repositories, following ubuntuguide's instructions, before this whole mess began.  thanks for the suggestion, anyway.)
"apt-get -f install" yields the same warning message as synaptic:  essential packages must be removed if i want to remove the broken ones.  meanwhile, apt and synaptic won't let me install anything new until i've fixed the broken packages.  bummer.

---

### Post by darkmatter on 2005-10-10
Just remove the vlc packages you installed manually.

Search Synaptic for the PROPER versions and intall from there.

---

### Post by jeffjanzen on 2005-10-10
i've successfully removed 9 packages manually, but essential packages still depend on libgcc1, libgpg-error0, libncurses5, libncurses5-dev, libvorbis-dev, and libxml2, so i can't remove those manually.
could i install other libraries that would replace these damaged ones?  does that make sense?:confused:

---

### Post by Wolki on 2005-10-11
[QUOTE=jeffjanzen]i've successfully removed 9 packages manually, but essential packages still depend on libgcc1, libgpg-error0, libncurses5, libncurses5-dev, libvorbis-dev, and libxml2, so i can't remove those manually.
could i install other libraries that would replace these damaged ones?  does that make sense?:confused:[/QUOTE]

Looks like you tried to install debian packages for central system files on Hoary? Hm.... very bad situation. In synaptic, try whether you can force other versions of those packages (crtl+e). If not, an upgrade to breezy might help, if you can, as the versions are newer and should replace the debian ones. No guarantees though.

---

### Post by jeffjanzen on 2005-10-11
"Force Version..." doesn't work.  it looks like synaptic has to remove those essential packages to force a different version, too.
it's a good trick to know, though.  it may come in handy in the future.  thank you for trying.
when can i expect the official (stable) release of breezy?

---

### Post by Wolki on 2005-10-11
[QUOTE=jeffjanzen]"Force Version..." doesn't work.  it looks like synaptic has to remove those essential packages to force a different version, too.
it's a good trick to know, though.  it may come in handy in the future.  thank you for trying.
when can i expect the official (stable) release of breezy?[/QUOTE]

I thought so :-/
Breezy goes stable (if there's no delay) in 2 days, on the 13th. Basically, you can go for it now if you're on broadband (i think there'll still be a round of updates). I'm not sure it will work though, you might have to reinstall. Or ask someone who knows more than me ^^;;;

---

### Post by jeffjanzen on 2005-10-11
FIXED!
i searched my ubuntu install cdrom for good versions of my broken libraries and reinstalled the versions existing on the cd (using dpkg at the root terminal), which forced out the broken packages.  basically, a manual "Force Version..."  too bad synaptic couldn't do that for me...

---

