---
title: "Booting"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by Cameroon Loser on 2005-08-08
Hello, I'm a total Ubuntu newbie and when I tried to install the first boot loader thingy it gave me a fatal error. So I went on without a bootloader. What should I do to be able to dualboot?

---

### Post by tonysathre on 2005-08-08
first install windows then linux. you have to have a bootloader (grub) to boot into linux. when you install ubuntu, install the bootloader on the MBR (master boot record) so that grub will add any other OS you have installed on your system. then when you boot up you will be greeted with a menu to pick which OS you want to load.

---

### Post by Cameroon Loser on 2005-08-08
Tried that but then the GRUB didn't install. Now I have them both installed and Linux booted, but no Boot loader. GRUB failed to install and it said it was a 'fatal error'.

Are there any alternative multibooters?

---

### Post by Lord Illidan on 2005-08-08
You have 2 hard drives or just 1 partition? Is it RAID? IDE?

---

### Post by Cameroon Loser on 2005-08-08
I installed it on a second partition. I don't know what that RAID / IDE stuff means.

---

### Post by Cameroon Loser on 2005-08-08
Come on, help me! I still can't dualboot!

---

### Post by RastaMahata on 2005-08-08
[QUOTE=Cameroon Loser]Come on, help me! I still can't dualboot![/QUOTE]
 type this in a console and copy-paste the output here```
sudo fdisk -l
```

---

### Post by Cameroon Loser on 2005-08-08
```
Schijf /dev/hda: 60.0 GB, 60022480896 bytes
255 koppen, 63 sectoren/spoor, 7297 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1        5929    47624661    7  HPFS/NTFS
/dev/hda2            5930        7204    10241437+   7  HPFS/NTFS
/dev/hda3            7205        7297      747022+   5  Uitgebreid
/dev/hda5            7205        7297      746991   82  Linux swap / Solaris

```

---

### Post by RastaMahata on 2005-08-08
hope this helps:
[http://www.linuxquestions.org/questions/archive/63/2005/07/3/332444](http://www.linuxquestions.org/questions/archive/63/2005/07/3/332444)

---

### Post by Cameroon Loser on 2005-08-08
I found out already, and altough I'm not bothering to read it, thanks anyways.

---

