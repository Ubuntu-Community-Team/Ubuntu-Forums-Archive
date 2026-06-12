---
title: "AO+Ubuntu+Wine=Sad"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by bakentake on 2008-02-05
Welp I've got Wine, Installed, and downloaded Anarchy Online, but every time i try and get wine to run the .exe I get:

zach@zach-desktop:/home$ wine AnarchyOnline_17.6.1_EP1_EP2_EP3.exe
wine: could not load L"c:\\windows\\system32\\AnarchyOnline_17.6.1_EP1_EP2_EP3.exe": Module not found

I've been using :

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

as it was the only thing that wasn't for ubuntu 6.XX or something, if anyone could help it'd be great.

---

### Post by pedro_orange on 2008-02-05
Unless you've installed AO in c:\\windows\\system32 wine is looking for it in the wrong place.

Make a launcher for the item, and then u can edit the command etc. You should find most games under the .wine/c_drive/program files/ directory.

---

### Post by bakentake on 2008-02-05
I guess I should've said that my computer is only ubuntu, so I redownloaded ao, and its in my home, but when I type the command it spits that out at me. I have done the "winecfg".

---

