---
title: "sudo apt-get install ndiswrapper-utils"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by CBondra on 2006-08-25
Everywhere I go it says to use "sudo apt-get install ndiswrapper-utils" to install ndiswrapper, but isn't this the internet method? If I have it downloaded, how do I install it? Is there a special command for that?

---

### Post by Bachstelze on 2006-08-25
The command to manually instal a DEB package is

```
sudo dpkg -i filename.deb
```

---

### Post by CBondra on 2006-08-25
Thank you so much!

---

### Post by CBondra on 2006-08-25
What other types of packages are there?

---

### Post by Bachstelze on 2006-08-25
You probably won't have to use them but there are RPM packages, used in RedHat/Fedora, Mandrake/Mandriva and SuSE especially. You can convert them to DEBs using alien if you _really_ have to but it's very unlikely, you won't find much software that isn't in the Ubuntu repos.

---

### Post by CBondra on 2006-08-25
Okay because ndiswrapper is just being such a pain right now and I didn't know if it was a .deb

---

### Post by Bachstelze on 2006-08-25
Have you followed the intructions from [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) ?

---

