---
title: "outdated existing packages"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by gulmer on 2007-06-07
Is there a way to get an upgrade to a package that is loaded but is an older version and I need the new version to work with my hardware. The gphoto2 version that is in the repository and loaded is an old version and doesn't have my camera model listed,but, the new version does. Thanks for a reply.

---

### Post by jfinkels on 2007-06-07
> **gulmer said:**
> Is there a way to get an upgrade to a package that is loaded but is an older version and I need the new version to work with my hardware. The gphoto2 version that is in the repository and loaded is an old version and doesn't have my camera model listed,but, the new version does. Thanks for a reply.

I believe you can forbid a certain version of a package from being installed.

From the man page for aptitude:
```
       forbid-version
          Forbid a package from being upgraded to a particular version. This
          will prevent aptitude from automatically upgrading to this version,
          but will allow automatic upgrades to future versions. By default,
          aptitude will select the version to which the package would normally
          be upgraded; you may override this selection by appending
          &#8220;=<version>&#8221; to the package name: for instance, &#8220;aptitude
          forbid-version vim=1.2.3.broken-4&#8221;.

          This command is useful for avoiding broken versions of packages
          without having to set and clear manual holds. If you decide you
          really want the forbidden version after all, the &#8220;install&#8221; command
          will remove the ban.

```

So you might type something like this in the terminal:```
sudo aptitude fobid-version gphoto=2.2.0-3
```

I have never done this, though, so don't rely on me :D Give it a try, though.

---

### Post by tbroderick on 2007-06-07
What version of Ubuntu are you using, Dapper, Edgy. Feisty, etc.? And what version of gphoto2 do you need?

---

### Post by 5-HT on 2007-06-07
If the version you'd like hasn't been backported, you'll need to either compile it yourself or track down a ubuntu{version}-compatible build (perhaps from the projects website if available). If you are not familiar with compiling from source there is plenty of information/guides/walkthroughs on the wiki and forums.

---

### Post by Fidelio on 2007-06-07
> **5-HT said:**
> If the version you'd like hasn't been backported, you'll need to either compile it yourself or track down a ubuntu{version}-compatible build (perhaps from the projects website if available). If you are not familiar with compiling from source there is plenty of information/guides/walkthroughs on the wiki and forums.
You mean ubuntu's release philosophy results in them having out of date software in the repositories? Which philosophy is that?

---

### Post by 5-HT on 2007-06-07
> **Fidelio said:**
> You mean ubuntu's release philosophy results in them having out of date software in the repositories? Which philosophy is that?

The repositories for a version are frozen save for security security updates/important bug fixes  (in certain warranted circumstances, however, a package may be updated for other reasons). If one wants to update packages in Ubuntu to newer versions one can either: i) enable backports, ii) update to a more recent Ubuntu release, iii) compile the desired packages, iv) find the binaries somewhere, or v) use some unofficial repos.

If you'd like to always use bleeding edge software without waiting for a new Ubuntu release, using a rolling release distro would be more appropriate (personal vote here for Arch, but there are plenty of great ones. For a Debian-based system: Debian Sid is worth checking out).

---

### Post by gulmer on 2007-06-07
> **tbroderick said:**
> What version of Ubuntu are you using, Dapper, Edgy. Feisty, etc.? And what version of gphoto2 do you need?

Dapper 6.06- gphoto2 version 2.1.6 installed and I need version 2.3.1
I downloaded this version from their web site, I just do not know how to get it into the repository. I've got both the gphoto2 and the libgphoto2 in a file in the home folder. They were loaded to the HDD.

---

### Post by jfinkels on 2007-06-07
> **gulmer said:**
> Dapper 6.06- gphoto2 version 2.1.6 installed and I need version 2.3.1
I downloaded this version from their web site, I just do not know how to get it into the repository. I've got both the gphoto2 and the libgphoto2 in a file in the home folder. They were loaded to the HDD.

Oohh, I think I misunderstand your question (the wording was a bit confusing :P)...Just uninstall the version installed:```
sudo aptitude remove libgphoto2 gphoto2
```then double click on the .deb files you have to install them using GDebi. Will that work?

---

### Post by tbroderick on 2007-06-07
> **gulmer said:**
> Dapper 6.06- gphoto2 version 2.1.6 installed and I need version 2.3.1
I downloaded this version from their web site, I just do not know how to get it into the repository. I've got both the gphoto2 and the libgphoto2 in a file in the home folder. They were loaded to the HDD.

Download this link;

[http://www.freefilehoster.com/uploads/1172613986gphoto2+libphoto2-2.3.1_dapper.tar.gz](http://www.freefilehoster.com/uploads/1172613986gphoto2+libphoto2-2.3.1_dapper.tar.gz)

It's a .deb someone made of gphoto and libphoto 2.3 for dapper. Just extract and double-click and it should install. Install libphoto first.

---

### Post by gulmer on 2007-06-11
> **tbroderick said:**
> Download this link;

[http://www.freefilehoster.com/uploads/1172613986gphoto2+libphoto2-2.3.1_dapper.tar.gz](http://www.freefilehoster.com/uploads/1172613986gphoto2+libphoto2-2.3.1_dapper.tar.gz)

It's a .deb someone made of gphoto and libphoto 2.3 for dapper. Just extract and double-click and it should install. Install libphoto first.

This worked, all installed perfectly. Thank you for this link.;)

---

