---
title: "Trouble with Update Manager"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Afkpuz on 2008-02-12
Hey, I was doing a check for updates and the progress bar stopped moving.  I clicked cancel, and now I get this error message in terminal when I try to sudo apt-get update

```
Failed to fetch http://marillat.free.fr/dists/unstable/Release.gpg  Could not resolve 'marillat.free.fr'
Failed to fetch http://marillat.free.fr/dists/unstable/main/i18n/Translation-en_US.bz2  Could not resolve 'marillat.free.fr'
Failed to fetch http://marillat.free.fr/dists/unstable/main/binary-i386/Packages.gz  Could not resolve 'marillat.free.fr'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

How do I fix these dependencies?

---

### Post by taurus on 2008-02-12
Maybe that site is down.  So, you can edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of that reps (or repos) to comment it out.  Save it and close gedit.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kwacka on 2008-02-12
You are not connecting to the repositories listed at marillat.free.fr. Try updating again, its possible the site was down for a while.

If it still gives an error (and you can still connect to other sites) come back here.

---

### Post by Afkpuz on 2008-02-12
Fixed.  I had added some repos for freevo and those were causing the problem.  removed them and all is well!

---

