---
title: "setup for dial-up"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by aggies on 2006-06-05
I am new with ubuntu. Can someone please tell me step by step how to setup for dial-up connection?

Thanks:confused:

---

### Post by ProjectGod on 2006-06-06
[SIZE="7"]**surprised **[/SIZE]no one answered this one... :D

well i havent used dial up in quite some time now... i think you'll have to firstly check youre hardware is being detected properly by linux...

i'm on a windows machine right now so from the top of my head its something like...

**lshw --help**

use the command to list the available "classes" then depending on the modem whether internal pci or external you could

**lshw -C PCI**

the code above is for internal pci modem...

anyway it should list the modem's name / driver / model / vendor etc etc... a good first step to check detection...

after this i guess you can use the:

**pppconf **or **pppconfig **command... I cant be sure!!!! :twisted: 

its a terminal based wizard to guide you through the process...

then afterwards you can use the command 

**pppon**

always check the help files such as pppconfig --help or pppconf --help and pppon --help

or for more thorough documentation type 

**man pppconfig **or **man pppconf**

---

