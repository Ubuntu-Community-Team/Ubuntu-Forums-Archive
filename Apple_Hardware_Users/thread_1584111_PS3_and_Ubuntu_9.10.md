---
title: "PS3 and Ubuntu 9.10"
date: 2010-09-28
forum: Apple Hardware Users
---

### Post by trj021782 on 2010-09-28
In case you couldn't tell I have a PS3 running Ubuntu 9.10.

I have many issues I would like to resolve however all of the forums and threads I have found refer to how to resolve these issues in 9.04. Here are the problems I am currently working on:

1. getting Ubuntu to resize my resolution to 1920x1080
2. getting my PS3 controller to connect to Ubuntu via Bluetooth ( I found a solution to this one in the form of QtSixA but after installing the program i could not find it and it does not execute from a terminal)
3. Getting a working version of PCSX2 (I found it in the compatible PPC64 architecture build but i have yet to successfully install anything from tarballs)
4 getting qemu to work (tarballs again)

these are the first issues I want work through, if anyone has any help to offer I would appreciate it.

---

### Post by SeijiSensei on 2010-09-28
> **trj021782 said:**
> In case you couldn't tell I have a PS3 running Ubuntu 9.10.

I don't how much help you'll be able to get here, but you might want to ask your question at [AVSForum]("http://www.avsforum.com/avs-vb/forumdisplay.php?f=142") as well.

---

### Post by trj021782 on 2010-09-28
> **SeijiSensei said:**
> I don't how much help you'll be able to get here, but you might want to ask your question at [AVSForum]("http://www.avsforum.com/avs-vb/forumdisplay.php?f=142") as well.

Thank you, I shall do so right away

---

### Post by linuxopjemac on 2010-09-29
Maybe this helps:
[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

---

### Post by trj021782 on 2010-09-29
****NEW UPDATE****

I have successfully made the PS3 Ubuntu install output at 1080p (thereby using my entire TV screen) and i have also installed QtSixA and used my PS3 controller in Ubuntu. . . so those two problem have been resolved that only leaves me with figuring out how to compile tarballs files. I cannot figure out dependencies which is okay because i have been less than successful with the make command anyway. So if anyone has any advice or links i would appreciate it

---

### Post by linuxopjemac on 2010-09-29
```
sudo apt-get install build-essential
```

---

