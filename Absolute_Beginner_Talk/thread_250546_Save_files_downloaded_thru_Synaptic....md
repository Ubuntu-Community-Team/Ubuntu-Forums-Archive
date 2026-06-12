---
title: "Save files downloaded thru Synaptic..."
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by plsoft on 2006-09-04
Is there any way i can save the files (new or upgrades) downloaded thru synaptic or apt-get?

---

### Post by tkjacobsen on 2006-09-04
all the deb's are saved in /var/cache/apt/archives

---

### Post by plsoft on 2006-09-05
thnkx tkjacobsen. Let's say i have to reinstall ubuntu for some reasons, and i back-up the files saved in /var/cache/apt/archives in a cd. How do i use this cd to reinstall the softwares and their dependencies (preferably thru synaptic)?

---

### Post by monktbd on 2006-09-05
you can make your own repository:

[http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html)

---

### Post by omns on 2006-09-05
.

---

### Post by tkjacobsen on 2006-09-05
the easiest way would be to go to the cd and type in terminal:
```
sudo dpkg -i *.deb
```

(That wouldn't install dependencies not in the directory)

---

### Post by plsoft on 2006-09-06
pls tell in detail (easiest way possible pls) how i can use the cd as a repository. I couldn't follow the instructions on the link given by GrantG. Pls help out as i'm new to ubuntu.

---

### Post by az on 2006-09-06
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

or the simple version:

[https://help.ubuntu.com/community/AptMoveHowto/simple](https://help.ubuntu.com/community/AptMoveHowto/simple)

---

