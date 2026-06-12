---
title: "new repository = update?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by marn on 2007-09-24
I've added a new repository to the sources list for a programm (scribus) which is already installed. Will the package automatically be updated to the newer version according to the new repository, or does the the old version need to be deinstalled. In Synaptic I see an option "Reinstall" when I choose a package. Is that the same thing? Rather a lot in one go. I'd appreciate any advice.

---

### Post by mysticmatrix on 2007-09-24
> **marn said:**
> I've added a new repository to the sources list for a programm (scribus) which is already installed. Will the package automatically be updated to the newer version according to the new repository, or does the the old version need to be deinstalled. In Synaptic I see an option "Reinstall" when I choose a package. Is that the same thing? Rather a lot in one go. I'd appreciate any advice.

1) Yes, it will be automatically updated like any other application, as long as you have appropriate line in source list.
2) Reinstall- just a uninstall and install again of same version. That's not related to upgrade, intead if you just want to reinstall something.

---

### Post by marn on 2007-09-24
Thanks for the answer. Is there a way to manually start the update, or how do I know if the program has been updated? (I don't usually note the current version number! :))

---

### Post by Vixis on 2007-09-24
> **marn said:**
> Thanks for the answer. Is there a way to manually start the update, or how do I know if the program has been updated? (I don't usually note the current version number! :))

Button Update in Synaptic or in terminal:
sudo apt-get update && sudo apt-get upgrade

To see current version number:
scribus --version

---

### Post by mysticmatrix on 2007-09-24
> **marn said:**
> Thanks for the answer. Is there a way to manually start the update, or how do I know if the program has been updated? (I don't usually note the current version number! :))

System --> Administration --> Update Manager and then click Check. Just like any other application :guitar:

---

### Post by marn on 2007-09-24
Thank you for your help - I'm slowly coming to terms with Ubuntu. Btw, why does Ubuntu have two different ways of installing - Add/Remove and Synaptic (or are they the same?)

---

### Post by Maestro23 on 2007-09-24
> **marn said:**
> Thank you for your help - I'm slowly coming to terms with Ubuntu. Btw, why does Ubuntu have two different ways of installing - Add/Remove and Synaptic (or are they the same?)

Check this link: [https://help.ubuntu.com/community/InstallingSoftware?highlight=%28Installing%29%7C%28software%29](https://help.ubuntu.com/community/InstallingSoftware?highlight=%28Installing%29%7C%28software%29)

---

### Post by marn on 2007-09-24
@ Maestro23: Brilliant, thanks. Feel informed!

---

