---
title: "How to boot Ubuntu without X Server?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Harry_Callahan on 2006-09-02
Hello,

I'd like to know if it is possibile to boot Ubuntu without Gnome\KDE environment(without graphical server). I want control an old P3 500Mhz PC from remote, hoping to save CPU and Memory use....

Thanks

---

### Post by Titus A Duxass on 2006-09-02
Download the alternative CD and do a server install.
Then choose the packages you want.

---

### Post by SoftTaco on 2006-09-02
You can keep gnome\kde from coming up by just hiding the lancher files. I had to do it once to get a vid card to work right.

just:
sudo mv /etc/init.d/gdm /etc/init.d/gdm.bak

it will fail to find gdm and default to the console
and that way if you ever do decide to use gnome it will still be there

---

