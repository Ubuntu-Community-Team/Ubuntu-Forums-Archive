---
title: "Trouble With P2Ps"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by agonoruci on 2006-12-01
I am having a lot of trouble, I have tried LimeWire and that doesn't even open up, I don't even know where the aMule files are saved to, and GTK-GNUTELLA could not download anything, is there any other hope for me?

---

### Post by pay on 2006-12-01
Can you start Limewire in the terminal and post the error messages.

---

### Post by agonoruci on 2006-12-01
How do I run Limewire in terminal?

---

### Post by pay on 2006-12-01
open the terminal and run type "limewire" without the quotes. if that doesn't work open the terminal and type ```
sh /path/to/runLime
```Also make sure that you have java installed as limewire is dependent on java.

---

### Post by agonoruci on 2006-12-01
I dont know where my installed limewire is, cant find it

---

### Post by crgutierrez on 2006-12-01
To get access to your aMule/eMule "Incoming" folder, go to your home folder and select "Show Hidden Files" under the "View" menu OR press CTRL+H. It should be in your ".aMule" folder.

And try FrostWire instead of Limewire... works perfectly over here, even though i don't use it much.

---

### Post by pay on 2006-12-02
to find limewire try ```
find / -iname limewire
```

---

### Post by Frak on 2006-12-13
[http://ubuntuforums.org/showthread.php?t=315222&highlight=frostwire](http://ubuntuforums.org/showthread.php?t=315222&highlight=frostwire)

---

### Post by smileone on 2006-12-15
If you want to use LimeWire, you can downlaod LimeWire rpm package and convert to deb with alien
alien LimeWire.rpm

---

### Post by smileone on 2006-12-15
before run LimeWire check the java version that you have installed on your pc
```
sudo update-alternatives --config java
```

---

