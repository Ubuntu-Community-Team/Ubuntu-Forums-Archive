---
title: "disk cloning tool needed"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by stoppage on 2008-04-02
Has anybody used an automatic „image“ tool to clone Ubuntu from one disk to another (for dual boot)? I'm not interested in the terminal method, I hate the terminal. I have „Acronis 8.0“ but I think its Win-only. Any help much appreciated.

---

### Post by blazercist on 2008-04-02
i havent used it but i heard about ghost4linux its supposed to be good

---

### Post by bumanie on 2008-04-02
There is ghost4linux (as stated) there is also clonezilla,partimage and even gparted has a copy function, where it can copy a whole disc or a partition. Gparted cannot compress, but it doesn't sound as though you want a compressed image/copy anyway. I have used the copy function on gparted live cd and it went without a hitch.

---

### Post by taavikko on 2008-04-02
Why use complicated GUI, when you can just use **dd**
but if you dislike cli what can you do :(

---

### Post by stoppage on 2008-04-04
In the case of complicated GUI versus dd, Im just tired of this antiquated little "dos-box" method in Linux

---

### Post by wolfen69 on 2008-04-04
> **stoppage said:**
> Has anybody used an automatic „image“ tool to clone Ubuntu from one disk to another (for dual boot)? I'm not interested in the terminal method, I hate the terminal. I have „Acronis 8.0“ but I think its Win-only. Any help much appreciated.

if you open acronis in windows, search the menus for making a boot disk that will clone any OS.

---

### Post by stoppage on 2008-04-05
O.K., Ive just „imaged“ Feisty, following instructions on [http://ubuntuforums.org/showthread.php?t=599599]("http://ubuntuforums.org/showthread.php?t=599599")   
using Acronis instead of dd. Cloned Feisty from hda (80GB) to larger sda ( 320GB)....precisely from hda5 to sda7 for dual boot with Windoze where it sat sulking (recognised by live cd as disk) refusing to mount. Windoze was still booting up to the grub part of instructions on link. Dual boot menu did come up.....booting Linux rendered....Error 17..cannot mount selected partition.
Booting XP....selected disk does not exist. I resurrected XP with the help of Super Grub Disk but no sign of cloned Feisty although I can still boot it from its other installation. Im missing something here and I dont know what it is.

---

