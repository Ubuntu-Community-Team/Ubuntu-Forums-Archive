---
title: "Need Help transfering files to new computer"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by MrBeenz on 2007-08-30
See I bought a new computer and put kubuntu on it but i need help transfering some files from my old computer with kubuntu to new computer. Any ideas.

---

### Post by Hobo Joe on 2007-08-30
Are they networked?

---

### Post by macogw on 2007-08-30
If they're both going through the same router, you can install an openssh-server on one and transfer files through an ssh tunnel.  otherwise, you can get a usb transfer cable (that is *not* the same as usb a/a) and hook them together that way

---

### Post by MrBeenz on 2007-08-30
yes they are both on the same router. how do i install an openssh-server

---

### Post by splintercellguy on 2007-08-30
sudo apt-get install openssh-server? You could setup Samba or FTP also.

---

### Post by macogw on 2007-08-30
Well I think the ssh (or ftp) server would have to be on the Windows box.

---

### Post by splintercellguy on 2007-08-30
Both ways really, if you want the Windows box to upload.

---

### Post by MrBeenz on 2007-08-30
ok i installed it now how do i use it

---

### Post by MrBeenz on 2007-08-30
i never said i had a windows box

---

### Post by MrBeenz on 2007-08-30
thanks for the help everyone i figured it out.

---

