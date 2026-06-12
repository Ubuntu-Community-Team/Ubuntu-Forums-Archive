---
title: "Huge firefox bug"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-03-14
Ok, I opened a Linux Terminal (Konsole) and typed "cd firefox" then it changed directory, typed "sudo ./firefox" and it asked for PW, gave it and it says "./firefox-bin: error when loading shared libraries: libgtk-xll-2.0.so.0 cannot open shared object file: No such file or directory" Anyone know what I did wrong?

---

### Post by aysiu on 2007-03-14
Why are you doing *sudo ./firefox*?

---

### Post by Peter1234123 on 2007-03-14
sudo=root access, firefox=Shell directory

---

### Post by aysiu on 2007-03-14
> **Peter1234123 said:**
> sudo=root access, firefox=Shell directory
You're trying to update Firefox? Is that why you need root access?

Try *gksudo*--that's for graphical applications:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

For example, when I updated my Firefox, I did ```
gksudo firefox
``` I didn't have to do the ./ because Firefox is integrated with my Ubuntu system via [this script](http://www.psychocats.net/ubuntu/firefox).

---

### Post by Peter1234123 on 2007-03-14
No, I am using KUbuntu, same files etc. but with the KDE interface, it only came with Konquerror, not firefox.

---

### Post by aysiu on 2007-03-14
> **Peter1234123 said:**
> No, I am using KUbuntu, same files etc. but with the KDE interface, it only came with Konquerror, not firefox.
You can install and use Firefox on Kubuntu.

If you want the stock Ubuntu Firefox, you can install it with this command: ```
sudo apt-get update && sudo apt-get install firefox
``` If you want Mozilla's Firefox, use [the script I linked to before](http://www.psychocats.net/ubuntu/firefox).

---

### Post by Peter1234123 on 2007-03-14
I also tried gksudo and it says bash: gksudo: command not found.

---

### Post by Peter1234123 on 2007-03-14
Thanks, so much, I was sick of no Java/Flash etc.

---

### Post by aysiu on 2007-03-14
> **Peter1234123 said:**
> I also tried gksudo and it says bash: gksudo: command not found. Sorry. Yeah. I assumed you were using Ubuntu and not Kubuntu. You can install *gksudo*: ```
sudo apt-get update && sudo apt-get install gksu
``` There's also a special version for Kubuntu called *kdesu*. But if you're using the Ubuntu Firefox, you won't be updating Firefox individually using *gksudo*.

> **Peter1234123 said:**
> Thanks, so much, I was sick of no Java/Flash etc. Theoretically, can't you have Java and Flash in Konqueror?

---

