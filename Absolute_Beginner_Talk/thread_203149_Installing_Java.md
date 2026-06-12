---
title: "Installing Java"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by msv240586 on 2006-06-24
Hey guys,  I apparently need to install java into the /usr/java/jre1.5.0 directory. I installed it but it installed it to the Home folder. As you guys know that the /usr directory is read only. So now i have my java sitting in the home folder. How can i get it to where its supposed to be, in /usr/java/jre1.5.0?

Thanks

---

### Post by raptros-v76 on 2006-06-24
sudo cp -r <source> <target directory>

---

### Post by Winblowz on 2006-06-24
You have to open your file manager as root, because you don't have the needed permissions. Open the terminal and type "sudo nautilus" if you're using Gnome, or "sudo konqueror" if you're using KDE. 

On a side note, why did you install Sun Java manually? You could have just done "sudo apt-get install sun-java5-jre."

---

