---
title: "CD-ROM Eject Problem"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-12-02
Hi I just installed Wine from the Ununtu repositories and it seemed to be working perfectly until the first program I tried to install...I was installing Battlefront 2 and the installation was running fine until it asked me to insert the 2nd install disc. It wouldnt let me eject the disc(I even tried the manual way of sticking the pin in the little hole! lol i apologize for not know the correct term?') It wouldnt let me eject the disc until I exited the installation. Anyone have any suggestions at all, anything at all would be appreciated thnx!:)

---

### Post by nite owl on 2006-12-02
Maybe it could be a problem with configuration??? Would anyone know if I have to configure my cd drive with Wine somehow???

---

### Post by CatKiller on 2006-12-02
I've not had to do this myself, but a **sudo umount /cdrom** in a second terminal window might work. (note there is only one n in umount). You might also need to **mount /cdrom** after you've swapped discs, before you go back to Wine.

---

### Post by nite owl on 2006-12-02
Hi thanks for your reply 'CatKiller' ill let you know how it goes..

---

