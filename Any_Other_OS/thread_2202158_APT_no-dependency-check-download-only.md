---
title: "APT no-dependency-check-download-only?"
date: 2014-01-27
forum: Any Other OS
---

### Post by wolfgentleman on 2014-01-27
Basically I used apt-rdepends to get a complete package list of dependencies, now I want to download those packages. I also want to download them in i386 not just amd64. Any ideas?

I could not figure out where to put this thread, so if there is a better place for it...

---

### Post by ian-weisser on 2014-01-27
I do not understand why you would want such a thing.

Nevertheless: Script it.
For each package in the dependency list, 
Use   apt-cache <packagename> | grep Filename: | cut -d" " -f2   to get the archive path for that package.
Prepend the mirror name or IP address on the front of the archive path to create the URL for that package
Wget the package URL.

---

### Post by wolfgentleman on 2014-01-27
> **ian-weisser said:**
> I do not understand why you would want such a thing.
I am trying to get KDE (the PIM module to be specific) 4.8+ (that's when groupdav resource came in) on LMDE and breaking as little as possible. So I added Debian Jessie repo, commented out LMDE repos, apt-get update, then did an rdepends on kde-full, then I reversed the commented repos in sources.list and apt-get update. Since I have a repo already I might as well grab kde-full and all of it's deps recursively of both i386 and amd64, then dump it in a new section. Also I filtered the ones that did not have version requirements to prevent breakage and simplicity.
> **ian-weisser said:**
> Nevertheless: Script it.
For each package in the dependency list, 
Use   apt-cache <packagename> | grep Filename: | cut -d" " -f2   to get the archive path for that package.
Prepend the mirror name or IP address on the front of the archive path to create the URL for that package
Wget the package URL.
I think I understood that... will try in a bit.

---

### Post by ian-weisser on 2014-01-27
> **wolfgentleman said:**
> I am trying to get KDE (the PIM module to be specific) 4.8+ (that's when groupdav resource came in) on LMDE and breaking as little as possible. So I added Debian Jessie repo, commented out LMDE repos, apt-get update, then did an rdepends on kde-full, then I reversed the commented repos in sources.list and apt-get update. Since I have a repo already I might as well grab kde-full and all of it's deps recursively of both i386 and amd64, then dump it in a new section. Also I filtered the ones that did not have version requirements to prevent breakage and simplicity.

Watch out that your dependency list (and script) doesn't start replacing a lot of Ubuntu packages needlessly. A fully-recursive list of dependencies may take you pretty deep down a rabbit hole.
 
Mixing Debian and Ubuntu packages sometimes works...and sometimes doesn't. Compiled binaries may be compiled against different toolchains (that's always fun), and the two versions may have rather differently-versioned dependency requirements.

If you run into problems, it may be worthwhile to back up and try installing the PIM from tarball or source. Those have their own problems, naturally.

---

### Post by wolfgentleman on 2014-01-28
> **ian-weisser said:**
> Watch out that your dependency list (and script) doesn't start replacing a lot of Ubuntu packages needlessly. A fully-recursive list of dependencies may take you pretty deep down a rabbit hole.
 That's why I killed anything that didn't have version requirements.

> **ian-weisser said:**
> Mixing Debian and Ubuntu packages sometimes works...and sometimes doesn't. Compiled binaries may be compiled against different toolchains (that's always fun), and the two versions may have rather differently-versioned dependency requirements.
I'm not mixing Ubuntu and Debian. Debian Jessie packages with Linux Mint Debian Edition... I posted here because this community gets faster replies and tends to be a lot nicer than others. That and it was more of a Debian-based OS in general question. I may end up just grabbing the Ubuntu based LM... although then I can't use the Kali repos so I may try to find a PPA or something with the wanted packages... Ugh. Why did they have to move to Debian base rather than Ubuntu like before?!? I have been battling to find a happy medium between KDE 4.8+ on a purely Debian based OS or Kali repos in a purely Ubuntu based OS, with no luck. I try LMDE, its not based on the latest Debian Jessie. Try Debian Jessie, everything tends to break but that is to be expected with testing. Try regular LM KDE or Kubuntu, Kali repos break things but again that's to be expected when mixing Debian and Ubuntu packages... ](*,)

> **ian-weisser said:**
> If you run into problems, it may be worthwhile to back up and try installing the PIM from tarball or source. Those have their own problems, naturally.

I thought about doing that, but it seemed like a bit more of a hassle than I wanted to deal with... I didn't feel like doing the init scripts, ect.

---

### Post by oldos2er on 2014-01-28
Moved to Other OS/Distro Support.

---

