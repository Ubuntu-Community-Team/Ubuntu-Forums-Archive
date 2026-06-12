---
title: "how do i fix this error?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-09-07
heres the error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
how do i fix it?
NOTE:i get it when i try to use the terminal to do most things so i probably cant use terminal to fix it...
plz help... i want to install awn lol

---

### Post by lisati on 2007-09-07
Please tell us what you get when you type the following at the terminal:
```

dpkg --configure -a

```

---

### Post by zvacet on 2007-09-07
```
sudo dpkg --configure -a
```

---

### Post by antisocialist on 2007-09-07
> **lisati said:**
> Please tell us what you get when you type the following at the terminal:
```

dpkg --configure -a

```

sure here it is:
dpkg: requested operation requires superuser privilege
and i own my computer and am using the account i made when i installed ubuntu
how do imake myself a superuser?

---

### Post by antisocialist on 2007-09-07
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

i entered yours and got this:
Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

then it prompted for a new command

---

### Post by antisocialist on 2007-09-07
i tried installing awn and got this message:
 apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
how do i fix it if i am root?

---

### Post by zvacet on 2007-09-07
```
sudo apt-get -f install
```

---

### Post by antisocialist on 2007-09-07
> **zvacet said:**
> ```
sudo apt-get -f install
```

i think i fixed it via synaptics but im going to try installing awn again to be sure

---

### Post by swoll1980 on 2007-09-07
it's telling you it's locked because synaptics is still running you have to shut it off before you can install things in the terminal

---

