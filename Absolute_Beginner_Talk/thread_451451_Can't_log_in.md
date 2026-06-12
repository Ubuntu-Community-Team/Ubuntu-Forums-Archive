---
title: "Can't log in"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by fr6zeros on 2007-05-22
I'm typing this from Windows.  I have both OS and have been adding stuff to my Ubuntu and making changes with packages (yiaks). I  can't log in now and I get this message:
GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in.

It doesn't sound too good and I don't have a system administrator to help.

---

### Post by Sparkster185 on 2007-05-22
Can you boot to recovery mode and access just the command line?  If you can, if you type

"df -h /home" how much disk space do you have left?

---

### Post by taurus on 2007-05-22
Boot into recovery mode from GRUB menu and at the prompt, type

```
aptitude clean
```
That would free up some space for you to log in. 

```
df -h
```
Then, reboot your machine.

```
shutdown -r now
```

---

### Post by fr6zeros on 2007-05-22
Problem solved, thank you very much for your quick response.  I'm thinking on using only Ubuntu in the future, Everyone is very helpful here and I'll probably ask for more help.

---

### Post by Sparkster185 on 2007-05-22
If your /home is really that full, you might want to consider re-partitioning it and making it larger so you can avoid this in the future.

What I did is bought a second hard drive.  I mounted it, copied my /home directory over to it and then edited the /etc/fstab file so that my 2nd drive was mounted as /home.  Not too painful and now I have 250GB for my user data.

---

### Post by taurus on 2007-05-22
> **Sparkster185 said:**
> If your /home is really that full, you might want to consider re-partitioning it and making it larger so you can avoid this in the future.

What I did is bought a second hard drive.  I mounted it, copied my /home directory over to it and then edited the /etc/fstab file so that my 2nd drive was mounted as /home.  Not too painful and now I have 250GB for my user data.

Even if you have plenty of disk space on a separate /home and your / is full, you can't log in without seeing that error message because it cannot write to /tmp.

---

