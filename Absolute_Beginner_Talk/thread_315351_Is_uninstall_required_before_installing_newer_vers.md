---
title: "Is uninstall required before installing newer version of software?"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by nyxynyx on 2006-12-09
Hello! Is uninstall required before installing newer version of software? Can i just install the tarball without uninstalling a previously installed version? Thanks!

---

### Post by ciscosurfer on 2006-12-09
As far as .deb files go, you don't need to uninstall before you install a new version (when using apt, old versions, and current versions for that matter, are located under /var/cache/apt/archives).

If you are compiling your apps, I'm not as sure on the correct procedure.  I'm assuming you can just install a new version without uninstalling the old version without hassle.  But I could be wrong there.

---

### Post by Circus-Killer on 2006-12-09
ummm.....okay, dont take this as being the word from above. i know nothing. but afaik, for most packages you can just install the new version of the software over the old. i say most, cos there will be some that require an uninstall.

if you check in the files extracted from the tarball, there should be a README or an INSTALL file, read both. one of the them should mention something about upgrading.

(edit: this is all assuming that you not talking about a .deb package)

---

