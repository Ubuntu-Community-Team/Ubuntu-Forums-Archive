---
title: "FWBuilder Dependency File problem"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by jfourie on 2006-12-29
Hi There

I have just installed the Edgy version of Ubuntu and then tried to install FWBuilder. I have however run into a circular dependency problem. The one FWBuilder package has a dependency  on FWBuilder-Linux. and FWBuilder-Linux has dependency on FWBuilder. How do I get one of the 2 packages to install without checking the circular dependency?

Thanks
Johan

---

### Post by linuchsan on 2006-12-29
Are you using apt-get to install fwbuilder?

---

### Post by jfourie on 2006-12-30
Yes I tried to use apt but it couldn't find FWBuilder. I then found it  in the Edgy Packages on the Ubuntu site and downloaded the .deb files for it and tried to install it through the Gnome interface.

---

### Post by jfourie on 2006-12-30
OK I sorted out my problem. Had to add Universe to APT. Then it found it and installed it properly.

Thanks for the help.

---

