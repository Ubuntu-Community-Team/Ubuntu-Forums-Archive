---
title: "Automatix question?"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by Il_Tuo_Nome on 2006-03-11
During the installation process for Ubuntu, does automatix install anything KDE related? I have this file that was created after I used automatix called 'kubuntu-packages-jridell-key.gpg' in my /home directory. So I took that to mean it installed some KDE packages. Is that correct? If so, which one's and can they safely be removed? Can **kubuntu-packages-jridell-key.gpg** be safely removed?

Thanks for the help :)

---

### Post by Wolki on 2006-03-11
This is one of the Kubuntu developer's gpg key, it's used to sign some of the kubuntu packages. I assume Automatix provides support for installing KDE3.5 on Breezy, and you need this in your keyring for a clean install. There should not be any need for the file itself anymore, you can probably remove it without worries.

I don't know whether Automatix installs KDE stuff by default, I doubt it though. See if you have kdelibs installed, it's needed by kde applications, if you don't have it your system should be kde-free.

---

### Post by Robgould on 2006-03-11
automatix does not install KDE stuff per se, but does work for kubuntu.  You can follow the link and see what it installs.

---

### Post by mstlyevil on 2006-03-11
I never had it install KDE apps on Ubuntu Breezy. You should be ok in that regard.

---

### Post by Il_Tuo_Nome on 2006-03-11
Thank you all for the replies, I wasn't so thanks :)

---

