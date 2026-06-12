---
title: "Root Privilege"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by Cufishing on 2005-11-05
Ok, I have my M/Bs chipset driver downloaded. Here is Step 2:
Begin Installation
From within a shell with root privileges, type "sh NFORCE-Linux-x86-1.0-0306-pkg1.run" to initiate the installation.

I can relate to this. But, I don't know enough yet: :confused: 
A. If I should or should not be doing this.
B. How to have root privilege.
C. Understand the correlation between M$ sfae mode and Linux Root privilege.

Would somebody throw me a bone on this one?

---

### Post by Kyral on 2005-11-05
Well, the NVidia packages are incredibly safe. I use them every. As for how to gain root, well just prefix the command with "sudo"

The password is your user password.

MS Safe Mode(*snicker*) and Root power are completely different

Read this page and all will become clear

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Cufishing on 2005-11-05
Ok, cool beans. But now I've got more questions.
The installer needs "libc header" install Libc developmental package.
How do I get that package? Could not find it with Synaptic.

Also is this something I can handle? (Fully automatic, or easily answered questions)
Or do I need another guide.

---

### Post by Kvark on 2005-11-05
You need the package called build-essential.

---

