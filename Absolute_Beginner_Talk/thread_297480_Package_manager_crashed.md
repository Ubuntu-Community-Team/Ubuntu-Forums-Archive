---
title: "Package manager crashed"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by jgmattila on 2006-11-11
I'm pretty new to this OS and am running 6.6.

Synaptic package manager crashed when I was trying to download & install VM Ware Player.

I seem to have lost access to the "repositories", whatever and wherever they are.

           I got this message:

        E: Malformed line 2 in source list /etc/apt/sources.list (URI parse)
E: Unable to lock the list directory

Can anyone tell me whats going on and how to fix it?

---

### Post by Sef on 2006-11-11
Applications > Accessories > Terminal

gksudo gedit /etc/apt/sources.list

copy and paste the sources list here.

---

### Post by jgmattila on 2006-11-12
> **Sef said:**
> Applications > Accessories > Terminal

gksudo gedit /etc/apt/sources.list

copy and paste the sources list here.

Hi, 

I tried running that line in terminal and got this list of error messages:

   "E: Malformed line 2 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Malformed line 2 in source list /etc/apt/sources.list (URI parse)
E: Unable to lock the list directory"

---

### Post by taurus on 2006-11-12
How about pasting the output of this command instead?

```
cat /etc/apt/sources.list
```

---

### Post by jgmattila on 2006-11-12
I  am still getting the message:

E: Malformed line 2 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

after running the command line given.

Also I don't seem to be able to get root access when I have the terminal up.  My password doesn't seem to be authenticated.  I have been using a five character password, should it be six?

---

