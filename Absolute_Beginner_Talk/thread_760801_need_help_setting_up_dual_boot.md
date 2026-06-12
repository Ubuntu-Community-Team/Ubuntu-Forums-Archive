---
title: "need help setting up dual boot"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Devildog007 on 2008-04-20
I've just installed Ubuntu 7.1 and parted my HDD to look like this.

4gb-fat32 (to be used by boot loader)
90gb -ext3 Ubuntu
1gb-swap
5gb-ext want to install backtrack 2

I want to install backtrack 2 to the 5gb partition but I know if I do then LILO will overwrite my grub and I won't be able to boot into Ubuntu. I searched through other forums and tried different things but nothing seems to work. I have not changed anything in ubuntu. can someone walk me through on installing LILO to the fat32 partition and setting it up to boot to ubuntu. Thanks

---

### Post by A4006 on 2008-04-20
Once you have installed Backtrack 2, just reinstall GRUB:

1.Boot your Ubuntu LiveCD.
2. Open a terminal window.
3. Type "grub"
4. Type "root (hd0,0)", or whatever your harddisk + boot partition numbers are.
5. Type "setup (hd0)", or whatever your harddisk number is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by sailor2001 on 2008-04-20
a handy suggestion is to download and burn a "super grub" cd.  it's free

---

### Post by Devildog007 on 2008-04-20
I've tried the super grub cd but it didn't find my backtrack install only ubuntu. but a very nice little app gonna keep it around.

---

### Post by Devildog007 on 2008-04-20
Everything so far has not worked it has just let boot into Ubuntu and not backtrack.

---

