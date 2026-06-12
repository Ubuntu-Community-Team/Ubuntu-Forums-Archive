---
title: "Realtek AC97 chips set, is silent, and shouldnt be."
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-09
still not producing so much as a fart of sound, i dont know what todo, i download the drivers, and they unpack,, then what?

---

### Post by 5-HT on 2007-08-10
Did the drivers install properly, have you loaded the module, and have you also checked the ouputs in alsamixer?

---

### Post by jake16424 on 2007-08-10
> **5-HT said:**
> Did the drivers install properly, have you loaded the module, and have you also checked the ouputs in alsamixer?

no i cant get them to install. thats the problem.

---

### Post by 5-HT on 2007-08-10
> **jake16424 said:**
> no i cant get them to install. thats the problem.
Was there an error message? If it's in regards to how to perform the installation, there should be a README/INSTALL/etc.. file in the package that details everything.
I don't have the card myself so I can't be of specific help.

---

### Post by jake16424 on 2007-08-10
> **5-HT said:**
> Was there an error message? If it's in regards to how to perform the installation, there should be a README/INSTALL/etc.. file in the package that details everything.
I don't have the card myself so I can't be of specific help.

jacob@jacob-desktop:~$  ./install
bash: ./install: No such file or directory
jacob@jacob-desktop:~$





after i do what the .readme file says todo..

---

### Post by 5-HT on 2007-08-10
From what you posted, you're trying to run an install script from your home directory but there's no such file there. You need to either be in the top-level directory of the extracted package, or reference it by its absolute path.

i.e., if the archive you expanded became ~/foo, you need to either:
1) run the script from within ~/foo, not ~/
or
2) runt the script using the full path: ./home/jacob/foo/install

The READ me should document all of this.

---

### Post by jake16424 on 2007-08-10
ive tried all paths that are relivent to the file directory,, nothing works,, just keeps saying that same message,,,

---

### Post by splintercellguy on 2007-08-10
Okay, so where did you extract the driver files?

---

