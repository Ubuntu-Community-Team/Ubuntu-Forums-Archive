---
title: "software index is broken"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by botheredbybees on 2006-12-29
Hi, I just tried to update f-spot to the latest version (0.3.0-1) using the debian package on packages.debian.org

It told me I had an unmet dependency, which I installed, but now I'm getting an error message in synaptic: 'Software index is broken'

When I run sudo apt-get install -f
 it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I can search for broken packages in synaptic it finds libfontconfig1 2.3.2-7ubuntu2 but when I try to re-install or remove this package synaptic lists about 100 other applications that must be removed as well

I think I'd like to just go back to the way things were - is there a rollback option somewhere?
:confused:

---

### Post by botheredbybees on 2007-01-02
well,
yes; there is a way to roll this back:

sudo aptitude purge fonconfig-config

thanks to nblit for this tidbit -> [http://ubuntuforums.org/showthread.php?p=1928618]("http://ubuntuforums.org/showthread.php?p=1928618")


=D>

---

