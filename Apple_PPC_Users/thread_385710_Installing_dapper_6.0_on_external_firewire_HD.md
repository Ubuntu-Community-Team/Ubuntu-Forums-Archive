---
title: "Installing dapper 6.0 on external firewire HD"
date: 2007-03-16
forum: Apple PPC Users
---

### Post by penguinhack62 on 2007-03-16
Hello,
I am trying to install Ubuntu Dapper 6.0 onto a external firewire HD. When installation is almost complete it states it can not install to yaboot. What do I need to do when I am partitioning HD. I used the assisted install.  Am I better off doing custom install. I am new to MAC computers. I have an iBook G4. Any help will be greatly appreciated. I am fluent in linux  with many years of use. I have never dual booted with MacOS X.

---

### Post by grazie on 2007-03-16
Any particularly reason for using Dapper? Dapper doesn't support firewire booting out of the box, but I believe if you can rebuild the kernel to support this.

However, there are also outstanding ppc installer bugs ([#64219]("https://launchpad.net/ubuntu/+source/ubiquity/+bug/64219"), [#67669]("https://launchpad.net/ubuntu/+source/ubiquity/+bug/67669") & [#76614]("https://launchpad.net/ubuntu/+source/ubiquity/+bug/76614")) which means the yaboot installation will fail on firewire drives. Both topics have discussed quite recently in the forum. To set up yaboot manually check [this]("http://www.ubuntuforums.org/showthread.php?t=380424") and other threads. You'll probably need to make a few additional tweaks for firewire, but you'll need to dig out those for yourself, unless somebody else posts the details.

---

