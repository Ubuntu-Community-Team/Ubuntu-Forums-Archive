---
title: "BURG instead of GRUB?"
date: 2011-12-06
forum: Any Other OS
---

### Post by Ricx94 on 2011-12-06
I've currently got Windows 7 on my laptop, and I'm planning on setting up a dual boot with Linux Mint 12.
wondering if there's any way that during the installation, BURG could be used instead of GRUB for boot selection on startup.

---

### Post by Jahid65 on 2011-12-06
no you can't. you have to install BURG manually.

---

### Post by bluexrider on 2011-12-06
once the installation is don it can be easily switched

---

### Post by Ricx94 on 2011-12-06
could someone give me some assistance in installing BURG on my linux mint 12 install? every site has something different, and i haven't found anything that is specific to linux mint 12...most are for 11

---

### Post by bluexrider on 2011-12-06
> **Ricx94 said:**
> could someone give me some assistance in installing BURG on my linux mint 12 install? every site has something different, and i haven't found anything that is specific to linux mint 12...most are for 11

well,  Lisa is just a baby however she uses Gnome 3. 

should be able to do this:

sudo add-apt-repository ppa:ingalex/super-boot-manager
sudo apt-get update
sudo apt-get install burg

---

### Post by Ricx94 on 2011-12-06
thanks! I've got it running good.

---

### Post by bluexrider on 2011-12-06
U R welcome, glad to help

plz mark this (SOLVED)

---

### Post by Ricx94 on 2011-12-06
> **bluexrider said:**
> U R welcome, glad to help

plz mark this (SOLVED)

sorry, will do :)

---

### Post by GTull on 2012-01-21
I tried this and while it seemed to install OK, it didn't work and grub just loaded as normal any help?

---

### Post by jodiaq on 2012-02-13
i have installed burg using some commands.
Now i want to switch back to grub.
How to do that.
One more thing is grub can boot iso images also. If they are bootable. Can i boot a redhat iso image.
Help me in this.
One more help. How to know which boot loader i am using.

---

