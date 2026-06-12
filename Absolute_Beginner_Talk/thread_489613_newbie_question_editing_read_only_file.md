---
title: "newbie question: editing read only file"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by USSEnterprise on 2007-07-01
I am trying to fix the sound on my Toshiba laptop, and I need to edit the file "alsa-base" to do so. How do I make said file capable of being edited and saved?

Thanks
Joe

---

### Post by Taliskerd on 2007-07-01
'chmod +w <filename>' should do it.

See 'man chmod' in a terminal for details about this.

---

### Post by janbockaert on 2007-07-01
you need to have admin rights to do so. Open a console, and type: sudo gedit /the pad to the alsa-base file/

You will get asked your password, after you entered, gedit will open the file and you will be able to edit and safe it.

Maybe it is not a bad idea to make a back up before you edit the file.

---

