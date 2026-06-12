---
title: "Does apt-get install the latest versions?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Nexus... on 2007-08-11
Hi I was just wondering does apt-get install the latest of the selected software?

For those who might not understand or misinterpret, if I typed in:
sudo apt-get alien 

Would that download the latest version of alien?

(Alien is used to convert .rpm packages into .deb self installing packages - I would recommend) 

:)

---

### Post by Nekiruhs on 2007-08-11
Yes. It installs the version it finds in the repositories. IF you have added a repo it checks to see which is newer and installs the newer one.

---

### Post by forestpixie on 2007-08-11
It would download and install the latest version from the repos - NOT necessarily the newest version that's available elsewhere is my understanding.

---

### Post by testube_babies on 2007-08-11
After you do an apt-get update, the apt-get install will install the latest versions available in the Ubuntu repos.  This is not always the latest version of the program available, but it is the latest version that is officially supported by Ubuntu.

---

### Post by Nexus... on 2007-08-11
Thanks and these "repos" you wer on about if I am not mis-readin testube _babies reply they are updated with "apt-get update"?

---

### Post by schorsch on 2007-08-11
No, the repos are updated without your intervention but by the maintainers of the software. The command "apt-get update" updates the files stored locally on your computer which contain the information about the actual versions.

---

