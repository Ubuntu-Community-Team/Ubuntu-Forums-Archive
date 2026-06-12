---
title: "Neverwinter nights, ./fixinstall"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by SphereX253 on 2007-10-07
I followed the instructions on the bioware site for installing from an existing windows installation.  I downloaded the binaries. I copied the files and folders it said to. I extracted the binaries.. however when I go to the terminal to continue with next step (./fixinstall) I get this error:

bash: ./fixinstall: No such file or directory


It worked just fine the first time I did it.  Then I reformatted and now it won't work. Am I missing something?

---

### Post by wormser on 2007-10-07
> **SphereX253 said:**
> bash: ./fixinstall: No such file or directory

The error is telling you that the file is not in that directory.  The ./ means current directory and is used to run programs when you are in that directory.  Find where fixinstall is and **cd** into that directory then the command will work.  Use the **ls** command to verify the file is in the folder you are in.

---

